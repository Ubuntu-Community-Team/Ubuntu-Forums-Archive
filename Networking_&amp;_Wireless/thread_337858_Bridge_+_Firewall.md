---
title: "Bridge + Firewall"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by raspi on 2007-01-13
Hi,

I'm configuring Linux ethernet bridge with brctl.

Current configuration:
INTERNET - ADSL router - *Linux Bridge* - Switch - Machines

I have eth0 + eth1 = br0

It works fine but now I'd like to set up firewall with ebtables or iptables.
I don't want to use NAT because some of the machines has public IP and some have private IPs.

How do I set up these firewall rules:
-- LAN-side: --
ALLOW all outgoing traffic to any port to INTERNET-side

-- INTERNET-side: --
DROP ALL
ALLOW INCOMING (TO LAN):
-TCP PORT 22 (SSH)
-TCP PORT 80 (HTTP)

I don't want my ISP to see my LAN IP:s so:
DROP 10.0.0.0/8 (including ARP/RARP)
DROP 172.16.0.0/12 (including ARP/RARP)
DROP 192.168.0.0/16 (including ARP/RARP)
DROP 169.254.0.0/16 (including ARP/RARP)
ALLOW 192.168.0.1 (So I can configure ADSL router through LAN-side)

Also I'd like one chain where I can dynamically add ports which can go to LAN-side from INTERNET-side.

---

### Post by raspi on 2007-01-14
Something like this?

```

#!/bin/sh
IPT=/sbin/iptables

LANIF=eth0
INETIF=eth1

$IPT -P FORWARD DROP

$IPT -A FORWARD -m physdev --physdev-in $LANIF --physdev-out $INETIF -j ACCEPT
$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -p tcp -m tcp --dport 22 -j ACCEPT
$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -p tcp -m tcp --dport 80 -j ACCEPT

$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -s 10.0.0.0/8 -j DROP
$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -s 172.16.0.0/12 -j DROP
$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -s 192.168.0.0/16 -j DROP
$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -s 169.254.0.0/16 -j DROP

$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -s 192.168.0.1/32 -j ACCEPT

#$IPT -A FORWARD -m physdev --physdev-in $INETIF --physdev-out $LANIF -j DROP

```

---

