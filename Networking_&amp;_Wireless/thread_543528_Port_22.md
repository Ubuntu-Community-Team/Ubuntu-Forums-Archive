---
title: "Port 22"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Yanski on 2007-09-05
Hi guys hope some one can help.. After getting a router from my ISP..a D-Link DSL-G624T I did a shields up scan on GRC. The result was all stealth except port 22 which is just closed,   With my previous router...a Voyager 210 all was stealth all the time. How can I stealth that port?? Tried D-Link support with no luck ](*,)
I use Ubuntu feisty and have Firestarter installed.
Very newbie advice would be appreciated. Thanks.

Result of scan from Speed Guide:

 22/tcp   	 closed   	ssh  	Secure Shell - most common use is command line access, secure replacement of Telnet. Could also be used as an encrypted tunnel for secure communication of virtually any service.

Some trojans also use this port: InCommand, Shaft, Sk

 22/udp   	 filtered?   	ssh  	Old verson of pcAnywhere uses port 22/udp (no relation to ssh and port 22/tcp).
The real pcAnywhere port is 5632. The value 0x0016 (hex) is 22 decimal; the value of 0x1600 (hex) is 5632 decimal. Some say that pcAnywhere had a byte-swapping bug that led to its incorrect use of port 22.
Total scanned ports: 	1
Open ports: 	0
Closed ports: 	0
Filtered ports: 	1

---

