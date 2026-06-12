---
title: "any way to fix ubuntu's problem with that network card (VT6102)???"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by coniglia on 2008-07-10
[SIZE="4"]Hello all,
I'm using ubuntu 8.04 (but not from a long time) in my desktop and laptop as well, sharing the same internet connection from d-link router through a switcher...
I'm facing a very slow internet speed problem with the desktop computer that using "VIA Technologies, Inc. VT6102" built in network card.
The problem doesn't exist with my current windows xp with the same connection and network card, it doesn't exist also with my laptop running the same ubuntu version and the same internet connection but with a different network card 

As example: download speed while downloading from synaptic at desktop is from 5 to 10 kb versus speed from 20 to 30 at the laptop :(

even the real player tells me when i trying to run it's internet connection test that I'm using "Dual ISDN (128 Kbps)" while i`m already using  dsl 256 kbps 
and the same program tells at the laptop that i`m using the dsl 256 k  


After searching the internet and specially this forum (and after trying all fixes also) i discovered that the problem is with the computability between ubuntu and that network card exactly (VIA VT6102) 
I don't know it's the driver or something in configurations.....


I tried many many fixes without any result please try to tell me if there is a way to fix that problem :confused::confused::confused:


Thanks all
        [/SIZE]

---

### Post by coniglia on 2008-07-11
any help please...or if there is no hope to fix this issue just tell me :(

---

### Post by chili555 on 2008-07-11
Does:```
sudo ethtool eth0
```say anything suspicious?

---

### Post by coniglia on 2008-07-11
well, i did that and i think there is no problem but actually i`m not experienced at this issues. So, that's what i get 

```
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000001 (1)
	Link detected: yes

```   

Thanks a lot :)

---

