---
title: "Help: How to Compile Source Code"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by catzlai on 2009-03-26
I am an absolute newbie so be kind to me.

I need to write c program for school work and my university has provided the programming tool and the source code is here:

[http://www.maths.cam.ac.uk/undergrad/catam/ccatsl/ccatsl2.2a.src.zip]("http://www.maths.cam.ac.uk/undergrad/catam/ccatsl/ccatsl2.2a.src.zip")

Can someone teach me how to compile the source code on Ubuntu 8.10, please?
Why can't I just put "#include<catam.h>" in my c program without compiling the source code?

---

### Post by Anthon on 2009-03-26
The source code does not get executed as a program directly. The C-language statements first need to be compiled into an executable, that Ubuntu knows how to load into memory and run.

This is different from interpreted languages or languages that are compiled 'on the fly', although those get converted from human readable source code to executed steps as well (but transparently).

---

### Post by catzlai on 2009-03-26
So what do I need to do to compile my own c program with the new catam.h library?

---

### Post by Anthon on 2009-03-26
Assuming the file for program you created is callde program.c:
   cc -o program program.c
from the commandline and then to run it (assuming there were no compile errors):
  ./program

---

### Post by KIAaze on 2009-03-26
They gave you a Makefile with the code! Use it! :)
Just type:
```
make
```

Ok, now I tested it and of course your evil teachers not only didn't tell you how to use it, but they gave you a Makefile for Windows only!
I adapted the Makefile for you (most important change: link with libm.so instead of with user32.dll):
```
  ######################################################################
  #                                                                    #
  #  Rudimentary Makefile for using CCATSL source code                 #
  #  dnh - damtp - 2006-09-04
  #                                                                    #
  ######################################################################

# make lib    or make  something.exe
# 

# If your compiler likes [][] uncomment this:
#CATFLAGS  	= -DCCATSL2D

INCDIR		= .
CCATSLSRC	=  ccatslnum.c
CCATSLOBJ	=  ccatslnum.o
CCATSLINC	=  ccatslnum.h
STRIPOPT	= -Wl,--strip-all

LDFLAGS = $(CCATSLOBJ) -I$(INCDIR) $(STRIPOPT) -lm

BIN = testphi testroots
BINWIN = $(BIN:=.exe)

%:	%.c $(CCATSLOBJ)
	gcc  $< $(CCATSLOBJ) -o $@ -I$(INCDIR) $(STRIPOPT) -lm

%.exe:	%.c $(CCATSLOBJ)
	gcc  $< $(CCATSLOBJ) -o $@ -I$(INCDIR) $(STRIPOPT) -luser32

all: $(BIN)

allwin: $(BINWIN)

lib:	$(CCATSLOBJ)

$(CCATSLOBJ):	%.o:	%.c %.h
	gcc  -c $< -o $@ -I$(INCDIR)

clean:
	rm -f *.o *.exe $(BIN)

```

_On GNU/Linux:_
First of all make sure you install the **build-essential** package:
```
sudo apt-get install build-essential
```
Then:
```

#compile
make
#run tests
./testphi
./testroots

```
_On Windows:_
```

#compile
make allwin
#run tests
./testphi.exe
./testroots.exe

```

_To compile manually on GNU/Linux (it's important to know how to do this):_
```
gcc  -c ccatslnum.c -o ccatslnum.o -I.
gcc  testphi.c ccatslnum.o -o testphi -I. -Wl,--strip-all -lm
gcc  testroots.c ccatslnum.o -o testroots -I. -Wl,--strip-all -lm

```
The Makefile is just there so you don't have to enter the above commands manually. ;)

I attached the whole thing below:

---

### Post by catzlai on 2009-03-26
This works!!!!
Thanks a lot for your help! =)

---

