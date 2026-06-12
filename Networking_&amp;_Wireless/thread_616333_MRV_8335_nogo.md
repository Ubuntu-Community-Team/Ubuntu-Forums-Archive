---
title: "MRV 8335 nogo"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by WernerBrandt on 2007-11-18
I got a WLAN PCI card with a Marvell 8335 chipset.

Problem is, I cannot get it working...

LSPCI:
> lspci | grep 8335
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


Ndiswrapper:
> ndiswrapper -l
8335mod : driver installed
        device (11AB:1FAA) present


I dont have any wlan0 or eth1, dont see any wireless devices, either using WCID or 
Gnome network-manager

Further setup:
USB RT2500 USB -> works with serial monkey drivers

I tried already  (-> no success)
[LIST]

* disable eth0 
* No USB wlan device installed
* Marvell PCI card setup hard coded on IRQ 9 (and tried others)
* Using standard drivers
* Disabled standard drivers
* Using several different drivers for mrv 8335, including the ones with came with my card, but the latter failed, because of missing some files?? 
Only Mrv8000c.cat, Mrv8000c.inf and Mrv8000c.sys are provided (Win2K, WinXP, could not use any Win 9x, because those even has less)
* WCID for configuring
* Gnome network-manager for configuring

[/LIST]

Am I missing something, or doing anything wrong?
(Or maybe card failure? used to work on an M$ box tho...)

---

### Post by genti on 2007-11-21
What kernel are you running? Maybe a 64bit?

---

### Post by FoxOne on 2008-04-29
had the same issue, probably the same card (WG311v3 from Netgear) I used the 98 drivers and had no issue with Ubuntu 7.04-7.10, Slackware, SUSE, xBSD. Can't get it to work with OS X.... good luck

---

