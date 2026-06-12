---
title: "Have 2 Wireless Cards, Use?"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by greybeard62 on 2006-11-25
Absolutely new to Ubuntu 6.10, installed yesterday.  Second Linux tried, this one different.  Only OS on Toshiba Laptop, blew away everything and gave Edgy the whole hard disk.  Now, no wireless, was hoping not to fight this like on other Linux but....
I have two PCMCIA wireless cards, both known to work. Netgear WG511-v2 and Linksys WPC54GS-v2.  Can't seem to make either work..
Install seemed to go with noprobs, everything seems to work except wireless.  Read a bunch o posts and searched here so I have looked.  Does Edgy work with either of these cards?  How?  Why compile ndiswrapper, it was up in other Linux..had to ndiswrapper and play with other, every time reboot issued modprobe and dhcpcd.  Was hoping to get a Linux that just booted up or at least can be implemented that way with some mods..
Router is linksys wireless-G, no security, wide open, other two laptops connecting fine runnning XP

---

### Post by spd106 on 2006-11-25
Have a look here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

When it comes to ndiswrapper first try the ndiswrapper-utils package, then compile for source it that doesn't work.

---

