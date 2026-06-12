---
title: "pptp vpn-sever problems"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by nownto on 2008-07-29
Greetings, I'm working on a pptp vpn server solution for my iphone. Currently I can connect and get ip address of 192.168.2.100 with a router of 192.168.2.19, both of these are as expected since those are the settings. When I connect I can view the ppp0 connection on my server that is created, which has a ip address of 192.168.2.19. I'm wanting to forward all my traffic across this vpn which is where the problem is coming from. Upon connection on the client I'm unable to ping 192.168.2.19, but the ppp0 interface shows the icmp packets coming across using tcpdump. Do to this dead connection none of my traffic is being sent across the vpn, any help on this is greatly appreciated.

---

