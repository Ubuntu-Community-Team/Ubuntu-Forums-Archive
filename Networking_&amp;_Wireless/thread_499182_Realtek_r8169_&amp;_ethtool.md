---
title: "Realtek r8169 &amp; ethtool"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by wj313 on 2007-07-12
Hi forum,

 network settings with "ethtool" doesn't seem to affect the "r8169" kernel module.

 Plattform testet: Dapper, Gutsy (Tribe2)
 Kernel versions testet: 2.6.17-10, (and the one from Gutsy)
 ethtool versions testet: 3, 5
 r8169 driver versions testet: 2.2LK, 6.001.00 (compiled from the realtek homepage)

 We've tried almost all combinations of above versions/plattforms.

 Is there any workaround to set the speed/duplex/autoneg settings of the r8169 driver?

 (mii-tool and parameters specified at the "insmod" command line of the r8169 driver doesn't work either..)

 A bug within launchpad is filed:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/125537](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/125537)

```
root@ubuntu:~# ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes: 10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes: 10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
root@ubuntu:~# ethtool -s eth2 autoneg off
root@ubuntu:~# ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes: 10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes: 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
root@ubuntu:~# ethtool -s eth2 speed 10
root@ubuntu:~# ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes: 10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes: 10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
  Current message level: 0x00000033 (51)
        Link detected: no
root@ubuntu:~#
```

---

### Post by wj313 on 2007-07-16
Just for the record,

 It's strange, but it does work if the parameter "autoneg off" is appendend to _every_ ethtool command. 

 So, "ethtool -s eth0 speed 100 duplex full autoneg off" does work,
 "ethtool -s eth0 speed 100" not.

---

