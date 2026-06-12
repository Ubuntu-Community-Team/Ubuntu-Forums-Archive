---
title: "cannot find -lf2c"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by santhust on 2009-06-12
Hi,

when i compiled levmar-2.4 i encountered the following:


santhust@santhust-laptop:~/levmar-2 (copy).4$ make -f Makefile
gcc -L/usr/local/lib  -L. lmdemo.o -o lmdemo -llevmar -llapack -lblas -lf2c  -lm
/usr/bin/ld: cannot find -lf2c
collect2: ld returned 1 exit status
make: *** [lmdemo] Error 1


i am trying to use levmar which is a C/C++ implementation of Levenberg-Marquardt nonlinear least squares minimization algorithm that is distributed under the GNU General Public License. 

any help will be greatly appreciated. thanks

---

### Post by Rubicon_82 on 2009-06-12
You should find the libraries you need in the *libf2c2-dev* package.

---

### Post by santhust on 2009-06-14
hi, **thanks**.

i searched libf2c2-dev package in synaptic package manager and then installed it. On compilation of the levmar-2.4 "cannot find lf2c" didn't appeared. But the problem wasn't solved. this is what appeared, when i compiled: 


-*- mode: compilation; default-directory: "~/levmar-2.4/" -*-
Compilation started at Sun Jun 14 14:19:44

make -k 
gcc -L/usr/local/lib  -L. lmdemo.o -o lmdemo -llevmar -llapack -lblas -lf2c  -lm
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libf2c.so: undefined reference to `MAIN__'
collect2: ld returned 1 exit status
make: *** [lmdemo] Error 1
make: Target `all' not remade because of errors.

Compilation exited abnormally with code 2 at Sun Jun 14 14:19:45



i couldn't understand it. could you help a bit more.

_this down below is the program i am trying to compile:_



#
# Unix/Linux GCC Makefile for Levenberg - Marquardt minimization
# Under windows, use Makefile.vc for MSVC
#

CC=gcc
CONFIGFLAGS=#-ULINSOLVERS_RETAIN_MEMORY
#ARCHFLAGS=-march=pentium4 # YOU MIGHT WANT TO UNCOMMENT THIS FOR P4
CFLAGS=$(CONFIGFLAGS) $(ARCHFLAGS) -O3 -funroll-loops -Wall #-pg
LAPACKLIBS_PATH=/usr/local/lib # WHEN USING LAPACK, CHANGE THIS TO WHERE YOUR COMPILED LIBS ARE!
LDFLAGS=-L$(LAPACKLIBS_PATH) -L.
LIBOBJS=lm.o Axb.o misc.o lmlec.o lmbc.o lmblec.o
LIBSRCS=lm.c Axb.c misc.c lmlec.c lmbc.c lmblec.c
DEMOBJS=lmdemo.o
DEMOSRCS=lmdemo.c
AR=ar
RANLIB=ranlib
LAPACKLIBS=-llapack -lblas -lf2c # comment this line if you are not using LAPACK.
                                 # On systems with a FORTRAN (not f2c'ed) version of LAPACK, -lf2c is
                                 # not necessary; on others, -lf2c is equivalent to -lF77 -lI77

#LAPACKLIBS=-L/usr/local/atlas/lib -llapack -lcblas -lf77blas -latlas -lf2c # This works with the ATLAS updated lapack and Linux_P4SSE2
                                                                            # from [http://www.netlib.org/atlas/archives/linux/](http://www.netlib.org/atlas/archives/linux/)

#LAPACKLIBS=-llapack -lgoto -lpthread -lf2c # This works with GotoBLAS
                                            # from [http://www.tacc.utexas.edu/resources/software/](http://www.tacc.utexas.edu/resources/software/)

#LAPACKLIBS=-L/opt/intel/mkl/8.0.1/lib/32/ -lmkl_lapack -lmkl_ia32 -lguide -lf2c # This works with MKL 8.0.1 from
                                            # [http://www.intel.com/cd/software/products/asmo-na/eng/perflib/mkl/index.htm](http://www.intel.com/cd/software/products/asmo-na/eng/perflib/mkl/index.htm)

LIBS=$(LAPACKLIBS)

all: liblevmar.a lmdemo

liblevmar.a: $(LIBOBJS)
	$(AR) crv liblevmar.a $(LIBOBJS)
	$(RANLIB) liblevmar.a

lmdemo: $(DEMOBJS) liblevmar.a
	$(CC) $(LDFLAGS) $(DEMOBJS) -o lmdemo -llevmar $(LIBS) -lm

lm.o: lm.c lm_core.c lm.h misc.h compiler.h
Axb.o: Axb.c Axb_core.c lm.h misc.h
misc.o: misc.c misc_core.c lm.h misc.h
lmlec.o: lmlec.c lmlec_core.c lm.h misc.h
lmbc.o: lmbc.c lmbc_core.c lm.h misc.h  compiler.h
lmblec.o: lmblec.c lmblec_core.c lm.h misc.h

lmdemo.o: lm.h

clean:
	@rm -f $(LIBOBJS) $(DEMOBJS)

cleanall: clean
	@rm -f lmdemo
	@rm -f liblevmar.a

depend:
	makedepend -f Makefile $(LIBSRCS) $(DEMOSRCS)

# DO NOT DELETE THIS LINE -- make depend depends on it.

---

### Post by fergalm on 2009-07-18
I'm having a similar problem to the OP. I'm trying to build pgplot ([www.astro.caltech.edu/~tjp/pgplot/](www.astro.caltech.edu/~tjp/pgplot/)) which has C bindings to Fortran functions. Everything works up until the point of

```

 f77 -o cpgdemo cpgdemo.o -L`pwd` -lcpgplot -lpgplot [COLOR="Red"]-lf2c[/COLOR] -L/usr/X11R6/lib -lX11 \
-L/usr/lib/gcc/i486-linux-gnu/4.3.3 \
-L/usr/lib/gcc/i486-linux-gnu/4.3.3 \
-L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib \
-L/lib/../lib \
-L/usr/lib/../lib \
-L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../..\
 -lgcc -lm -lc

```

which gives a similar error message
```

/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libf2c.so: undefined reference to `MAIN__'
collect2: ld returned 1 exit status

```

I'm running a fresh install of Ubuntu 9.04, with the following packages installed
[LIST]
[*]xorg-dev
[*]fort77
[*]libf2c
[*]gfortran
[/LIST]

and a couple of other things like svn, gv etc. that are unrelated.

I've gotten pgplot to install on 8.04 before, so I suspect that there's some new package I need to set up or something silly like that. But any help is appreciated.

---

### Post by fergalm on 2009-07-20
What what it's worth, I solved my problem using gfortran to compile instead of f77. Hope that helps someone else.

---

### Post by musi on 2009-08-05
I had the same problem. 
Searching in the web i found one post that proposed to first delete libf2c.so in /usr/lib and then to make a new link to libf2c.a: ln -s libf2c.a libf2c.so.
This you can only do as su.
This solved my problem. 
Hope that helps someone.

---

### Post by nameslight on 2010-12-03
> **musi said:**
> I had the same problem. 
Searching in the web i found one post that proposed to first delete libf2c.so in /usr/lib and then to make a new link to libf2c.a: ln -s libf2c.a libf2c.so.
This you can only do as su.
This solved my problem. 
Hope that helps someone.

I tried this and worked! Thank you very much!

---

