---
title: "Ubuntu n00b with a slow network connection..."
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by sweetL on 2008-03-17
Right... internet browsing is actually fine, and some transfers seem ok, but other services seem REALLY bad. (i did try the ipv6 thing, but made no difference)

Im using navicat to manage mysql, over a local network connection... but its REALLY slow!

Samba seems ok, 350meg took about a minute or so.

Any suggestions?

Thought this info *might* be helpful:

**Output from ethtools eth0:**
```
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes
```

and heres the lshw output
```
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 21
                serial: 00:19:b9:f9:ec:60
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5721-v3.65 ip=192.168.1.121 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by sweetL on 2008-03-25
no ideas?

---

