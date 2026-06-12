---
title: "Routing with 2 network cards"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Darkleton on 2008-05-23
Hi,

The solution I'm currently trying to implement is an Ubuntu server which will act as gateway/router/proxy/filter for 100 PDAs.
The server has two network cards, laid out:
eth0 = 192.168.1.2 - connected directly into an ADSL router (192.168.1.1)
eth1 = 192.168.2.1 - connected to internal switch

What we want are for the PDAs to come in via eth1, go through Squid and DansGuardian and go out via eth0 to the internet. 

I've never actually set up Ubuntu in a server sense so never had to use iptables but I know I've got to do that for forwarding.
I've set up the sysctl ipv4 forwarding setting, so now need to get on to iptables and then squid.

Firstly, what iptables rules should I set so that any internal connections get routed via squid out to the internet, and secondly what options in squid would I set to make this work, namely which ip would i use to listen on, eth1 or eth0.  
We want squid to work transparently (get info via DHCP) but I guess that's another question.
Any help would be greatly appreciated.

Just out of interest, this is what I was told, but wanted to check if it was correct before doing it:

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.2.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

Thanks

Mike

---

