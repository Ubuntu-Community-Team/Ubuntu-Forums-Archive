---
title: "Strange dual NIC problem"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by roots on 2007-07-13
hi there,

i got an abit NF7 mobo with onboard NIC and an additional DLink DGE530TGigabit NIC on PCI.
just did a fresh feisty install.

both NICs are recognized fine.

onboard NIC: eth0, DHCP on 192.168.1.0 subnet
Gbit NIC: eth1, static ip on 192.168.0.0 subnet

while eth0 is running fine (ssh, [www..](www..).), the Gbit NIC doesnt get an IP address despite the fact that (using system->admin->network setting) its configured to a static IP address.
ifconfig lists eth1, but again, with no valid IP address.

if i do 

```

roots@machineone:/$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x00000037 (55)
        Link detected: yes

```

everything looks fine so far.

BUT, if i do 

```
nm-tool
```

i only get the eth0 (onboard) NIC listed!

at the moment i don't see what to look for...is there any config file for nm where i should add eth1?!?


any help very much appreciated!
.roots

---

### Post by roots on 2007-07-13
FIXED...

a reboot was necessary... :-)

---

