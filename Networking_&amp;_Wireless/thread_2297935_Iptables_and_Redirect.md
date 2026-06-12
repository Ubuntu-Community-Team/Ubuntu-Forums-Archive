---
title: "Iptables and Redirect"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by faber-cpu on 2015-10-07
Please help. I need to redirect connection. I'll move mail serwer to other machine and need to REDIRECT 587 port to new serwer from old one. OLD and NEW serwers have public IP so old serwer should redirect connection on WAN interface to new server.
I try this:
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -t nat -A PREROUTING -p tcp -d old.server --dport 587 -j DNAT --to new.server:587

it works but the problem is with changed source IP (NAT), I dont want NAT, the new server should see connection from original IP but I see connection from old.server. How to fix this ?

---

### Post by faber-cpu on 2015-10-07
and again my test:
with only this it not work
iptables -t nat -A PREROUTING -p tcp -d old.server --dport 587 -j DNAT --to new.server:587

with this work but source IP is changed
iptables -t nat -A PREROUTING -p tcp -d old.server --dport 587 -j DNAT --to new.server:587
iptables -t nat -A POSTROUTING -p tcp -d new.server --dport 587 -j SNAT --to-source old.server

The problem is with interface ? that forward is done on the same interface ?

---

