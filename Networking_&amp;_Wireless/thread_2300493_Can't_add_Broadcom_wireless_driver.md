---
title: "Can't add Broadcom wireless driver"
date: 2015-10-26
forum: Networking &amp; Wireless
---

### Post by iyarlin on 2015-10-26
I have Lenovo ThinkPad twist. My OS is dual windows 10 - Ubuntu 14.04LTS. I'm fairly new to Linux. 

Recently I had ran Ubuntu from a live USB and had no problem adding my Broadcom device (14e4:4359) via: system settings -> software & updates -> additional drivers. 

After dual installing Ubuntu I can still see the device but when I try to activate it via marking it and clicking apply changes it doesn't work (I.e. A progress bar appears but it stops after a moment).

Thanks!

---

### Post by jeremy31 on 2015-10-26
What is the version that is shown in additional drivers?

---

### Post by iyarlin on 2015-10-26
Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)

Above is written: BCM43228 802.11a/b/g/n

---

### Post by jeremy31 on 2015-10-26
```
dpkg -l | grep bcmwl
```

---

### Post by iyarlin on 2015-10-26
Typing dpkg - l | grep bcmwl
didn't produce any output

---

### Post by Beren Camlost on 2015-10-26
Could you make a wired connection from your router to your laptop and install the driver from the additional drivers tab?

The issue is, *I think*, that while the live USB environment comes with the bcmwl-kernel-source package it doesn't install this by default when you make a persistent install.

---

### Post by iyarlin on 2015-10-26
Also typing lshw gave that the configuration for the device is driver = bcma-pci-bridge latency = 0

---

### Post by iyarlin on 2015-10-26
> **Beren Camlost said:**
> Could you make a wired connection from your router to your laptop and install the driver from the additional drivers tab?

The issue is, *I think*, that while the live USB environment comes with the bcmwl-kernel-source package it doesn't install this by default when you make a persistent install.

I don't have a wired connection at the moment.. I do agree this seems most promising..

---

### Post by jeremy31 on 2015-10-26
Download the driver from [http://packages.ubuntu.com/trusty-updates/bcmwl-kernel-source](http://packages.ubuntu.com/trusty-updates/bcmwl-kernel-source) pick the 32 or 64 bit version depending on your install and select a mirror site to download from.  Copy it to a CD/DVD/USB drive to get it in Ubuntu OS and double click to install

---

### Post by praseodym on 2015-10-26
Hi,

the driver from 14.04 is buggy, install the one from 14.10 instead:

[http://packages.ubuntu.com/utopic/bcmwl-kernel-source](http://packages.ubuntu.com/utopic/bcmwl-kernel-source)

---

