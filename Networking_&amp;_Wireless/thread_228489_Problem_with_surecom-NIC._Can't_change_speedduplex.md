---
title: "Problem with surecom-NIC. Can't change speed/duplex"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by eager on 2006-08-03
I have serious problems with my nic ( a surecom EP-320X) on my 6.06-install. No matter what I do I can't seem to change my nic from 10 Mbit halft duplex to e.g 100 full duplex.

I've tried both mii-tool and ethtool but none of them seem to do the job. 

It doesn't work to force it or only advertise the selected speed/duplex. 

this is what mii-tool and ethtool returns no matter if I for exampel entered mii-tool --force=100baseTx-FD eth0 
```
 sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: off
        Current message level: 0x00000000 (0)
        Link detected: no

```

```
sudo mii-tool -v eth0
eth0: 10 Mbit, half duplex, no link
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   10 Mbit, half duplex
  basic status: no link
  capabilities:
  advertising:

```

I don't get it... Any thoughts on this? It works fine in 10 Mbit half duplex, but I want to use this computer as a fileserver (i.e I want 100Mbit/FD). The computer is connected to a switch which can handle 100Mbit/FD (I have other computers on my lan running at 100/FD). Its not a question of inadequate cables either.. they work fine with the other computers if I swap them.

uh](*,)

---

