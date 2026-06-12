---
title: "WNA3100 internet only works for a few minutes"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by chillbot on 2015-10-03
First I downloaded ndiswrapper: 

udo apt-get install ndiswrapper-common ndiswrapper-dkms ndiswrapper-utils-1.9


Then I downloaded driver files
cd~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo ndiswrapper -i bcmn43xx64.infsudo 
ndiswrapper -masudo 
modprobe ndiswrapper

I can connect to a wireless network but it only works for a few minutes.  After a few minutes it stops.

---

### Post by chillbot on 2015-10-03
I seemed to have fixed it.  I apparently needed to plug it out and plug it back in again.

---

