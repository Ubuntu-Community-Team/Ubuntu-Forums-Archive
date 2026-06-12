---
title: "[SOLVED] Artheros Ar5008 series Install"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by coninsan on 2008-03-18
Hi 

I must say, due to the explicit help of this forum i am inches away from having a fully functioning linux pc, the only thing missing is my wireless card. 

I am unable to find anything on google about how to install it, so i have come here once again to seek your wisdom of how maybe to install it. 

heres my lspci output on my wireless.
```
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
```

By the way, this is quite important because: 1 my education is primaraly centered around computers, 2 the network at my school is wireless and 3 without wireless you are doomed at my school. :)

---

### Post by coninsan on 2008-03-18
anyone?

---

### Post by coninsan on 2008-03-18
???

---

### Post by Giacecco on 2008-03-18
Look for "AR5418" on the the Madwifi web site at [http://madwifi.org/wiki/Compatibility/D-Link](http://madwifi.org/wiki/Compatibility/D-Link) . It looks like getting it to work will not be easy.

---

### Post by coninsan on 2008-03-18
my card is listed there YAY!

but i do not know how to get the drivers form the page, all that i really can find out about it is: 
[HTML]DWA-556 
Chipset:	AR5418 (802.11/b/g/n)
URL:	http://www.dlink.com/products/?pid=549
Supports:	IEEE 802.11bgn
Interface:	PCI Express
Device Information:	168C:0024
Subsystem ID:	1186:3a70
H/W Version:	A1
F/W Version:	1.00
madwifi version:	Trunk December 7, 2007
OS:	Ubuntu x86_64 7.10
Notes:	Doesn't work out of the box with Ubuntu 7.10
Notes:	Working with network-manager (some issues) with snapshot from madwifi.
Notes:	Low signal disconnection issues? Seeing drops and then restarts. Could be my environment.[/HTML]

and i do not know what to make of it...

---

### Post by coninsan on 2008-03-18
After some scouting i found this via another thread. :)

heres the thread:
[http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY](http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY)


and heres the site that solved my problem: 
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

So this case is SOLVED :-D

---

