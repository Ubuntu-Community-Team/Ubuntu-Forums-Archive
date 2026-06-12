---
title: "wireless set up"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-07
Hi
I am trying to set up my wireless connection at present ,for my wireless connection I use a netgear WNP111 dongle .In a past post i was asked for the output of two coads,lspci -nn ,and    lsusb ,                                                                      Bus 003 Device 004: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:7a04 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:08b4 Logitech, Inc. QuickCam Zoom
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
david@david-desktop:~$ 



Am i right in thinking that my dongle has no driver to make it work .
I have downloaded ndiswrapper common from the web site ,but i don't think that i have installed it as I cannot find it on my system .
Can someone help please .

---

### Post by mapes12 on 2009-01-07
Your dongle does not appear to be natively supported. But this thread may help get it working: [http://ubuntuforums.org/showthread.php?t=844856](http://ubuntuforums.org/showthread.php?t=844856)

Alternatively, you may want to get a natively supported device: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)  

I've got this one in my laptop which is simply plug and play: [http://www.linuxemporium.co.uk/products/wireless/#pidR26799](http://www.linuxemporium.co.uk/products/wireless/#pidR26799)

---

### Post by 3rdalbum on 2009-01-07
It sounds to me like your wireless dongle needs "firmware" in order for it to work. Firmware is sorta like software that runs on the device itself. The good news is, you can load the firmware just by downloading a single file and putting it into /lib/firmware. The bad news is, this might not cause the adapter to spring to life (it might need a driver as well), but it's the best place to start!

Search on Google for "WPN111 firmware" and you might find the file you need.

---

### Post by garrydog on 2009-01-07
Hi
I have found the firmware on Google ,will it have to be a ubuntu file ,or will a wondows file work .the one i am downloading is ,WNP111-2

---

