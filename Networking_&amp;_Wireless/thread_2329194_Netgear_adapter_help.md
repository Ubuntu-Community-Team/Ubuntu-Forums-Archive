---
title: "Netgear adapter help"
date: 2016-06-28
forum: Networking &amp; Wireless
---

### Post by Snazzler on 2016-06-28
I'm a TOTAL noob when it comes to everything, so I need to know how I can get my netgear WNDA3100v3 adapter up and running on Ubuntu. I need a very very detailed, noob friendly, step by step process on what the heck I need to do. Thank you so much in advance!

---

### Post by wildmanne39 on 2016-06-29
Hi, this is the worst usb device to get working, even if you can it usually performs poorly here is a link if you want to try to make it work.
[http://ubuntuforums.org/showthread.php?t=2321779&highlight=WNDA3100v3](http://ubuntuforums.org/showthread.php?t=2321779&highlight=WNDA3100v3)
I would do research and buy a cheap usb adapter.

---

### Post by wildmanne39 on 2016-06-29
*Thread moved to **Networking & Wireless**.*

---

### Post by Geoffrey_Arndt on 2016-06-29
Panda provides excellent wifi adapters that work on Ubuntu based systems without needing driver install/compiling.    My friends & I have several of these working on various equipment.    Cost on Amazon for the ultra 150 nano dongle is $10 usd.
[URL="http://www.pandawireless.com/"]
http://www.pandawireless.com/[/URL]

---

### Post by praseodym on 2016-06-29
Lets try:
```

sudo apt-get install git build-essential dkms linux-headers-generic linux-headers-$(uname -r)
git clone https://github.com/jurobystricky/Netgear-A6210
cd Netgear-A6210
make
sudo make install
```
Reboot and show
```
modinfo mt7662u_sta
lsusb
lsmod
iwlist chan
iwconfig
sudo iwlist scan
```

---

