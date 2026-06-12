---
title: "UFW blocks OpenVPN Clients"
date: 2017-10-05
forum: Networking &amp; Wireless
---

### Post by jduskey on 2017-10-05
I have a server that is set to allow 192.168.1.0/24 to connect, as well as forcing all traffic through vpn. When I use pfsense' openvpn server, I can connect to my home network fine and access all clients except ones that are running ufw. My client IP is 10.0.8.2 and I've allowed all traffic in UFW from that IP range but still no dice.

---

### Post by TheFu on 2017-10-07
You said the server only allows 192.168.1.0/24.  Why would traffic from 10.0.8.2 be allowed?

I would check the log files.  Might want/need to enable or turn up the logging for the different parts - firewall, server, vpn.

---

