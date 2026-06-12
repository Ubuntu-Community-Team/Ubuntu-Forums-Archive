---
title: "hp dv8000 no wireless...."
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by dlo2k6 on 2008-07-13
just installed ubunut 8.04 and at first things seem to be working perfectly and i love it. Only problem is that i cant get my wireless to work... I am currently using a wired connection and of course it works just fine. I went to the device manager and their were question marks next to my wireless card. This is the card i have :

BCM4318 [AirForce One 54g] 802.1BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller1g Wireless LAN Controller ubuntu

I have tried using the network manager at the top of the toolbar but it doesnt detect any wireless networks in the area. This is really confusing any help would be greatly appreciated. i search about the desktop manager online and from what i read it is supposed to constantly be looking for the best wireless in my area but it doesnt seem to do that. I also have a button on the laptop a wlan button it wont turn on like it always used to be with windows that may also be the problem. Anyone who knows anything about this and can help it would be great.

---

### Post by adldesigner on 2008-07-14
Open up a terminal (Applications > Accessories > Terminal) and try the following commands:

(Lists all your PCI devices)
```
lspci
```
(Lists all your USB devices)
```
lsusb
```
(Lists your hardware and extracts Network entries)
```
sudo lshw -C -network
```
(Lists any wireless network available in your area)
```
iwlist scan
```

Post the output of each one of those commands enclosed by CODE tags (for better code readability).
This should help us start to diagnose your issue.

---

