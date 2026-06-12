---
title: "pptp (client to server) ok / (client to client) no ok"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by koe1974 on 2008-11-30
Solved:

$cat /proc/sys/net/ipv4/ip_forward 
0

$sudo sysctl -w net.ipv4.ip_forward=1

+-------------------------------------------+

I have a pptp server on ubuntu server 8.04LTS. All of my WinXP client machines can connect to the server and browse shares but they cannot communicate with one other. I need the clients to also be able to talk to one another because there is a printer on one client everyone needs access to.

I think it is a routing issue but I am not 100% sure how this all works.

Each time a client connects to the server a new ppp device is created. So for example: 
ClientA (192.168.101.10 : ppp0) / ClientB (192.168.101.11 : ppp1) / Etc

How can I get these devices talking?

I have tried to ping and connect via remote desktop but it times out with or without the firewall.

Any suggestions would be greatly appreciated.

FYI: I have it all working with hamachi but would prefer to rule out the middle man.

---

