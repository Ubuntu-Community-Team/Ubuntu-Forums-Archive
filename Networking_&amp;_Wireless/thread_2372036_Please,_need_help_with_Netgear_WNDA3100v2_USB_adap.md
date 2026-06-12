---
title: "Please, need help with Netgear WNDA3100v2 USB adapter [BCM4323]"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by ninjad0d0 on 2017-09-20
I'm running Ubuntu 16.04.3 and have the bcmn43xx64.inf installed (had it saved on flash drive from when I briefly used it before in Ubuntu 16.04.2 and it worked) but the adapter is not popping to life after update.  I do also have the Rosewill RNWD-N9003PCE card installed which works fine right out of the box, but I would like to get my Netgear adapter ginning again because it has noticeably greater range.  Oh, I don't know a thing about Linux systems, so if you tell me what you need to know I'll fetch it.  

lsusb:
killerpythons@killerpythons-SX2850:~$ lsusb
Bus 002 Device 004: ID 058f:6363 Alcor Micro Corp. 
Bus 002 Device 003: ID 0781:5575 SanDisk Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 258a:0001  
**Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]**
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present

usb-devices
T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0846 ProdID=9011 Rev=00.01
S:  Manufacturer=Broadcom
S:  Product=Remote Download Wireless Adapter
S:  SerialNumber=0
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=ff Driver=(none)

---

### Post by ninjad0d0 on 2017-09-21
Hello?  Any experts on here?

---

### Post by jeremy31 on 2017-09-21
See [https://askubuntu.com/a/568118/300665](https://askubuntu.com/a/568118/300665)
It seems to need ndiswrapper which isn't as good as a USB adapter that is supported by a kernel module

---

### Post by ninjad0d0 on 2017-09-21
Already been there, done that.  No go.  I just got lucky in Ubuntu before using Windows Wireless Drivers, saved the drivers for later just in case.  Not working in latest update 16.04.3.

---

### Post by ninjad0d0 on 2017-09-21
I just want to add that it isn't my pci card interferring with it because I shut down, removed the card, booted back up, and no recognition other than what I've already posted.

---

### Post by ninjad0d0 on 2017-09-21
I also tried the driver on the installation disk (bcmwlhigh6) and no go, same with bcmwlhigh5.

---

### Post by ninjad0d0 on 2017-09-21
And yes, I tried the 32 bit version of each so far.  No go.  No, the drivers are not installed at the same time.

---

### Post by ninjad0d0 on 2017-09-21
I'd also like to mention that all related driver links in Ubuntu Forums return "page not found".

---

