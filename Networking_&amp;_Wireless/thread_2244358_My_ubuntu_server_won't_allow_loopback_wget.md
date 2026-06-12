---
title: "My ubuntu server won't allow loopback wget"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by Bruno_SK on 2014-09-15
I have the following rules on my Ubuntu Server 14.04:


```
#!/bin/sh
# Flushing all rules
iptables -F
iptables -X


# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP


# Allow unlimited traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


# Allow incoming SSH
iptables -A INPUT -p tcp --sport 513:65535 --dport 22 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 --dport 513:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT


# Forward 80 to 8080
iptables -I INPUT -m mark --mark 1 -j DROP
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination SERVER_IP:8080
iptables -t mangle -A PREROUTING -p tcp --dport 8080 -j MARK --set-mark 1


iptables -A INPUT -p tcp --dport 8080 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 8080 -m state --state ESTABLISHED,RELATED -j ACCEPT


# Allow DNS lookup
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A INPUT -p tcp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT

```And I'm unable to do a simple (connection refused):
```
wget http://www.example.com

```or (connection refused):
```
wget http://localhost/

```or even (stays idle):
```
wget http://localhost:8080

```How do I fix my config in order to be able to do it?


Thanks!

---

