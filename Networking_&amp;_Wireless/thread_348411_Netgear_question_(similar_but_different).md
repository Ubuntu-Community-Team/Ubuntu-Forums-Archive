---
title: "Netgear question (similar but different)"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by elvenwood on 2007-01-28
I'm trying to hook a Netgear 311, but Ubuntu doesn't seem to want to load the software that comes with it. I checked compatability and they said no driver needed. I haven't spent enough time in Ubuntu to get it to load by hand.
Anyone? :confused:

---

### Post by Greg2 on 2007-01-28
> **elvenwood said:**
> I'm trying to hook a Netgear 311, but Ubuntu doesn't seem to want to load the software that comes with it. I checked compatability and they said no driver needed. 
What version of  Netgear 311 ?

they all use a driver (module)

Netgear WG311v2 = ACX 111
Netgear WG311T = AR5212

and what version of Ubuntu are you using?

---

### Post by elvenwood on 2007-01-28
WG311v3

But I'm completely clueless as to the version on Ubuntu; the tower was a gift with partitioned hard drives.

---

### Post by Greg2 on 2007-01-29
> **elvenwood said:**
> WG311v3

But I'm completely clueless as to the version on Ubuntu; the tower was a gift with partitioned hard drives.
OK, to be sure in terminal do:
```
lspci | grep Wireless
```if your output reads something like:
Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
you can download this driver with```
wget ftp://downloads.netgear.com/files/wg311v3_1_0.zip
```unzip the WG311v3.INF and WG311v3XP.sys to a new folder, then please follow these instruction (using the drivers you just unziped):
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Please note that they are not specific instuctions for your card!
Here is some more info (not for your card, but your chipset) to help you with this:
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29)

For your Linux version do:```
cat /proc/version
```
I do not have this card to give you specific instruction... or I would do so. :roll:

---

