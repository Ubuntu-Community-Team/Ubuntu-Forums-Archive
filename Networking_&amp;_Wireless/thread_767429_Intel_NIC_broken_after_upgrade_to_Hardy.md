---
title: "Intel NIC broken after upgrade to Hardy"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by nickswift on 2008-04-25
All working fine in Gutsy. Ran the upgrade and everything worked great apart from my network card.

# lspci -nn | grep Gigabit
03:00.0 Ethernet controller [0200]: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) [8086:10b9] (rev 06)
# lsmod | grep e10
e1000                 125760  0 
e1000e                 97828  0 

With link light up on device, ethtool shows:

# ethtool eth1
Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: no

Anyone have any ideas?

---

### Post by nickswift on 2008-04-27
Downloaded the latest e1000 drivers from sourceforge. A quick rmmod and modprobe did the trick.

---

