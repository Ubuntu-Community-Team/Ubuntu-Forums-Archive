---
title: "gcc cannot find libraries?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by starshape on 2010-04-11
Hi.
I have files, written in C: 
something.h and something.c containing function f()
i compile them with command:

   gcc -c something.c -o something.o

and pack them into a library:

   ar r libsth.a something.o

I also have a file main.c, in which i use this function f(), and in this file I have a line: #include "something.h"

Then, when i try to compile main.c, with command:

   gcc main.c -o main -L. -lsth

I get an error:
   something.h: No such file or directory.

I can't understand why? I also tried to provide full path to the library for -L, but that didn't work either (although, I could've done that wrong). I also tried including -I. in command but that also didn't work.

Oh, and I think the files are correct - when I don't include this library, instead just leave this files something.h and something.c in the directory, program compiles just fine.

EDIT: I also forgot to mention that all those files are in the same directory, somewhere in my home directory

---

### Post by lisati on 2010-04-11
Thread closed: wrong subforum, and duplicate of [http://ubuntuforums.org/showthread.php?t=1452251](http://ubuntuforums.org/showthread.php?t=1452251)

---

