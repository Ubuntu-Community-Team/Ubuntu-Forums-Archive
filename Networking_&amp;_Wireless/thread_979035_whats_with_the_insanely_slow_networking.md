---
title: "whats with the insanely slow networking?"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by b0b138 on 2008-11-11
Internet is fine, LAN is slower than dirt. I might get 1Mb transfer rate.

---

### Post by pdwerryhouse on 2008-11-11
Duplex issues? Use ethtool to make sure you're not running half-duplex. For example, mine says:

```
# ethtool eth0
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
        Wake-on: g
        Current message level: 0x00000037 (55)
        Link detected: yes

```

---

### Post by b0b138 on 2008-11-12
it says no data available

---

### Post by b0b138 on 2008-11-15
Thanks very much, you got me looking at hardware issues rather than ubuntu issues. Looks like an old 3com card wasn't working right, or isn't supported well anymore.

---

### Post by Iowan on 2008-11-15
Another thread mentioned ipv6 as a culprit - but that was wireless.

---

