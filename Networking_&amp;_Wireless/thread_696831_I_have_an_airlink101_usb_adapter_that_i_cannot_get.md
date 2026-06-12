---
title: "I have an airlink101 usb adapter that i cannot get working, please help"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by ogwilson on 2008-02-14
[http://www.airlink101.com/products/awll3025v2.html](http://www.airlink101.com/products/awll3025v2.html)
 
I have this wireless USB adapter. I tried using ndiswrapper but i got an error trying to install it from the disc saying
 
[COLOR=#000000]not dependent llbvc[/COLOR]
 
[COLOR=#000000]or something to that effect. Well, I cannot get online to see if there are any restricted drivers for this available, which there probably aren't. Well, does anyone know if there is anything I can do?[/COLOR]

---

### Post by ogwilson on 2008-02-14
After snooping around on the net, I found some more info.
 
The chipset is Zaydas Z1211, if that helps at all. I found something on this:
 
[http://linuxwireless.org/en/users/Download#Requirements](http://linuxwireless.org/en/users/Download#Requirements)
 
Does anyone think this will help me?

---

### Post by rustybronco on 2008-02-14
Z**D**1211 chipset? if so it should work.
output of lsusb and look for an i.d **like** this xxxx:xxxx
this might help also with the i.d. [http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices)

---

### Post by ogwilson on 2008-02-14
Yesm thank you, I meant ZD1211.
 
Well, that page is the one i originally came across while searching info on it. I tried the specific method on that site, but to no avai.

---

### Post by rustybronco on 2008-02-14
please post the output of **lshw -C network**
**iwlist scan **
and **lsusb**

and **Kevdog's finest** work on connecting from the command line with troubleshooting tips.
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

