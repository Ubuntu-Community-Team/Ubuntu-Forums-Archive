---
title: "MT7601U Wireless Adapter issue"
date: 2018-12-21
forum: Networking &amp; Wireless
---

### Post by kzkx4 on 2018-12-21
I am using Lubuntu 18.04 LTS virtual machine.

I have the following USB wireless adapters.

$ lsusb

Bus 001 Device 006: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 005: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter


The first one "RT5370 Wireless Adapter" works perfectly with Lubuntu and there are no issues at all.
But the second one "MT7601U Wireless Adapter" works only 50-50% of the time (if successful, wifi connectivity will have no issues until it is unplugged from the system, after that, if connected the following problem [COLOR=#ff0000]_**MAY**_[/COLOR] occur (not always) :

In some cases, the second one "MT7601U Wireless Adapter" cannot detect any networks nor connect to my router even though lsusb shows that it is detected by the system.

even after I unplug the MT7601U Wireless Adapter from the Lubuntu 18.04 LTS virtual machine, "lsusb" still shows it as "detected by the system".

I tried this also with the latest Lubuntu 18.10 and Ubuntu 18.04 LTS, this issue is also there in both of them. Can you tell me what should I do?

---

