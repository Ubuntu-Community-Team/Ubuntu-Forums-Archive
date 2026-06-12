---
title: "WiFi card is ridiculously slow in 8.04 beta"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by NCLI on 2008-03-28
I realize that 8.04 is by no means finished, but if I don't point this out now, odds are it will never be fixed.

Anyway, this is my WiFi card:
> 05:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
Subsystem: Micro-Star International Co., Ltd. Unknown 802.11g mini-PCI Adapter
Flags: bus master, slow devsel, latency 64, IRQ 20
Memory at fdefa000 (32-bit, non-prefetchable) [size=8K]
Capabilities: [40] Power Management version 2 

My connection status swings wildly, going from 100% to 15 while sitting right beside the router, but slow no matter what. It worked fine in 7.10.

---

### Post by Marsan on 2008-04-25
Same stuff here. Se bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/190515)

---

