---
title: "New to Linux from mac, help with wireless"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Dharmapunx13 on 2009-03-26
I am used to my mac OS X on which i simply click on the airport and choose a wireless connection from the surrounding area. I recently started dual booting with Ubuntu 8.10 and Network Connection makes no sense to me. I'm sitting at school where I should have a strong wireless connection but the option to choose this connection doesn't even come up. I've tried at other hotspot areas as well. I want to know how to run my network Connections and view available hotspot sources.
Searching on the internet only makes me confused because I'm new to Linux and controlling a computer system, please avoid using jargon, or do me one better and use it then explain it so I understand.
Thank You!!

---

### Post by avtolle on 2009-03-26
We need to know the chipset for your wireless card (if an airport, I'm guessing it will be Broadcom). Please open a terminal (Go to Applications in the top panel, click on it, then from the list click on Accessories, then from the next list select Terminal). After the prompt that appears type```
lspci
```which will provide more information than just your wireless card, and post the output here for review.

---

### Post by Dharmapunx13 on 2009-03-26
I'm currently on my OS X partition, but I think this is the same information:
AirPort Card Information:

  Wireless Card Type:	AirPort Extreme  (0x14E4, 0x88 )
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	Broadcom BCM43xx 1.0 (5.10.38.24)
  Current Wireless Network:	Wi-EWU-access
  Wireless Channel:	11

---

### Post by mlentink on 2009-03-26
Sorry to butt in, but please keep in mind that, whereas Apple only needs to worry about its own hardware, Ubuntu needs to cater to just about every exotic network card around. 
So it might not be able to provide support immediately out of the box.

---

### Post by LowSky on 2009-03-26
Broadcom sometimes has a few issues, you might need a proprietary driver dont worry its should be easy

At top panel go to system> administration > restricted drivers 
click to add the driver, and things should work after a reboot

EDIT: If that doesn't work you might need to add another package.
NOTE: you will need a wired internet connection in Ubuntu to download the drivers

---

