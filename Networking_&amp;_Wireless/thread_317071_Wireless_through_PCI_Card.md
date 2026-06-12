---
title: "Wireless through PCI Card"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by Shmifty on 2006-12-11
I'm putting Kubuntu on my friend's new computer and he bought a wireless PCI card for it (I'm not sure of the model number or driver so if anyone knows the command to give me that it would be appreciated). I have ndiswrapper and knetworkmanager in hopes of correcting the situation, but nothing works. I've search a few threads here to no avail and for some reason the wireless card just won't enable under the networking system settings.

Anyone have a possible solution for me to try?

---

### Post by FrodoB on 2006-12-11
You need to provide the output of:

lspci

that will help to identify what driver is needed.

---

### Post by Shmifty on 2006-12-11
**04:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

I've found the driver for the card but I can't get ndiswrapper to install it correctly.

---

### Post by FrodoB on 2006-12-12
This is a device that causes problems at first for a lot of people.  I can recommend two things:

1) Go to the ndiswrapper compatibility list and check for bcm4318 and get the drivers that the post recommends:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Do not worry that the driver comes from a source other than your equipment manufacturer.

2) Search this forum for bc4318 and find a post were they get the device working using ndiswrapper:

[http://ubuntuforums.org/search.php?searchid=11065505](http://ubuntuforums.org/search.php?searchid=11065505)

One  of those posts recommends this driver for instance:

[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

I do not have this device so I cannot comment, but I believe that I have read on another forum that that the Acer driver was good for someone else as well. Though at the time I am writing this that link seems to be down.

---

