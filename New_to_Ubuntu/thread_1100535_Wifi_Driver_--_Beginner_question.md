---
title: "Wifi Driver -- Beginner question"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Ceryn1126 on 2009-03-19
Im having trouble setting up the internal wireless cared on my laptop.  From the best I can tell it is a Marvell card based off the topdog line of cards.

this is the result of my lspci

```
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a30] (rev 02)
```

When i was seeing if i could get ndiswrapper to work with the vista driver (not something that works usually I have been told) I did find out the exact chipset for the card.

88W8687 Marvell PCI-Express 802.11bg Wireless

I did some googling and found someone claiming to have a working driver but it was posted in raw code and being a newbie I have no idea how to use it. Here is a link to the mailing list where the driver was located.

[http://osdir.com/ml/linux-wireless/2009-03/msg00369.html](http://osdir.com/ml/linux-wireless/2009-03/msg00369.html)

Can anyone shed some light on this or offer any general info about finding my driver.

Thanks

---

### Post by Hospadar on 2009-03-19
Can you not get the XP driver for this card? even from marvell's website?

just from a quick search it looked like some people at least go this (or something like it) working with ndiswrapper

---

### Post by Ceryn1126 on 2009-03-20
The other topdog chipsets seem to work and have drivers for xp.  Unfortunately this one seems to be something that is only used in  Gateway M-series laptops and the vista driver only has a .sys file for the driver, as a result ndswrapper won't take it.

---

### Post by ivanvajar on 2009-03-20
Can you find WinXP driver for it?

---

### Post by lkraemer on 2009-03-20
Ceryn1126,
I think you will find the information you need from this link.

[http://ubuntuforums.org/showthread.php?t=650637&highlight=MT6840](http://ubuntuforums.org/showthread.php?t=650637&highlight=MT6840)

I got my Gateway MT6840 Wifi working with the Intel Wifi card.

If you have a Gateway, I have a writeup that may be a little more help.

What does the following display in  a terminal window:
```

lshw -C network

```

lkraemer

---

### Post by Ceryn1126 on 2009-03-25
Sorry about the slow reply.  I was out of town.

```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:90:c6:5c:ef:28
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1d:73:4e:5d:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.12 multicast=yes wireless=IEEE 802.11bg

```

ID 3 is most likely a Nintendo Wifi adapter I'm using so that I can connect at work.

---

### Post by Kaivik on 2009-04-08
I have an M series i cant seem to get the wifi working either "network:UNCLAIMED"

---

