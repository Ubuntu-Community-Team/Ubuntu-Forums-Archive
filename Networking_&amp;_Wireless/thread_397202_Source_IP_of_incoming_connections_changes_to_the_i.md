---
title: "Source IP of incoming connections changes to the ip of the Gateway"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by ingipingi on 2007-03-30
I get a problem with Ubuntu server 6.10, whenever I try to setup a gateway (computer to forward internet back and forth from the localnet to the internet).

When an email comes from the internet to my server, the gateway-server dnat's the email to the mail server, but the it changes the source address of the packets (which make up the email) to the ip address of the server-gateway.

With my old fedora core 4 server this works like a charm, I use the same iptables rules.

My understanding was that dnat should only change the destination address, and snat should change the source address, am I missing something?

I have two nics (ethernet cards) connected to the server, one on 192.168.0.241 (eth0: the internal network) and the other on 192.168.10.241 (eth1: external network).

As I use webmin, my iptables command is something like this: iptables -t nat -A PREROUTING -p tcp --dport 25 -i eth1 -j DNAT --to 192.168.0.253:25

Could somebody please tell me what I am doing wrong?

---

