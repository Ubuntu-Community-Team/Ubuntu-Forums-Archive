---
title: "NATing by URL?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Bjoeboo on 2007-02-22
I have several machines on my home lan I want to connect to from work. Due to constraints on open outbound ports at work & also because I have several machines on home LAN running similar services (ssh,ssl,http,https) for different things: (linksys-router admin, Newsgroup Ninan-admin, ssl-explorer etc), I want to setup my LAN to resolve different subdomain names coming inbound from internet to different internal LAN boxes. Also maybe do port forwarding although I could do that part with my router/AP. Whats the best way to do this? Install & learn bind? Apache modprobe?

[https://ssl_explorer.myaddress.noip.com]("https://ssl_explorer.myaddress.noip.com/") should resolve internally to 192.168.0.113 

ssh session to Feisty1.myaddress.noip.com should resolve internally to 192.168.0.113
 
ssh session to linksys.myaddress.noip.com should resolve internally to 192.168.0.1 

Finally the tricky one.. Might use stunnel here but I'd prefer to keep all my resolution stuff in one place rather than scattered across router port forwarding, apache mod-probe, bind, iptables chains...etc.

[https://ninan.myaddress.noip.com]("https://ninan.myaddress.noip.com/") should resolve internally to 192.168.0.113:9090 I think port-forwarding breaks SSL protocol by design (this is definition of man-in-the-middle attack) so I probably need to terminate inbound SSL tunnel internally first, then forward it unencryted to internal destination on port 9090...

I am posting in beginner section as this seems quite easy to answer...

---

