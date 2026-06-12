---
title: "Help with ethtool issues NIC"
date: 2021-02-28
forum: Networking &amp; Wireless
---

### Post by arc- on 2021-02-28
[SIZE=3]I was trying to edit/change the speed from 100MB to 1000MB. However, I messed up something and ended up with (Speed unknown, Duplex unknown) also, I lost my internet connection, when the speed was set 1000MB. So I finally found this ( sudo ethtool -s eth0 advertise 0x008 ) and I got the internet back, but still lost the (Advertised link modes set as previous) how do I get them back? I want the (Advertise link modes) to match (Supported link modes) as previously. 
 
 Please help me to understand what went wrong? and how to get the correct Advertise link modes!
 
 Thank you.
 [CENTER][B]
 See below for examples:[/B]
 [/CENTER]

 _This is what I had before I messed this up._
 Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Supported pause frame use: No
     Supports auto-negotiation: Yes
     Advertised link modes:  10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Speed: 100Mb/s
     Duplex: Full
     Port: Twisted Pair
     PHYAD: 2
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: off (auto)
     Supports Wake-on: pumbg
     Wake-on: g
     Current message level: 0x00000007 (7)
                    drv probe link
     Link detected: yes
 
 _Then I ended up with this:_
 Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Supported pause frame use: No
     Supports auto-negotiation: Yes
     Advertised link modes:  1000baseT/Full 
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Speed: Unknown!
     Duplex: Unknown! (255)
     Port: Twisted Pair
     PHYAD: 1
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: Unknown (auto)
     Supports Wake-on: pumbg
     Wake-on: g
     Current message level: 0x00000007 (7)
                    drv probe link
     Link detected: no
 
 _I tried to fix it and ended up with this:_
 Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Supported pause frame use: No
     Supports auto-negotiation: Yes
     Advertised link modes:  1000baseT/Full 
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Speed: Unknown!
     Duplex: Unknown! (255)
     Port: Twisted Pair
     PHYAD: 1
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: Unknown (auto)
 Cannot get wake-on-lan settings: Operation not permitted
     Current message level: 0x00000007 (7)
                    drv probe link
     Link detected: no
 [CENTER]
 Then I got the internet to work with this: (sudo ethtool ... 0x008)
 [/CENTER]
_I ended up with this:_
 Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Supported pause frame use: No
     Supports auto-negotiation: Yes
     Advertised link modes:  100baseT/Full 
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Speed: 100Mb/s
     Duplex: Full
     Port: Twisted Pair
     PHYAD: 2
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: off (auto)
 Cannot get wake-on-lan settings: Operation not permitted
     Current message level: 0x00000007 (7)
                    drv probe link
     Link detected: yes
 
 [/SIZE]

---

