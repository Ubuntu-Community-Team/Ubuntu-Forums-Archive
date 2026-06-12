---
title: "HTTP requests take a while to come back initially"
date: 2018-01-26
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-01-26
I am running a Ubutnu 16 server with iptables and dhcp/dns on it.  (I am unable to find the dhcp process name; I see isc-dhcp-common and client, but NOT server).  I know DHCP works.  When I start up my windows 10 laptop, or wake it from sleep, it connects to wifi right away.  I can ping the lan interface on the ubuntu server (192.168.1.1).  I can also ssh to it.  I can NOT load a page for 1-2 minutes.  A ipconfig shows settings are alright.  My setup is this: Ubuntu server -> wap (dd-wrt) -> client (windows).  The wap has the dhcp server disabled.  the wan connection type is disabled on it.  I am not sure why there is such a long delay on loading pages (seems unable to connect), when the client has an IP, and can ping the server.  My guess is the way the server is configured with firewall rules/dhcp, is causing some kind of delay.

---

