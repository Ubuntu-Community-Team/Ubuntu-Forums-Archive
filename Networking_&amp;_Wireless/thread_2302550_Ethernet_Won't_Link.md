---
title: "Ethernet Won't Link"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by jacob9 on 2015-11-11
Hello!
  So I installed Ubuntu Server 12.04 on my laptop and I noticed I can't use my ethernet cable, I tried to install the sk98lin but it doesn't support my kernel since it's 3.16. I've spent around 7 hours on this and I still have no clue what I'm doing. I've tried 4 different cables and all the slots on my router, no dice. It works on my ethernet to USB adapter but that's very VERY slow for me.
```
lshw -c network
```
```
  *-network
       description: Ethernet interface
       product: 88E8042 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth0
       version: 10
       serial: 00:25:b3:4e:71:e5
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:e0000000-e0003fff ioport:2000(size=256)


```
```
ethtool eth0
```
```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: Unknown!
        Duplex: Unknown! (255)
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: no


```

---

