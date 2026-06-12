---
title: "Asus A8v Deluxe - Wake On Lan doesn't work"
date: 2015-01-31
forum: Networking &amp; Wireless
---

### Post by dimitris6 on 2015-01-31
Hello everybody!
I am posting this thread just because i need your help...
I am trying to set up a linux server ( Ubuntu server 14.04) in order to use It as NAS.
Due to the limited budget I decided to use an old mobo Asus A8v Deluxe.
I installed Ubuntu but i can't find a way to use the Wake On Lan capability.
I've read a lot of threads and i  have enabled this capability with a script which runs at every boot  "[COLOR=#000000][FONT=Ubuntu Mono]ethtool -s eth0 wol g[/FONT][/COLOR]".

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x00000037 (55)
                               drv probe link ifdown ifup
        Link detected: yes



However from what i can understand there is a firmware/driver error that disables this capability at Linux....Am I correct??;)
Has anyone found a solution to this?

I checked at Marvells support area and there is only drivers for kernel 2.6..

Thank you for your time!!

---

