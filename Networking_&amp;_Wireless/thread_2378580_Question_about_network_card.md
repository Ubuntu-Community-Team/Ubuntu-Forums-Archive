---
title: "Question about network card"
date: 2017-11-24
forum: Networking &amp; Wireless
---

### Post by dam034 on 2017-11-24
Dear users,

when I read the speed of a network card (10, 100, 1000 mbps) I have a thought I can't understand.

Since I know in a ethernet cable there are 4 wires to transmit and 4 to receive (in gigabit ethernet), the speed (e.g. 1gbps) refers to the total speed (up + down) or is 1gbps up + 1gbps down simultaneously?


Thanks

---

### Post by Yellow Pasque on 2017-11-24
> When a twisted pair or fiber link segment is used and neither end is connected to a repeater, full-duplex Ethernet becomes possible over that segment. In full-duplex mode, both devices can transmit and receive to and from each other at the same time, and there is no collision domain. This doubles the aggregate bandwidth of the link and is sometimes advertised as double the link speed (for example, 200 Mbit/s)

[https://en.wikipedia.org/wiki/Ethernet#Bridging_and_switching](https://en.wikipedia.org/wiki/Ethernet#Bridging_and_switching)

---

### Post by dam034 on 2017-11-25
So, how can I know if the ethernet connection from my PC to the switch is half-duplex or full-duplex?


Thanks

---

### Post by Yellow Pasque on 2017-11-25
Try:
```
sudo ethtool <name of your network interface>
```

---

### Post by dam034 on 2017-11-27
I tried the command, and this is the result:
```
root@srvesp:# ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
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
	Wake-on: d
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: yes
```

So I have 1gbps down + 1gbps up simultaneously?

And how can I see half or full duplex between ethernet switches?

Thanks

---

### Post by slickymaster on 2017-11-27
*Thread moved to **Networking & Wireless**.*

---

### Post by Yellow Pasque on 2017-11-27
```
Speed: 1000Mb/s
Duplex: Full
```

---

### Post by dam034 on 2017-11-27
And between ethernet switches how can I see if it is half or full duplex?

Thanks

---

### Post by Yellow Pasque on 2017-11-27
> **dam034 said:**
> And between ethernet switches how can I see if it is half or full duplex?

I have no idea. Hopefully, someone else can answer that. Good luck.

---

