---
title: "Compiling NDISWrapper"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by darklordveynom on 2007-10-23
Hi. I have no clue what I'm doing. I had my WUSB54GSC usb wireless network adapter working under Ubuntu until I updated to the new version that came out last thursday. When I try to do : sudo modprobe ndiswrapper  it says "FATAL: could not locate module ndiswrapper". I decided that I would try to compile it from source, but this is what it gave me

veynom@veynom-lunix:~/ndiswrapper-1.48$ make

make -C driver
make[1]: Entering directory `/home/veynom/ndiswrapper-1.48/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.22-14-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/veynom/ndiswrapper-1.48/driver'
make: *** [all] Error 2
veynom@veynom-lunix:~/ndiswrapper-1.48$ cat /proc/version
Linux version 2.6.22-14-386 (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 

Sun Oct 14 22:36:54 GMT 2007
veynom@veynom-lunix:~/ndiswrapper-1.48$ modinfo ndiswrapper
modinfo: could not find module ndiswrapper

Please help me.

---

### Post by ozone702 on 2007-10-24
When are the guys at Ubuntu ever going to create a standard for installing drivers and make it easier for us idiots to get a system up and running?

This has got to be the number one issue people have that stop them from moving to Ubuntu.

ozone

---

### Post by darklordveynom on 2007-10-24
Well, I figured it out, but to help others who may run into this problem here's what I did.

Look for the kernel-headers for gutsy with 2.6.22-14-386 at the end and install it. then follow the instructions in the NDISwrapper's INSTALL file. easy.

---

