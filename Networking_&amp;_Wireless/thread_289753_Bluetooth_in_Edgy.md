---
title: "Bluetooth in Edgy"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by richjoyce on 2006-10-31
I'm at a loss of what to try to do next trying to get my bluetooth usb dongle to work.  Here's the output of my lsusb:
Bus 004 Device 003: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

Googling that led me to:
[http://akosidexter.wordpress.com/2006/10/19/xubuntu-internet-over-gprs-via-bluetooth/](http://akosidexter.wordpress.com/2006/10/19/xubuntu-internet-over-gprs-via-bluetooth/)

Which states that my chipset should work...promising, however, when i run hcitool dev, I get:
foo@bar:~$ hcitool dev
Devices:
foo@bar:~$ 

Where can I look for more output on this, or what can I do to get this working

---

### Post by richjoyce on 2006-10-31
FIXED:
Turns out I just had to take it out of my usb hub and plug it directly into the computer!

---

