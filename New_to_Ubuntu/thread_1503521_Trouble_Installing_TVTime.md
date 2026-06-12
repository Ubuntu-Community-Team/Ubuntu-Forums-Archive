---
title: "Trouble Installing TVTime"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by charliechip95 on 2010-06-06
Hi! I'm brand-new to Linux Ubuntu (10.04), been using Windows XP for a long time before we switched over. So, needless to say, I'm also new at installing tar.gz files.. anyway, I've run into a problem installing TVTime. First, using cd commands in the terminal, I navigated to the folder with the tar.gz file, and extracted it using the "tar -xzvf" command. This seemed to work just fine. Then I went to the new folder created, and entered

"./configure --prefix=/usr --sysconfdir=/etc"

as it said to in the the INSTALL file, and it gave me this:

"~/Downloads/tvtime-1.0.1$ ./configure --prefix=/usr --sysconfdir=/etc
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g++... no"

I'm guessing maybe this means that I don't have some things installed that are needed... I tried the "make" anyway and it said:

"~/Downloads/tvtime-1.0.1$ make
make: *** No targets specified and no makefile found.  Stop."

So I'm not sure what to do at this point -- if I have to install something I'm not sure how to do it, being new to Ubuntu. Make sure to make any instructions you give noob-friendly. Thanks!

---

### Post by charliechip95 on 2010-06-07
Help? :KS

---

### Post by WinterRain on 2010-06-07
Why are you compiling it?
```
sudo apt-get install tvtime
```
will do the trick.

You can install most things with ubuntu software center or synaptic package manager.

---

### Post by Pulsartomi on 2012-05-24
Thank You WinterRain, I made it with Your help :)

---

### Post by recap on 2012-05-24
Thanks! :d

---

### Post by lisati on 2012-05-24
Old thread closed

---

