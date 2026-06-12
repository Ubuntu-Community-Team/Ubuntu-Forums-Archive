---
title: "No wireless in custom kernel"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by Charles Hand on 2006-08-27
Whenever I try to build a kernel, the result is no wireless. I'm doing a straight make oldconfig, and I don't understand why that doesn't build an identical kernel to the one I'm using. I don't know where to find the wireless device name. The closest thing I can find (while booted to the kernel that works) is in device manager, under WLAN interface, org/freedesktop/Hal/devices/pci_8086_4222, but there's nothing like that in menuconfig wireless device drivers.

Give me an idea where to begin to figure out why the new kernel doesn't support the wireless.

---

### Post by funchords on 2006-08-27
That code is the Intel 3945ABG Wireless LAN controller.  

This is a bit over my head, but I don't think Intel provides the source code.  Could that have something to do with it?

---

### Post by Zanthius on 2006-08-27
I'm having the same issues... i'm trying to download and install the ipw drivers now... but I dont see why I have to do this when it worked fine straight from the kernel 2 version ago....

---

### Post by Zanthius on 2006-08-28
I just followed all the install instructions on this page:
[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)

but still nothing... I might try re-compiling the kernel again after doing that...

---

