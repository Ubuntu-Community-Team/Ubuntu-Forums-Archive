---
title: "Not getting full download rate"
date: 2014-09-05
forum: Networking &amp; Wireless
---

### Post by cosmoshell on 2014-09-05
I upgraded a internet servace threw a ISP, the internet speed whent up but its not giving me the same speed as the speedtest websites show. I tried downloading from diffrent places at the same time where like as if there is a cap on the internet speed where you donlowad form a diffrent source and all the other downloads slow down.

supposed to get 50 mb get at a constent rate of 7 mb

```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```

---

### Post by m_duck on 2014-09-06
I know this is marked solved, but I'll put the reason up for Googlers. It is due to internet speeds being advertised in kbps or Mbps (kilo**bits** or mega**bits** per second) and regular people used to dealing in bytes (kilobytes kB, megabytes MB).

In your scenario, your advertised internet speed is 50 megabits per second - convert that to megabytes per second (divide by 8 as there are 8 bits in a byte) and you get 6.25 MB/s (which is close enough).

---

