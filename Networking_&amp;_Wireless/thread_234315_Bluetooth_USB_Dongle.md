---
title: "Bluetooth USB Dongle"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by pichalsi on 2006-08-11
Hi

I just installed Ubuntu and i have to admit i didnt think everything will work so well as it does, particularly hardware-wise. My only problem is that i cant get my unbranded USB dongle to work, i put it into USB port, the LED flashes but hcitool doesnt see any devices and lsusb only prints : 

```
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 004: ID 0675:0200 Draytech
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 004: ID 0c10:0000 - thats the dongle
Bus 002 Device 001: ID 0000:0000
```

do i need some drivers or it wont ever work? or is it only my fault? thanks in advance for help

---

### Post by wieman01 on 2006-08-11
Some USB dongle of unkown brands are not recognized by Linux. This really depends on the chipset their are using. Check out this list, perhaps yours is listed as well.

[http://www.holtmann.org/linux/bluetooth/features.html]("http://www.holtmann.org/linux/bluetooth/features.html")

I am afraid yours will have a problem... I've experience a similar issue before with an unknown (Taiwanese) brand. So I usually recommend "Billionton".

---

