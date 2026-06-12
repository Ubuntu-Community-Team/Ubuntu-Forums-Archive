---
title: "Wireless Dongle Not Working"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by tomazi2 on 2014-09-17
Hi all

I have installed ubuntu 14.04 LTS, inserted wireless dongle (netgear wna1100) but I cannot use wireless on my ubuntu. I looked at the netgear website i found the device but they do not have drivers for Linux distributions .

I am new to Linux so don't quiet understand how i can get it working so i can receive wireless.

---

### Post by tgalati4 on 2014-09-17
First, you will need a working, wired, ethernet connection.  Make sure you have applied all of the updates--there will be several hundred megabytes worth.  You may need to reboot once or twice to get everything updated.  Once that is done, open a terminal and post the output of these two commands:

```
lspci
ifconfig
```

Welcome to the forums.

---

### Post by tomazi2 on 2014-09-17
HI thank you for your replay.

I did update and upgrade everything, The lspci produces a massive list....? anything in particular to look at within this list...?

---

### Post by tgalati4 on 2014-09-17
Something networky:

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by praseodym on 2014-09-17
Please run the wireles_script as described here

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

and upload the file.

---

