---
title: "Gutsy 7.10 and Netgear GA311 Help!"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by Vasator on 2007-12-17
Okay here is the issue. I have scoured the boards, I am still  a newbie with Ubuntu but I want to stick with it because anything is better than Windows. I have a multi-nic system.

>  lspci | grep -i ethernet
00:02.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 05)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


The Gigabit is what I am having an issue with. It is a Realtek GA311 as shown above. It will not go to a gigabit link speed as shown:

> sudo ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

I have tried this: sudo ethtool -s eth2 speed 1000 duplex full autoneg on
and this: sudo ethtool -s eth2 speed 1000 duplex full autoneg off

but to no avail. It goes from 10mb half to 100mb full/half. I am still learning Linux and I like it so much better than Windows and if I could get some help I would really really appreciate it. Please don't let me go back to the dark side.

I have the the Network connected to a Netgear FVS124G 4-port Gigabit Router and I have no trouble at all on the otehr systems on the network. A FreeNAS Server, Custom built system with a realtek chipset onboard gigabit, and this system (the one with the issue) an IBM Intellistation which is a few years old. hint: the freenas server is older than this machine (it isn't the PCI Bus).

If you neeed any more info please let me know... Thank You

---

