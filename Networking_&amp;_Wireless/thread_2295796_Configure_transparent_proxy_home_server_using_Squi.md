---
title: "Configure transparent proxy home server using Squid"
date: 2015-09-21
forum: Networking &amp; Wireless
---

### Post by snakyjake on 2015-09-21
I have a Squid/Dansguardian proxy server that successfully works when the client uses a manually entered proxy address.

What I would like to do is configure a transparent proxy server.  I am assuming a transparent proxy server would not require manual client configurations that directs web traffic to the proxy server.

My LAN environment:
Home/Residential network
Cable Modem -->
------------------------> Router (wifi/ethernet) 
-------------------------------------------------------> Proxy Server (VMWare: Ubuntu Server v15.04 + Squid + Dansguardian)
-------------------------------------------------------> Client 1
-------------------------------------------------------> Client 2

Diagram:
[ATTACH=CONFIG]264573[/ATTACH]
									  
Is it possible the proxy server can intercept traffic from the clients, when the clients have direct access to the router?  I don't understand how traffic is "intercepted" in this diagram.

Do I need to change something on the router?

How do I configure for proxy transparency?

Thanks,
Jake

---

