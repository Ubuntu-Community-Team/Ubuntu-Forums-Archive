---
title: "VPN Server and IP Tables"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by vukasin0 on 2008-03-04
Hi,
I installed VPN Server(PopTop) and it work fine without enabled firewall-iptables. PPTP require 1723 port and GRE Internet protocol opened.

My question is, 
How to open GRE Internet protocol in IP Tables?

I tried with:
-A INPUT -i ppp0 -j ACCEPT
-A INPUT -i eth0 -p 47 -j ACCEPT
-A INPUT -i eth1 -p 47 -j ACCEPT
puting in /etc/sysconfig/iptables but without succes.

P.S.
eth1 = internet
eth0 = lan

Server is public on internet with static IP (no need for forwarding).

Sorry for my english I am not native speacker :).

---

### Post by The Cog on 2008-03-04
you probably need to open TCP 1723 as well:
iptables -A INPUT -i ppp0 -j ACCEPT
iptables -A INPUT -i eth0 -p 47 -j ACCEPT
iptables -A INPUT -i eth1 -p 47 -j ACCEPT
iptables -A INPUT -p tcp -dport 1723 -j ACCEPT

I assume you are also setting the default INPUT policy to DROP:
iptables -P INPUT DROP

---

### Post by vukasin0 on 2008-03-05
Port 1723 is opened of course I can telnet on them. INPUT is not DROP by default. In meantime I was reading about how to enable GRE support by kernel.Maybe is trick in that?!!?

---

### Post by The Cog on 2008-03-06
Try chapter 5 of [http://lartc.org/howto/](http://lartc.org/howto/)

---

