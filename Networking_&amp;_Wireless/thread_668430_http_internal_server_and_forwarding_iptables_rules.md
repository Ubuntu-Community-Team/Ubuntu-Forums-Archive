---
title: "http internal server and forwarding iptables rules"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by giannirusso on 2008-01-15
Hello, I had an ipchains firewall and now Im trying to set an iptables firewall.
These are the rules:
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -F
iptables -F -t nat
iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -A FORWARD -d 192.168.1.0/24 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -d 0.0.0.0/0.0.0.0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s 127.0.0.1/8 -j ACCEPT

#iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.168.1.200:80
#iptables -I FORWARD -p tcp --dport 80 -d 192.168.1.200 -j ACCEPT
All seems work but I think there is something wrong:
when I uncomment the last two lines, Im able, from outside the network, to connect to my webserver on internal 192.168.1.200 port 80 but no www internet connection for other internal pc.
It seems that ALL incoming tcp port 80 connections are forwarded on internal 192.168.1.200 server, also the www request of other internal pc.
Thanks for help.
Gianni

---

