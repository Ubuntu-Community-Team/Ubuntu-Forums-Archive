---
title: "Server with multiple interfaces?"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Tixer on 2008-05-19
I have a server with three interfaces, eth0, eth1, and wlan0.

All three of these all have their own domains through dyndns. eth0 and wlan0 have the domains controlled by their routers, and eth1, which is a pppoe connection, has ddclient running on it. I figured that if I have lighttpd bound to localhost, I should therefore be able to access my server on all three connections, assuming all ports are forwarded.

On both routers, typing in the domain goes nowhere. If I append the remote management port to the end of the domain, I can log into both routers. However, I am unable to get to my web server through either router.

I can, through other computers on their respective networks, navigate to the server through the local ip, 192.168.1.110 or 192.168.0.110 respectively. These both work, but I can't use the domains on the routers to go there.

As for the pppoe connection, everything appears to be working fine. Is there some reason why this isn't working, that I'm not thinking of? I can't figure out why a server would reply to the local IP and the router would reply to the domain on remote assistance, but the domain won't forward to the server.

Any ideas?

---

