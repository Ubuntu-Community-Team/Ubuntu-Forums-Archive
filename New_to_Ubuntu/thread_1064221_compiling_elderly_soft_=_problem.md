---
title: "compiling elderly soft = problem"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by zebrafish on 2009-02-08
Hello.
I'm very new to Linux and I've been trying to compile a specific program, TIGR Assembler: [http://powerdev.osuosl.org/node/37]("http://powerdev.osuosl.org/node/37")

Readme said only:
"A. This software must be compiled before use. To compile this software, do 
the following:
1) Change into the src directory.
cd src
2) Build the TIGR Assembler
make"

First it wanted xlc command, now says:
helena@ubuntu:~/Plocha/TIGR_Assembler_v2/src$ make
xlc -w -O3 -qarch=auto -qchars=signed -c ./asmg.c -o ../obj/asmg.o

xlc[m] Copyright 2001-2004 by S. Fuchs [[http://linecontrol.srf.ch/]](http://linecontrol.srf.ch/])
Licensed under the GPL, see file LICENSE of the distribution package.
version: 1.0.6
xlc: invalid option -- 'w'
xlc: invalid option -- 'O'
xlc: invalid option -- '3'
xlc: invalid option -- 'q'
xlc: invalid option -- 'a'
xlc: invalid option -- 'r'
xlc: invalid option -- 'q'
xlc: invalid option -- 'o'
xlc: invalid option -- 'w'
xlc: invalid option -- 'O'
xlc: invalid option -- '3'
xlc: invalid option -- 'q'
xlc: invalid option -- 'a'
xlc: invalid option -- 'r'
xlc: invalid option -- 'q'
xlc: invalid option -- 'o'


and the app from LineControl opens. What to do with this?



The Assembler is at least five years old; should I get a Linux distribution of the same age? If so, any recommendations?

---

### Post by howlingmadhowie on 2009-02-08
hi :)

if you go into the src directory and have a look at the Makefile, you'll see:

```

CC      = xlc 
CFLAGS  = -w -O3 -qarch=auto -qchars=signed

```

so xlc is the name of a c compiler. the c compiler on ubuntu is called gcc, so you'll have to change xlc to gcc in this file. gcc doesn't understand the options -qarch and -qchars, so you can delete them too.

i changed it to:

```

CC = gcc
CFLAGS = -Wall -O3

```

and it compiled okay with lots of warnings.

-------

update.

the make file creates an executable in ../bin. i've just tried to run it and it displays a list of command line options. seeing as i have no idea what the program does, i think i'd best stop here. it seems to work anyway :)

---

### Post by zebrafish on 2009-02-08
Thanks a bunch, it works now:D

---

