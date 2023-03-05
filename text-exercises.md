# Milestone 2 Short-answer questions

## Exercise 14

# Project Exercises
## patch-instructions
The `patch-instructions`pass converts a `para-asm-lang-v2` program to a `paren-x64-fvars-v2` program by replacing instructions in the former by equivalent ones in the latter.  To show the equivalence we show a program before and after the `patch-instructions` pass.

Before: `(patch-instructions
              (begin
		(set! fv0 10)
		(set! fv1 42)
		(set! fv1 (+ fv1 fv0))
		(set! fv0 fv1)
		(halt fv0)))`

After:  `(begin
		(set! fv0 10)
		(set! fv1 42)
		(set! fv1 (+ fv1 fv0))
		(set! r10 fv1)
		(set! fv0 r10)
		(set! rax fv0))`



Before we have a halt instruction that is converted to a set! to rax after the pass.

## Abstracting Physical Locations
The difference between `Asm-lang-v2` and `Nested-asm-lang-v2` is that a statement in a `begin` expression can be yet another `begin` expression in the latter. This allows for nesting of begins that gives the programmer the option to perform sub-computations before continuing with the rest of the program. This way the programmer does not have to think about writing one big sequential program.

