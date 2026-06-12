---
title: "make: xlc: command not found"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by zebrafish on 2009-02-01
Hello.
I'm very new to Linux and suddently need to install a program, TIGR Assembler.

The Readme file says:
"TIGR ASSEMBLER needs the following to run:

1) a UN*X or Linux based machine with 32 or more MB of RAM; this requirement
   varies with the data set size being assembled
2) a C compiler capable of compiling both K+R C and ANSI C
3) /bin/csh (C shell); for the launcher"

I have GCC and CSH installed...

and then it says:
"A.  This software must be compiled before use.  To compile this software, do 
    the following:

   1) Change into the src directory.

      cd src

   2) Build the TIGR Assembler

      make"

After "make", I'm getting this error:
helena@ubuntu:~/Plocha/TIGR_Assembler_v2/src$ make
xlc  -w -O3 -qarch=auto -qchars=signed -c ./asmg.c -o ../obj/asmg.o
make: xlc: Command not found
make: *** [../obj/asmg.o] Error 127
:(

Ideas?

---

### Post by albinootje on 2009-02-01
> **zebrafish said:**
> 
make: xlc: Command not found
make: *** [../obj/asmg.o] Error 127

Please do the following :
```

apt-cache search xlc
sudo apt-get install xlc

```
and try again.

---

### Post by homemadejam on 2009-02-01
```
sudo apt-get install xlc
```

That should cure your problem :)

Jam

---

### Post by zebrafish on 2009-02-01
Thanks, it worked, or at least something different happened.

Now I'm getting this:
helena@ubuntu:~/Plocha/TIGR_Assembler_v2/src$ make
xlc  -w -O3 -qarch=auto -qchars=signed -c ./asmg.c -o ../obj/asmg.o

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


and the XLC app opens.
How do I use it?

---

### Post by albinootje on 2009-02-01
> **zebrafish said:**
> 
xlc: invalid option -- 'w'

Where did you download the assembler software ?

This web page [http://www.jcvi.org/cms/research/software/](http://www.jcvi.org/cms/research/software/) says :
> 
 TIGR Assembler

Enabled the first published whole-genome assembly of a free-living organism in 1995. Last revised in 2003.

This link, found via Google, [http://sourceforge.net/projects/tigr-assembler](http://sourceforge.net/projects/tigr-assembler) gives an error.
If this software is really 5 years old, then it is not surprising you're really into trouble compiling and using it.
Your best bet would be using some Linux distribution from 2003 to make this run.

---

