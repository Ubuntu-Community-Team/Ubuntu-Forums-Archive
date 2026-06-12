---
title: "ATH0 start on boot"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by monkeywork on 2006-12-28
Hi All,

i have a problem where ATH0 refuses to connect to my wireless network on boot, regardless if I have the information coming in static or dhcp.   In order to get access to the network once I'm booted up I need to:

ifdown ath0
ifup ath0

Anyone have this problem before or have any advice on getting this resolved?

---

### Post by syracus on 2006-12-30
Hi all,

noone since july 2005 ?!?...damn, i ran into the same problem with my pci netgear wlan adapter since switching from debian etch to ubuntu edgy :(

Can't find any solution to this problem besides executing a proprietary script S99forceath0 which simply calls 'ifdown ath0; ifup ath0;'.

But hey....this can't be really a solution, right ? So please, can someone help us ?

---

