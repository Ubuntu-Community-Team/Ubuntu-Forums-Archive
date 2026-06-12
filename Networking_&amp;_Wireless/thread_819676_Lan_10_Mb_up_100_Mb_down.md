---
title: "Lan 10 Mb up 100 Mb down"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by foxops on 2008-06-05
I'm running hardy with on a lan and connecting to a server running hardy server.  When I run iperf I'm getting:

foxops@foxops:~$ iperf -c sentry -f m -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to sentry, TCP port 5001
TCP window size: 0.02 MByte (default)
------------------------------------------------------------
[  5] local 192.168.3.3 port 50177 connected with 192.168.3.2 port 5001
[  5]  0.0-10.4 sec  13.1 MBytes  10.6 Mbits/sec
[  4] local 192.168.3.3 port 5001 connected with 192.168.3.2 port 47530
[  4]  0.0-10.1 sec    113 MBytes  94.1 Mbits/sec

Any ideas?  Both cards are 100 full duplex:
Laptop-
foxops@foxops:~$ sudo ethtool eth0
[sudo] password for foxops: 
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
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes

Server-
foxops@sentry:~$ sudo ethtool eth0
[sudo] password for foxops: 
Settings for eth0:
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
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes

Anyone have any experience with a card pulling 100 Mb down and sending 10 Mb up?

---

### Post by ModelM on 2008-06-05
Maybe I can learn something here. I don't know anything about iperf. Why are the TCP window sizes different between server & client?

---

### Post by foxops on 2008-06-05
> **ModelM said:**
> Maybe I can learn something here. I don't know anything about iperf. Why are the TCP window sizes different between server & client?

I'm not sure, both are stock (as in I haven't fooled with anything related to TCP).  Time to check man pages.

---

