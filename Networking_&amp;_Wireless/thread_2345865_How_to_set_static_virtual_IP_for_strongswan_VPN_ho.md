---
title: "How to set static virtual IP for strongswan VPN host?"
date: 2016-12-08
forum: Networking &amp; Wireless
---

### Post by unvilon on 2016-12-08
Hi everyone, 
I have OpenVZ server with working strongswan IPSec VPN.
I managed to set up static virtual IP for VPN clients, but my server always has 10.0.2.15. and I can't figure out why and how to change it..
So, I want to set this address manually, but I have no idea where.. Currently VPN clients, gets IP from 10.0.0.0/24, so I want the server IP to be 10.1.0.0


Also, I want to have an access to localhost of this server from clients only through VPN. Currently I don't have it, but I have an access to another clients.

```

iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.0.0.0/24  -j ACCEPT
iptables -A INPUT -i venet0 -p esp -j ACCEPT
iptables -A INPUT -i venet0 -p udp --dport 500 -j ACCEPT
iptables -A INPUT -i venet0 -p tcp --dport 500 -j ACCEPT
iptables -A INPUT -i venet0 -p udp --dport 4500 -j ACCEPT
iptables -A INPUT -i venet0 -p udp --dport 1701 -j ACCEPT
iptables -A INPUT -i venet0 -p tcp --dport 1723 -j ACCEPT
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o venet0 -j MASQUERADE

```

How I should change my iptables? Please help.. :)

---

### Post by unvilon on 2016-12-19
Bump.

---

