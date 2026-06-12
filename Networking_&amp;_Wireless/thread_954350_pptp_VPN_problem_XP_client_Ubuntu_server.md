---
title: "pptp VPN problem XP client Ubuntu server"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by guyh2 on 2008-10-21
Hi All

Recently installed 8.04 server to replace a WS2003.
Pretty much got everything up and running apart from the VPN.

Using an XP client and the Ubuntu 8.04 server, 
I can connect from the Internet ok, 
I can ping the server's internal IP 192.168.1.200, 
I can browse smb shares on the server
However 
I can't ping any other machines on the internal network 192.168.1.x
I can't browse any other smb shares on the internal network

The server is behind a modem/router on a switch with the rest of the machines. It has a single eth0 card

The client's end seems to be ok, only packets destined for the internal net are sent over the VPN, routing table looks fine etc.

Banging my head against the wall here now :(

Thanks for reading :)

---

