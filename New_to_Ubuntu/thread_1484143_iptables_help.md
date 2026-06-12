---
title: "iptables help"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Joker5bb on 2010-05-15
I have got a virual AP setup with dhcpd apache and airbase-ng 
and im trying to get it into Non Transparent mode,

i have tried this but it does not work:

ifconfig at0 up
ifconfig lo up
ifconfig at0 10.0.0.1 netmask 255.255.255.0 
ifconfig at0 mtu 1400
route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.0.1
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables -t nat -A PREROUTING -p udp -j DNAT --to 10.0.0.1
iptables -P FORWARD ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 10.0.0.1

---

