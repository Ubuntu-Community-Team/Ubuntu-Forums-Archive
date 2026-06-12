---
title: "Console piping output question"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by lems on 2010-04-20
So I have a program that accepts input from the command line and can be run like so...

myprogram 
> arg1, arg2

or like so:

"arg1, arg2" | myprogram

unfortunately, the above statement pipes the two arguments into myprogram, but terminates right after. How do I make myprogram stay in interactive mode? so in other words I wanna be able to have it do this:

"arg1, arg2" | myprogram
> display some output
> enter more args here


I don't want it to terminate.

---

### Post by undecim on 2010-04-20
check the program manual and look for an interactive mode option.

---

### Post by Iowan on 2010-04-20
Is that a program you wrote?

---

### Post by lems on 2010-04-20
> **Iowan said:**
> Is that a program you wrote?

no, it's just some other program.

---

