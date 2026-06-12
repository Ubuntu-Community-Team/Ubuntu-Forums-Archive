---
title: "Network Operating in Half-Duplex"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by ill0gical0ne on 2006-11-11
I recently upgraded my server to Ubuntu 6.10, and as soon as I did, my network transfer speed dramatically dropped; as if it were operating with 10baseT.  I've looked around everywhere for solutions, but none that I've tried so far have worked.

```
$ mii-tool -v
eth0: negotiated **100baseTx-FD**, link ok
  product info: vendor 00:00:20, model 32 rev 1
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
```

```
$ ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: **100Mb/s**
        Duplex: **Full**
        Port: MII
        PHYAD: 31
        Transceiver: internal
        Auto-negotiation: **on**
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: yes
```

I have DD-WRT setup on my router, and auto-negotiation is enabled.  Average network speeds 1800 KB/s (very slow).

---

### Post by netztier on 2006-11-14
> **ill0gical0ne said:**
> I have DD-WRT setup on my router, and auto-negotiation is enabled.  Average network speeds 1800 KB/s (very slow).

The result of autonegotiation is expected, the transfer rate however isn't. 

How did you measure this throughput? It's from switchport to switchport, isn't it? If one of the systems involved is connected via WLAN, i't's not even that bad, even for 54Mbps 802.11g.

Have you tried [COLOR="Black"]iperf[/COLOR] from the universe repositories? It's a convenient tool to measure raw tcp and udp throughput and is available also for windows, which comes in very handy in a heterogenous network (been there done that, twice a day...).

regards

Marc

---

