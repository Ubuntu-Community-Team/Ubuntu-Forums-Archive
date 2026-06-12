---
title: "BCM43xx and compiling kernel 2.6.22.1 on Feisty?"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by affected on 2007-07-22
I'd like to compile the new kernel 2.6.22.1, partly due to the new wifi stack, partly for other optimizations it provides, but apparently the bcm43xx driver for the new stack is not merged in the kernel, which I take to mean that I would have to compile that module for the kernel myself. 

Is this correct, am I likely to run into a lot of trouble trying to get it to work, and is there any significant improvement in the functioning of the bcm43xx driver when using the new stack? Mainly, will it support connection speeds over 11 Mb/sec? If not, then I guess I may as well continue using ndiswrapper as I do now.

---

### Post by kevdog on 2007-07-22
I could be wrong but I thought I read somewhere else that the native bcm43xx driver that works > 11Mb/sec had only been released for the Fedora Core, and has yet to be written for other distros (ie Debian).  I could be wrong.  I think this is the reason its not included in the Gusty development currently.

---

