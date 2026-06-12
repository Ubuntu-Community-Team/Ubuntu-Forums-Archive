---
title: "Enable Orinoco Silver Card on Dell Insipiron 3700"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by lalarrea on 2007-05-01
Hello,

I just installed Xubuntu on an old Dell Inspiron 3700 (Celeron 450Mz, 128 MB RAM, 12GB HD). I am doing it mainly to play around with Linux.  Installation was ok, and everything works fine.  However, i am trying to setup my wired and wireless network cards and i have not been able to do it.

I checked the wiki and ran some tests and the card is recognized. When i run lshw command i get the following:
-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: eth2
serial: 00:02:2d:3c:74:5a
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinono driverversion=0.15 firmware=Lucent/Agere 7.28
multicast=yes wireless=IEEE 802.11b

-network: 1 DISABLED
description: Ethernet interface
physical id: 2
logical name: eth0
serial: 00:e0:98:72:a6:e7
capabilities: ethernet physical
configuration: broadcast=yes dirver=pcnet_cs multicast=yes

I am trying to connect using Internet sharing via wireless on a iMac.  If that is not possible, at least I want to try connecting directly to my cable modem using the wired card.

I am no linux expert, so please give me detail steps.

Thanks,

LA

---

### Post by lalarrea on 2007-05-04
Any ideas anyone?

---

