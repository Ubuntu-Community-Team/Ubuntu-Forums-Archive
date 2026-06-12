---
title: "Wireless USB Adapter"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by AaronC on 2006-12-18
I am currently in the process of downloading ubuntu and i was wondering if anyone could give me some early tips on getting my Belkin 54mpbs Wireless USB Network Adapter to work...i currently have a BT home hub as my wireless router.

the driver is rt2500usb.sys on windows if that helps

---

### Post by n00b@linux on 2006-12-18
Check to see if your wireless USB adapter is supported (look for your manufacturer and/or your chipset):
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
If not, then you'll have to use ndiswrapper.  You can download it from the repos and follow this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by AaronC on 2006-12-18
it has a couple on there but i dont know what version mine is...my download is 29% so wont be long i will give it a go soon :)

---

