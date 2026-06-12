---
title: "Two Router Network problem"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by ian.leckey on 2008-08-26
Hi,

I'm running a two router network and it's all working swimmingly. The only problem I'm having, is connecting to the web/admin interface on the 2nd router, remotely (locally it works fine).

Router 1 (zyxel wireless modem-router) is connected to the WAN port of Router 2 (pheenet wireless hotspot router).

Router 1:
external ip> 87.164.x.x
internal ip> 192.168.0.1

Router 2 (WAN port):
external ip> 192.168.0.220
internal ip> 192.168.2.254

I can connect to the web interface of router 1 remotely, but how can I get to the interface of router 2? I've tried forwarding ports but to no avail.

Thanks.

---

### Post by jigsaws on 2008-08-26
You should forward port on router 1 - i.e. port 8888 to 192.168.0.220 port 80. You should also check if wan access is enabled at router 2. The problem can be also firewall at router1 or router2.

But if everything is ok, it should works with no problem. Remember to connect port 8888 :-)

---

