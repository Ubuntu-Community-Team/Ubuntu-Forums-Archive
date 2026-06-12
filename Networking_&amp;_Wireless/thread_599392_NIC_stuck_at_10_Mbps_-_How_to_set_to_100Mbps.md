---
title: "NIC stuck at 10 Mbps - How to set to 100Mbps"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by cjbujold on 2007-11-01
Slow Network!  Using Ubuntu 7.10 and the network card only runs at 10 Mbps.  How do we set it so that it runs at 100 Mbps?

> sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000001 (1)
	Link detected: yes


Thanks

---

### Post by thirunavukkarasu on 2007-11-01
sudo ethtool -s eth0 speed 100 duplex full autoneg on

here eth0 represents the your LAN device; and also please refer to the man pages of eththool for more.

rgds,
Thiru.S

---

### Post by netztier on 2007-11-01
> **thirunavukkarasu said:**
> sudo ethtool -s eth0 speed 100 duplex full autoneg on


That doesn't make sense. It's either "autoneg" or "duplex full". Autoneg is about negotiation of duplex modes - activating autoneg and a fixed setting is pointless.

regards

Marc

---

### Post by netztier on 2007-11-01
> **cjbujold said:**
> Slow Network!  Using Ubuntu 7.10 and the network card only runs at 10 Mbps.  How do we set it so that it runs at 100 Mbps?


If that's a 3com card, you might want to read this thread:

[http://ubuntuforums.org/showthread.php?t=503194](http://ubuntuforums.org/showthread.php?t=503194)

Best regards

Marc

---

