---
title: "Rediculously slow wired ethernet"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by mks74 on 2008-03-04
I have a fresh install of 7.10 AMD64 on an Asus nForce4 based AMD system.

Using the on-board ethernet, forcing 100/Full using ethtool, I get at best 12 KB/s download speed from my selected mirror. Rebooting to XP I get upwards of 1.5MB/s downloading the same file from the same mirror.

dmesg says:
forcedeth: using HIGHDMA
eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0

lspci says:
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)

ethtool says:
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 9
        Transceiver: external
        Auto-negotiation: off
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

I don't even know where to start. Any suggestions?
TIA

---

### Post by chili555 on 2008-03-05
I am suspicious that this is the problem:```
Auto-negotiation: off
```Generally, if a network card can't negotiate a rate with the device at the other end, your router or switch, perhaps, it will default to a very low rate. Please try:```
sudo ethtool -s eth0 autoneg on 
```Then do:```
sudo ethtool eth0
```See if autonegotiation is now on. Then try a big download and let us know the result. Thanks.

---

### Post by mks74 on 2008-03-07
Autoneg is not the problem. The reason it's off is that I turned it off since just booting he system gives me:

[quote=mks74's system]
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 9
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
[/quote]

which is an incorrect setting since the switch port is set to 100 Mbps full duplex, no negotiation.

My network setting in windows is 100/Full fixed, no negoation. I tried a gentoo livecd which gave me comparable results to ubuntu, I think forcedeth vs. my hardware is the issue here.

---

