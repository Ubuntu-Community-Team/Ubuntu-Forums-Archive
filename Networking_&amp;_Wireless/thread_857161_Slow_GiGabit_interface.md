---
title: "Slow GiGabit interface"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by cnolan011 on 2008-07-12
MB = ASUS-P5N32-E with Dual Gigabit ethernet LAN

when I do a:
```
cnolan@cnolan-dvr:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ MII ]
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
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```
I believe that the 'Speed' should read '1000Mb/s'
when I had this MB with XP installed I got high transfer rates, but now with 8.04, it is slow and showing 'Speed' '100Mb/s'
I have a Gb switch that I have not changed anything on it, . .

---

### Post by cnolan011 on 2008-07-12
i did a:
```
ethtool -s eth0 speed 1000 duplex full
```
and the speed changed to 'Speed: 1000Mb/s', . . 
but transfer times using scp are still really slow, around 800KB/s
 and before they where many times faster, . . . 
i am pscp froma windows machine, . . are there any know speed issues associated with PSCP ?

---

### Post by zakhooi on 2008-08-04
I have exactly the same problem.
If you've found a solution please inform us.

Thanks in advance

---

