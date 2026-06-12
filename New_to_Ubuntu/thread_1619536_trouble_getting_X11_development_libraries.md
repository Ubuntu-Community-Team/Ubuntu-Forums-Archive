---
title: "trouble getting X11 development libraries"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by calinabris on 2010-11-11
Hello, been trying to install Mesa-7.8.3, can't get the X11 library, searched around for a while yesterday and again today trying to find a way to get them, no luck. any help would be great. tried the sudo apt-get, that I've run across in posts that have solved it for other people but it doesn't seem to work for me. 


thanks

```
cal@ubuntu:~$ /home/cal/Mesa-7.8.3-rc1/configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gmake... no
checking for make... make
checking for makedepend... no
checking for sed... /bin/sed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc version is sufficient... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether gcc supports -fvisibility=hidden... yes
checking whether to enable assembly... yes, x86
checking for gcc option to produce PIC... -fPIC
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for posix_memalign... yes
checking pkg-config files for X11 are available... no
checking for X... no
configure: error: X11 development libraries needed for dri driver
cal@ubuntu:~$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-dev
cal@ubuntu:~$ sudo apt-get install libx11-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libx11-dev
cal@ubuntu
```:~$

---

### Post by albertwt on 2010-11-14
yes, I also face the similar problem when I need to install on my Ubuntu 10.4 Server 64 bit, need X Window libraries for the Adobe Livecycle 2.5 install.

---

### Post by calinabris on 2010-11-28
Still can't fix the problem. please help.

---

### Post by oscarbotia on 2011-01-14
sudo apt-get -y install libx11-dev

---

