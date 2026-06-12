---
title: "AR5007UG not detected by gusty &amp; feisty"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by apamatos on 2007-10-19
Hello

I have a Packard Bell easynote SW51 (AMD Turion 64) that uses an AR5007UG (=zd1211b?) wireless chip. This is not detected (not listed in network manager) by Feisty and Gusty.
I checked lsmod that lists the zd1211rw driver and lsusb that lists the Zydas USB interface. However there is no network interface (ex: eth1) associated with the driver.

As far as I read, I guess I should have an interface automatically mounted and be able to work with it.

Can anyone help please?
Somewhat urgent...

Thanks in advance
AP Alves de Matos
Portugal

---

### Post by isoengas on 2007-10-22
See my [reply]("http://ubuntuforums.org/showthread.php?t=583900&highlight=ar5007ug") to this post

---

### Post by apamatos on 2007-10-22
Thanks for the very valuable information. 
On the top of all this there is another issue, since I'm using the AMD64 version of gusty (it didn't work also with 32bit Feisty). I think that there are 64bit windows (to use with ndiswrapper) drivers to the chip but all links seem to be dead! 
Several posts point to the need to use 64 bit drivers with this version of ubuntu. Do you know if the new kernel for AMD64 comes with the correct drivers?

AP

---

