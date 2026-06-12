---
title: "can't get past iptables please help"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by mlalich on 2006-11-03
Here's my setup

Internet
|
L Router (10.1.1.1) ----- PC's connected to router
|
|
Ubuntu box Linux (running iptables)
| (2 NICs)
L eth0 (10.1.1.2) Statically assigned
L eth1 (192.168.2.1) Statically assigned
|
|
Cisco Switch (192.168.2.2)
L DNS/DHCP server (192.168.2.5) statically assigned
L Workstation (192.168.x.x) Dynamically assigned

Here's my rules for iptables

/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT --protocol tcp --dport 22 -j ACCEPT
iptables -A INPUT --protocol icmp -j ACCEPT
iptables -A INPUT --protocol tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

My issue is I can get out to the internet on the Linux box, but from anything on the 192.168.2.0 network can't even ping past the eth0 interface on the Linux box. I can ping to 10.1.1.2, but not to 10.1.1.1 or past onto the internet. I figure it's a rule or an iptables setting, but I don't know iptables enough to know. How can I get out from my internal network??

---

### Post by bmillsap on 2006-11-03
Is your default rule to drop on the forward chain?  If so, it looks like maybe you're allowing established traffic on the way out, but not on the way in?

Also, although I don't have this setup, I think MASQUERADE is typically used when the outbound connection has a dynamic IP.  If it's static, I think an SNAT rule is usually used.  I'm not sure if MASQUERADE wouldn't work, though.

---

