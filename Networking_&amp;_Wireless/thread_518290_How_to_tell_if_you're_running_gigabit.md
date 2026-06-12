---
title: "How to tell if you're running gigabit?"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by pylorns on 2007-08-05
I've been searching  to find the answers, I have a Vista box and an ubuntu box, and a gigabit switch - my ubuntu box has a abit motherboard with a gigabit card in it but it doenst look like i'm getting gigabit or even 100mb.  How can I tell the speed that Ubuntu thinks the card is at?

---

### Post by digen on 2007-08-05
What is the output of ethtool ?

$ sudo ethtool eth0

change the eth0 with your network interface name.

---

### Post by pylorns on 2007-08-05
Speed 100MB/s Full - says it supports 1000  how can I set it to 1000?

Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
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

---

