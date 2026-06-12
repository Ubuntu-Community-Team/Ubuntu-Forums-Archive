---
title: "Machine routes traffic through wrong IP"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by eranga2 on 2015-08-26
Our gateway is a router which redirects all browsing traffic to a proxy server (Ubuntu 14.04.3). Proxy server then process and sends the traffic back to the router through a different interface. Proxy is also connected to the LAN .Some computers in the LAN routes it's traffic directly to 192.168.0.2 ,which is the proxy server, disregarding the default gateway (192.168.0.1) set in the network settings. This has only identified with computers with static IP's for the moment. DHCP users do not have a problem. What could be the reason for this? How could we avoid this behaviour? Find a basic diagram of the network below.

[ATTACH=CONFIG]264058[/ATTACH]

---

### Post by SeijiSensei on 2015-08-26
Your static configurations probably have the wrong address in the "gateway" parameter.  Make it identical to the gateway address that the DHCP server provides.

---

