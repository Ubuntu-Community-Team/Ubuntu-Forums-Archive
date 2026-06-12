---
title: "ndiswrapper and Philips CPWUA054"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by victorvictorvict on 2007-05-07
Hello everybody!
I'm having weird troubles with my USB-WLAN adapter (a Philips wireless usb adapter 11g, CPWUA054/00) and ndiswrapper.
The device IS listed as supported on ndiswrapper's list of cards.

I'm running Feisty on a Pentium 4 3.0 GHz.
(The built-in help btw says that ndiswrapper is on the Ubuntu CD which it is not, someone should fix that...)

At first I tried using drivers from Philips's homepage but they didn't work at all and after some googling I found a post about the online drivers being older than the ones on the cd, so I installed using the ones from my CD instead. 

The weird part about this is that if I now:
$ ndiswrapper -l

I get:
cpwua2d driver present, hardware present

and the LED on the device lights up for a second (it's turned off otherwise) but it still IS NOT WORKING! as in no listing of a wireless device is showing up in the Network admin utility.

I am not getting ANY error messages, in dmesg or when modprobe or depmod -a. It's as if everything is working except it's not.

Any ideas?

---

