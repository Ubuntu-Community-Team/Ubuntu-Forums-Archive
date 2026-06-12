---
title: "Compiling rtl8185 drivers"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by TinBane on 2007-06-29
I downloaded the latest drivers and it has a script to compile everything, problem is, it doesn't work.

This is it's contents:

#!/bin/bash

tar -zvxf stack.tar.gz
tar -zvxf rtl818x.tar.gz
cd ieee80211
make clean
make
cd ../rtl818x-0.1
make clean
make
cd ../

Pretty straight forward. So I go through the steps and on make, i get this error:
adrian@Ubuntu-Sempron:~/Desktop/Wireless Drivers/rtl8185_linux_26.1010.0531.2006/ieee80211$ sudo make
make -C /lib/modules/2.6.20-15-generic/build M=/home/adrian/Desktop/Wireless Drivers/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** No rule to make target `Drivers/rtl8185_linux_26.1010.0531.2006/ieee80211'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

Problem is, there is a Makefile in the directory. Is it broken? I'm using the ndiswrappers for this driver, but there are a lot of problems.

Any idea on compiling it?

---

### Post by TinBane on 2007-06-30
BUMP.

Seriously, nobody has any ideas?

---

### Post by kevdog on 2007-06-30
You need to install the build-essential package first:

If you have an internet connection type skip to step #4, if you dont start at step #1:
#1 Place ubuntu installation cd-rom in driver, wait for it to become ready
#2. At command line type: sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

Why do you want to compile these drivers anyway??  There is already a version contained in the kernel by default

---

### Post by creakyknees on 2008-07-05
Hi kevdog

I've been trawling the forums for two and a half days now to get a Zyxel PCI wireless card to work - you seem to understand how to get this chipset to work

I'm running 8.04 on a new install and cannot get it to work.

You mention: "Why do you want to compile these drivers anyway?? There is already a version contained in the kernel by default"

Where is it? How do I 'activate' it?

Any help would be greatly appreciated.

Thanks

---

