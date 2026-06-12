---
title: "How to set up an Internet connection?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Terraman on 2009-02-14
Hi all,

I managed to install Ubuntu 8.04 on my elderly laptop (see specs in signature). However, I cannot find out how to set up an Internet connection.

I have a PCMCIA 3Com 3cCFE575BT card. Do I need a driver? If yes, how do I make it run?

Thanks in advance!

---

### Post by Bölvaður on 2009-02-14
did you get "PCMCIA 3Com 3cCFE575BT" from the "lshw" command?

I did a little google search and found this quite quickly

```
	[**pcmcia-cs driver: 3c575_cb**] [x86]
	[2.4+ kernel driver: 3c59x]
	3Com 3c575TX
	3Com Megahertz **3CCFE575BT**, 3CXFE575BT, 3CCFE575CT, 3CXFE575CT
	3Com Megahertz 3C3FE575CT

```

But I think the pcmcia-cs driver is installed by default. Make sure in synaptic that this driver is not installed.

---

### Post by Terraman on 2009-02-15
> **Bölvaður said:**
> did you get "PCMCIA 3Com 3cCFE575BT" from the "lshw" command?

Actually, from the Device Manager.

From the "lshw" command:```
     *-network DISABLED
          description: Ethernet interface
          product: 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone]
          vendor: 3Com Corporation
          physical id: 0
          bus info: pci@0000:05:00.0
          logical name: eth1
          version: 01
          serial: 00:10:4b:7c:9a:16
          size: 10MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=5 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
```

I do not know what, but I apparently have a configuration problem. I have not allready intalled Synaptic in this computer.

---

