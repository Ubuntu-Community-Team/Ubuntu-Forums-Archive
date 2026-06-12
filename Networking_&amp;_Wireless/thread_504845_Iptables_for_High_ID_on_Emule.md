---
title: "Iptables for High ID on Emule"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by naureo on 2007-07-19
I've read a lot of texts on the internet, but couldn't solve my problem.

I want to have a high ID on emule. If I connect the modem directly to my PC I get it, because the ports are OK on the modem.

Using an Ubuntu server between the modem and the computer I always get Low Id.

I have: ADSL Modem --- (connected to) an Ubuntu Server 7.04 --- (connected to a switch) with all machines connected to the switch.

The adsl modem ip is: 10.1.1.1
Ubuntu Eth0 is: 10.1.1.4
Ubuntu Eth1 is: 192.168.1.99
The pc running emule is: 192.168.1.11

I also have a ppp0 interface since I am using bridge mode with my modem (it's a dlink dsl 500b, in router mode it sux).

The emule ports are 15001 tcp and 15002 udp.

Here are my rules:
iptables -A FORWARD -p tcp --dport 15001 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 15001 -j DNAT --to 192.168.1.11

iptables -A FORWARD -p udp --dport 15002 -j ACCEPT
iptables -t nat -A PREROUTING -p udp --dport 15002 -j DNAT --to 192.168.1.11

I also tried the option "-i eth0/eth1/ppp0" on the second and fourth lines... but it didn't work.

Anyone?? Thanks

---

