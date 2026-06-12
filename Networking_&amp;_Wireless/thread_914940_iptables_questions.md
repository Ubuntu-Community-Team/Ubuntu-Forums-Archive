---
title: "iptables questions"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-09-09
Good day, everyone!
Here's my firewall:```
#!/bin/sh

# Flush all tables to default:
sudo iptables -F
sudo iptables -F -t nat

# Setting up default politics:
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD DROP

# Allow established connections:
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow all for loopback:
sudo iptables -A INPUT -i lo -s 127.0.0.0/255.0.0.0 -j ACCEPT

# Allow all for local networks
sudo iptables -A INPUT -s 192.168.0.0/255.255.255.0  -j ACCEPT

# Allow ICMP for all
sudo iptables -A INPUT -p icmp -j ACCEPT

# Nat for local networks:
# 192.168.0.0/24:
sudo iptables -t nat -A PREROUTING -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/255.255.255.0 -j MASQUERADE
sudo iptables -A FORWARD -s 192.168.0.0/255.255.255.0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.0.0/255.255.255.0 -m state --state RELATED,ESTABLISHED -j ACCEPT

#Enable forwarding
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo modprobe ip_nat_pptp
```Yes, it uses PPTP connection and redirects port 80 to 3128 (squid). I've got questions about it:
1. Is my current setup secure enough? 
2. I'd love to close all ports and enable only some of them, like http and icq, but it fails if I change the line ```
sudo iptables -A FORWARD -s 192.168.0.0/255.255.255.0 -j ACCEPT
``` to ```
iptables -A FORWARD -s 192.168.0.0/255.255.255.0 -p TCP --dport 80 -j ACCEPT
```. I'm pretty new to iptables, I understand that it is necessary to enable ICMP traffic, so I did, but it didn't work for me anyway. Meanwhile ```
iptables -A FORWARD -s 192.168.0.0/255.255.255.0 -p TCP --dport 80 -j DROP
``` works and blocks the outgoing traffic on port 80... Why?

---

