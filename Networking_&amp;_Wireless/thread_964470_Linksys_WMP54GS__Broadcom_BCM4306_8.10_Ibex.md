---
title: "Linksys WMP54GS / Broadcom BCM4306 8.10 Ibex"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by duke523 on 2008-10-30
Well, I am having problems with my wireless WMP54GS card.  I tried following the info at [http://ubuntuforums.org/showthread.php?t=370736]("http://ubuntuforums.org/showthread.php?t=370736").
No luck.
My router has WEP-128bit.

---

### Post by Ayuthia on 2008-10-30
> **duke523 said:**
> Well, I am having problems with my wireless WMP54GS card.  I tried following the info at [http://ubuntuforums.org/showthread.php?t=370736]("http://ubuntuforums.org/showthread.php?t=370736").
No luck.
My router has WEP-128bit.
Try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```
If it returns a list of wireless sites you should be able to connect.  It also means that you will need to blacklist the b43 and ssb modules.

---

### Post by unknown03 on 2008-11-04
No luck for me as well

---

### Post by duke523 on 2008-12-12
When use Ethernet to and run Update Manager, The B43 Driver will show up under Hardware Drivers and it works after that.

---

