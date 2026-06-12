---
title: "ZD1211 USB Adapter not working properly"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by guedesav on 2008-10-23
So, I'm trying to activate a ZD1211 based USB adapter on my PC. I followed the instructions on the ZD1211 Sourceforge page, and also on this page( [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)) ), and it compiled alright, but the problem is with the old zd1211rw module.

To put it simply, check these outputs:

> sudo lsusb
Bus 005 Device 004: ID 0ace:1215 ZyDAS 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
> sudo usbmodules --device /proc/bus/usb/005/004
zd1211rw

But the zd1211rw is on the blacklist, so obviously it isn't modprobed. Thus, it don't work(the wlan0 interface isn't created). What I really want to know is how to make Ubuntu recognize my USB adapter as zd1211 instead of 1211rw, or even if it is possible.

Thanks in advance, and I'll be waiting for answers.

---

### Post by guedesav on 2008-10-23
Um... so, it seems I just had to install zd1211b instead all along, so I'm very sorry for bothering you.

---

### Post by fuzzyworbles on 2008-12-17
i would like to know how you compiled it. i followed that link, but it's broken.

do you think it makes a difference that i'm using an amd64 kernel?

---

