---
title: "Driver for unknown wireless card?"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by lisard on 2008-10-26
How can I locate the driver for my wireless card?  I assume that to find this, I'll need to know what my wireless card is...how would I find that information?  I have a Compaq Presario C700.

All that I know about the wireless card is this from the product specs online:
Integrated Wireless G 802.11b/g LAN Card

Thanks,
Lisard

---

### Post by issih on 2008-10-26
Open a terminal (from the accessories menu) and enter:
```
sudo lshw -C network
```

then post the output here (note that you can copy text from the terminal using the mouse, or using ctrl+shift+c)

That will hopefully let us identify your wireless card's chipset. Without that information no one can tell you what to do really, unless they happen to have the exact model of laptop you do :)

---

### Post by lisard on 2008-10-26
Thanks. :D

This is what I got:

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f8:72:d4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.104.49.115 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s



It appears to only be answering about the ethernet...

---

### Post by Kevbert on 2008-10-26
Please take a look at these two links. If the [[COLOR="Red"]first one[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=743299") doesn't work try the [[COLOR="Red"]second[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=792158") (Atheros wireless can be a bit of a problem with Ubuntu).

---

### Post by lisard on 2008-10-26
Thank you. :)

The first one didn't solve the issues...and the second one looked "scary" (it looked like if I made a wrong move, I could ruin a lot of things).  But...I spoke this evening with my friend who got me into Linux to start with, and he helped me fix my problems, so I'm set for now.

Thanks for all your help, though, folks. :)

---

