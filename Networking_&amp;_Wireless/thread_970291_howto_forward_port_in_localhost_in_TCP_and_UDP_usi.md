---
title: "howto forward port in localhost in TCP and UDP using iptables"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by highfly22 on 2008-11-04
Hi,
I need iptables do something like 
sudo ssh  -L 139:localhost:22139 haiwei@localhost
but only allow the localhost access this port.

And how to configure iptables to implement UDP port forward?
Cause SSH only support tcp port forward.

I try this, but it doesn't work:
sudo iptables -t nat -A PREROUTING -p tcp -d 127.0.0.1 --dport 139 -j DNAT --to 127.0.0.1:22139

thanks,
Haiwei

---

### Post by widor on 2008-11-04
What output do you get from the following?

sudo iptables -L FORWARD -nv
sudo iptables -t nat -L -nv

---

