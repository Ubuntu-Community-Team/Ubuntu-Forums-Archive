---
title: "Wireless drivers for ubuntu 10.10 (inspiron 14R)"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by kmr3322 on 2011-03-20
Hey guys...

My Dell Inspiron 14R is not connecting to WiFi network. There are no drivers for wireless system in my laptop and I am unable to update my OS.

How to get it worked? How to get the drivers? I will be very much thankful if anyone help me out....:confused:

---

### Post by wep940 on 2011-03-20
First we need to know what model/chipset the adapter is:
 
- open a terminal window (Applications/Accessories/Terminal)
- type:  lspci <press enter>  and  lsusb <press enter>.  Post the output of both of those back here for us to check.

---

### Post by kmr3322 on 2011-03-20
Bus 002 Device 002: ID 8087:0020 Intel corp. Integrated Rate Matching Hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:641d Microdia
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub

Bus001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Is this what you have asked?

---

### Post by wep940 on 2011-03-20
> **kmr3322 said:**
> Bus 002 Device 002: ID 8087:0020 Intel corp. Integrated Rate Matching Hub
 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:641d Microdia
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
 
Bus001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
 
Is this what you have asked?
 
That's part of it - the "lsusb" which lists the known USB devices on your PC.  I checked the Microdia manufacturer:devid and see it is a web cam.  So, it appears your wireless is not a USB device, meaning it is most probably an internal mini PCI card.  If you could do the other command and post it's results that would help:
 
- open a terminal window
- type:  lspci <press enter>
 
Post the output back here.
 
Thanks!

---

### Post by wep940 on 2011-03-20
I just found this thread - perhaps it can help you with your 14R:
 
[http://ubuntuforums.org/showthread.php?t=1569966](http://ubuntuforums.org/showthread.php?t=1569966)

---

