---
title: "Install Asus USB-AC51 on HP Proliant Microserver"
date: 2016-09-05
forum: Networking &amp; Wireless
---

### Post by thomas.om.nilsson on 2016-09-05
Hey, 
total Linux noob! Just installed xubuntu Xenial Xerus 16.04 on my old HP Porliant Microserver; thought it would be a good idea to shove it in my closet and use it for storage/mediaserver etc. But I don't won't to have the ethernet cable running through my entire apartment, so I bought a Asus USB AC51 wireless USB-adapter at my local store; thinking that I would solve the driver installation through googling.. But after several hours of trying I am about to give up, so I thought maybe someone here could help me out. Tried basically all existing threads on this, but as I have no real knowledge on Linux, I have had a real pain trying to figure out where in the installation process I am doing my mistake or what I am missing on my system to finish my driver installation.

Hope that someone can find the time to help me out.

---

### Post by praseodym on 2016-09-05
Can you please show the output of this command:
```

lsusb
```
Does LAN work (temporarily)?

---

### Post by thomas.om.nilsson on 2016-09-06
Response 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:17d1 ASUSTek Computer, Inc. AC51 802.11a/b/g/n/ac Wireless Adapter [Mediatek MT7610/Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 002: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Yes, I have LAN cable connected and working currently.

---

### Post by praseodym on 2016-09-06
Check the installation manual here:

[https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u](https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u)

---

### Post by thomas.om.nilsson on 2016-09-06
Perfect, thank you!!! That fixed everything!

---

