---
title: "Broken iptables config"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by DarkHorizon on 2007-01-31
Hi all,

This week, I had been fiddling with my iptables configuration, and I've inadvertently done something Bad(TM). As the system is right now, I am able to NAT anything coming from my network going to the internet, however any connection originating from the host will not even get to the ISP gateway.

I believe the problem is related to me dropping all configurations (using the following command) in the `nat` table, due to a bad rule I'd left hanging around some time ago, but I can't be sure:

```
iptables -t nat -F
```

I'm not sure what else I might have lost, nor do I know how to restore it.

Could someone describe the necessary iptables rule to be able to restore this type of connection?

My current iptables config:

```
# LAN subnet
PRIVATE=10.0.0.0/24

# Loopback address
LOOP=127.0.0.1

# Ethernet interfaces
INET=ppp0
LAN=eth1

# Delete old iptables rules and temporarily block all traffic
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -F

# Set default policies
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
iptables -P FORWARD DROP

# Masquerade local subnet
iptables -t nat -A POSTROUTING -s $PRIVATE -o $INET -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Best regards,

---

