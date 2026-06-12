---
title: "Marvell Gigabit Ethernet Controller can't go faster than 100MB/s"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by PatrickKik on 2007-12-20
I have an onboard Marvell Technology Group Ltd. 88E8052 PCI-E ASF Gigabit Ethernet Controller (rev 20) which doesn't go faster than 100MB/s. There is a gigabit switch on the other and of the CAT6 cable so there shouldn't be a bottleneck.

patrick@hajo:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
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
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes[/INDENT]

Anyone any ideas? Thank you!

---

