---
title: "Need help with HP dv6915nr + Ibex"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by rwalker999 on 2008-11-29
I've been with Ibex for a while, and since I got it, the wireless has been spotty at best.  It would work initially, then go out, forcing me to reconnect.  I'd have to do so about 20x/day.
Anyways, after the most recent system update, my laptop won't even recognize that there is an active wireless card.

I'm running an HP i686, Atheros 802.11, and 8.10 last updated sometime yesterday.  My device manager is set on "Support for 5xxx series of Atheros 802.11..."  I've set it on that and rebooted, and set it on "Support for Atheros 802.11..." and rebooted, neither made a difference. 

If anyone can help me get my wireless going, I'd greatly appreciate it.  Need my laptop and wireless working for my law school exams in 1.5 weeks.  

If I need to attach any terminal outputs, just let me know and I'll do so with the quickness.

Thanks so much (for this help and past help I've found here...)  Any help may be rewarded in the future with some free legal services ;)

---

### Post by night_fox on 2008-11-29
```
lshw -C network
```

---

### Post by rwalker999 on 2008-11-29
> **night_fox said:**
> ```
lshw -C network
```

WARNING: you should run this program as super-user.
  *-network              
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:7f:07:00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.9 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:71:c3:7d:f0:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

