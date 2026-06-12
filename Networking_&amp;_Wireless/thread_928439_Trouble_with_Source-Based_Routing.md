---
title: "Trouble with Source-Based Routing"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by pepoluan on 2008-09-24
Hi all,

I'm trying to configure Ubuntu Server (8.04.1) to do Source-Based Routing. The scenario is like this: There are 2 Internet connections in my office. All staffs must use connection "A", while the board of directors and top management connect via "B".

The layout is roughly like this:

```

(LAN 172.31.x.x) == [Ubuntu] == ISP "A"
                       |
                   [Firewall] == ISP "B"

```

eth1 to "A", eth0 to "B", and LAN enters through eth2.


Now, I have created the following script:

```
#!/bin/bash

echo
echo "Preparing ALEXIS..."

route add -net 172.31.0.0 netmask 255.255.0.0 gw 192.168.251.1 dev eth2

# Enabling IP forwarding
echo "    Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

echo "    Preparing routing table..."
# The first routing table forwards out the Inet2 (Management)
# to be NAT-ed later
ip route add to default dev eth1 table 1

# The second routing table forwards out the Inet3 (Staff)
# to be NAT-ed later
ip route add to default dev eth0 table 2

## RULES
# Others
ip rule add from 172.31.0.0/17 dev eth2 table 1
# Staff
ip rule add from 172.31.128.0/17 dev eth2 table 2
# Management
ip rule add from 172.31.147.0/24 dev eth2 table 1

iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 202.155.210.182
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.252.1


exit 0

```

What puzzles me, ISP A users can access the Internet successfully, but the users who are (supposed to be) using ISP B can't access the Internet at all. Pings (from their desktop) to the default gateway of ISP B also failed.

Can someone tell me where I went wrong?


Thanks beforehand.

---

