---
title: "impossible to use wifi"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by pietshah on 2008-03-19
Hi Ubuntu community!

I'm using Ubuntu for some months already and had not cared yet that the wifi didn't work since I needn't it, but now I do.
I saw lots of posts here about wifi problems, but I'm too newbie to understand them...
My first problem is that I don't know what are the specificities of my wifi card.

I'm using a Acer Travelmate 2300. (Ubuntu 7.10)
I know that it has an integrated wifi card, but it doesn't look detected by Ubuntu since it doesn't appear in networks nor in material, and the leds/buttons for wifi on/off are unactive.

How could I install the drivers for my wifi card and use it?

Thanks a lot for your help.

Pierre

PS: as a result of sudo lshw -C network I have
```
 *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:58:60:d1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=201.208.0.128 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Linksys, A Division of Cisco Systems
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=32

```

---

