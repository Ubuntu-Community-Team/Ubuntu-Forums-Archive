---
title: "Dirty How to Monitor Mode (atheros chip)"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by VaDor on 2008-08-26
Hi,

I had some problems putting my atheros card in monitor mode so here is my quick guide line that solve problems such as:
> 
airmon-ng stop ath0
....
airmon-ng start wifi0
Interface	Chipset		Driver

wifi0		Atheros		madwifi-ngath0: ERROR while getting interface flags: No such device

ath1		Atheros		madwifi-ng VAP (parent: wifi0)


Then the card (using ath1) doesn't work in monitor or manage mode and some how the system creates the ath1 and not the ath0.

So for people that have atheros at least pci versions like me this worked well:
-- Install via apt-get madwifi-tools
-- Followed this guide [https://help.ubuntu.com/community/Madwifi-ng_on_Macbook_Pro](https://help.ubuntu.com/community/Madwifi-ng_on_Macbook_Pro) (ignore that this is for macbook, just focus this is for atheros chips)

Attention: The guide uses old revisions for example, they say "wget http://patches.aircrack-ng.org/madwifi-ng-r3386v3.patch" but if you go to the same you will find that the last revision at this time is "madwifi-ng-r3745.patch" same thing for madwifi repository trunk.


Regards,
Vador:popcorn:

---

