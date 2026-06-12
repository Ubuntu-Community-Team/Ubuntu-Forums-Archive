---
title: "Can't install/compile this program."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-09
I'm trying to install this program that's not in synaptic. The instructions are simple, but they don't work for me. I have GCC compiler 4.3 installed. 

It says to type ./configure, and this is what happens.






checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
configure: error: The C++ compiler doesn't work or doesn't exists at all!
*********************************************************************
* Check your C++ installation (many distributions have a separate   *
* package for the C++ compiler).                                    *
*********************************************************************
root@rob-desktop:/home/rob/Desktop/worker# make
make: *** No targets specified and no makefile found.  Stop.
root@rob-desktop:/home/rob/Desktop/worker# make install
make: *** No rule to make target `install'.  Stop.

---

### Post by alien21010 on 2009-09-09
First of all did you install build-essential?  

sudo apt-get install build-essential

Then run, which g++.  Something along the lines of /usr/bin/g++ should return.  If not, then you don't have a c++ compiler installed (although I would find that hard to believe if you installed GCC).  

Lastly, you almost never should run make as root, it's not needed, and can be very damaging depending on what you are doing.  It's also important because the root account does not inherit the environment that you were working in (which may be why it does not know how to find g++).  Therefore, try building outside of root too.

---

