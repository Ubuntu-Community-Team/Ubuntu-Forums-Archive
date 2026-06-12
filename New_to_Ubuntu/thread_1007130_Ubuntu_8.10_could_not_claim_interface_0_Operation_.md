---
title: "Ubuntu 8.10: could not claim interface 0: Operation not permitted."
date: 2008-12-10
forum: New to Ubuntu
---

### Post by biggerstone on 2008-12-10
Hi,All:
   i have downloaded a boot_usb tools from [http://svn.openezx.org/trunk/src/host/boot_usb/](http://svn.openezx.org/trunk/src/host/boot_usb/). i make it successfuly under my Ubuntu 8.10 
   (Header file verison: /usr/src/linux-headers-2.6.27.7). My make file include is : INC ?= /home/administrator/andorid/linux-2.6.24/include.
  If not setting this path, make error and output: asm-arm/setup.h:No such file or directory.  
  
  According with the guideline of "http://www.motorolafans.com/forums/android-os/21887-porting-andoid-a1200-ming.html", when i upload zImage-a1200 file to 
  Motorola Ming A1200 by usb_boot. An error occures:
administrator@ubuntu:~/boot_usb-0.2.0$ ./boot_usb zImage-a1200
Serching for EZX phone: E2/A1200/E6/A910 found.
FAILED: claim usb interface 1 of device: could not claim interface 0: Operation not permitted
administrator@ubuntu:~/boot_usb-0.2.0$ 
administrator@ubuntu:~/boot_usb-0.2.0$ pwd
/home/administrator/boot_usb-0.2.0

I add a item to /etc/udev/rules.d/45-libmtp8.rules according by "http://ubuntuforums.org/showthread.php?t=346840", but the problem still exist.

If anybody can tell me why???

---

