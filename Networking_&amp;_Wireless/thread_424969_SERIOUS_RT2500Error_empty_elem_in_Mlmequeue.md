---
title: "SERIOUS: RT2500Error: empty elem in Mlmequeue"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by eiapoce on 2007-04-27
I tried compiling the Ralink RT2500 drivers found at [http://www.serialmonkey.com/](http://www.serialmonkey.com/) - The make process presented some errors but I was in a hurry to make a wireless connection functional. So I finisched with a sudo make install.

Now I can't login anymore to the tty shells ( <CTRL><ALT><F1-F6>) All I get is this error line repeating at infinitum.

```
RT2500Error: empty elem in Mlmequeue
```

How I remove th driver and from where??? 

Enrico

---

### Post by eiapoce on 2007-04-27
Well I solved with a clean re-install. Looks like the old Microsoft Windows 95 way of dealing with the problems is still actual in 2007.

---

### Post by erm67 on 2007-04-28
boot in single user mode next time

---

### Post by bloggins666 on 2007-04-28
I also ran into compile errors while trying to compile the serial monkey rt2500 driver version:1.1.0-b4. The error was that the macro INIT_WORK() was being called with 3 parameters but only needs 2. I tried to figure out which parameter to remove and of course this caused the kernel to lock up as soon as I fired the gun or rather did the insmod rt2500.ko.

Does anyone know what the solution to this problem is? I gather that this version of the driver is just not compatible with the 2.6.20 kernel which is what is delivered by Feisty Fawn.

Cheers!!

---

