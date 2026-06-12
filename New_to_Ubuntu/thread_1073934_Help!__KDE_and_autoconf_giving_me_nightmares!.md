---
title: "Help!  KDE and autoconf giving me nightmares!"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by heddasgun on 2009-02-18
Where to begin? Well I'm trying to broaden my horizons and learn some C++.  How disappointed I am that I can't even get the "Hello World" project to work! 
I'm such a noob!  I'm not ashamed to admit it.  I've spent the last 2 days pouring over forums, tutorials, etc. and I can't get the help I need.  Of the many problems I have, the most immediate is this error message..

/home/mac/devKDE/hello/debug
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?

when I run automake i get this fantastic error in KDE

cd '/home/mac/devKDE/hello' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/mac/devKDE/hello/debug' && cd '/home/mac/devKDE/hello/debug' && CXXFLAGS="-O0 -g3" "/home/mac/devKDE/hello/configure" --enable-debug=full && cd '/home/mac/devKDE/hello/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
This Makefile is only for the CVS repository
# Unable to find autoconf!!
# Unable to find autoheader!!
# Unable to find autom4te!!
# Unable to find automake!!
# Unable to find aclocal!!
This will be deleted before making the distribution
./admin/cvs.sh: 651: --version: not found

make[1]: *** [cvs] Error 1
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make: *** [all] Error 2
*** Exited with status: 2 ***


I have autoconf 2.13, but when I try to get a newer version using

sudo apt-get install autoconf2.63

i get this,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package autoconf2.63


I downloaded autoconf 2.63 from sourceforge but I have no idea how to install it.

I must admit I haven't entered code like this since I was a little girl running DOS programs.  Most of these commands mystify me completely.  If someone with a lot of patience could help me, using small words, I'd be grateful.

---

### Post by heddasgun on 2009-02-20
Yesterday I used Synaptic, uninstalled KDE and reinstalled it with what seems to be the proper version of autoconf etc.  Now I'm wondering if qt4 is the problem.  Should I be using qt3 instead?  The good/bad news is I got a new error message when I try to build with KDE and here it is...


```
cd '/home/mac/devKDE/hello/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="0" LC_MESSAGES="C" LC_CTYPE="C" make
make all-recursive
Making all in doc
Making all in .
make[3]: Nothing to be done for `all-am'.
Making all in en
make[3]: Nothing to be done for `all'.
Making all in po
make[2]: Nothing to be done for `all'.
Making all in src
compiling hello.cpp (g++)
linking hello (g++)
hello.o: In function `main':
/home/mac/devKDE/hello/src/hello.cpp:24: multiple definition of `main'
main.o:/home/mac/devKDE/hello/src/main.cpp:39: first defined here
main.o: In function `main':
main.cpp:(.text+0x25d): undefined reference to `hello::hello()'
main.cpp:(.text+0x2bc): undefined reference to `hello::hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x24): undefined reference to `hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x28): undefined reference to `hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x260): undefined reference to `non-virtual thunk to hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x264): undefined reference to `non-virtual thunk to hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x294): undefined reference to `non-virtual thunk to hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x298): undefined reference to `non-virtual thunk to hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x300): undefined reference to `virtual thunk to hello::~hello()'
hello.moc.o:(.rodata._ZTV5hello[vtable for hello]+0x304): undefined reference to `virtual thunk to hello::~hello()'
collect2: ld returned 1 exit status
make[2]: *** [hello] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***
```

---

