---
title: "Load balance error"
date: 2014-11-19
forum: Networking &amp; Wireless
---

### Post by Rafael_ on 2014-11-19
I'm trying to do a load balance with 2 ISP links, using Ubuntu 14.04.1 LTS amd64 (kernel 3.13.0 24-generic), squid3 3.3.8, iptables 1.4.21 .

I used some how-to, but no success.
With this configuraton all traffic use only one link (OI) with squid3. Without proxy and using [COLOR=#000000][FONT=verdana]MASQUERADE[/FONT][/COLOR], the page loading are extremely slow.
With this configuration, the boot time is at about 3 minutes.

I don't have any idea what's wrong. Can someone help me please?


My balance script :
```

#!/bin/bash
OI_IPA="192.168.254.18"
OI_NET="192.168.254.0/24"
OI_GAT="192.168.254.254"
OI_NIC="eth1"
COPEL_IPA="177.x.x.179"
COPEL_NET="177.x.x.176/29"
COPEL_GAT="177.x.x.177"
COPEL_NIC="eth2"
ip route flush table OI
ip route flush table COPEL
ip route flush table BALANCEAMENTO
ip rule del from 192.168.254.18 table COPEL
ip rule del from 192.168.254.18 table OI
ip rule del fwmark 0x2 table BALANCEAMENTO
ip rule del fwmark 0x1 table COPEL
ip route del default
ip route add $OI_NET dev $OI_NIC src $OI_IPA table OI
ip route add default via $OI_GAT table OI
ip rule  add from $OI_IPA table OI
#ip route add 127.0.0.0/8 dev lo table OI 
ip route add $COPEL_NET dev $COPEL_NIC src $COPEL_IPA table COPEL
ip route add default via $COPEL_GAT table COPEL
ip rule  add from $COPEL_IPA table COPEL
#ip route add 127.0.0.0/8 dev lo table COPEL 
ip rule add fwmark 2 table BALANCEAMENTO
ip rule add fwmark 1 table COPEL
ip route add default scope global table BALANCEAMENTO nexthop via $OI_GAT dev $OI_NIC weight 1 nexthop via $COPEL_GAT dev $COPEL_NIC weight 1
ip route add default via $OI_GAT
ip route flush cache

```

My firewall script:
```

#!/bin/bash
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING -i eth1 -d 192.168.254.18 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.8:80
iptables -t mangle -A PREROUTING -s 192.168.0.0/24 -d 0/0 -j MARK --set-mark 2
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -j MASQUERADE

# iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
# iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE

iptables -t nat -A PREROUTING  -i eth0 -p tcp -s 192.168.0.0/24 --dport 80 -j REDIRECT --to-port 3129
# I try define a site load from one link, but doesn't work with this:
iptables -I PREROUTING -t mangle -s 192.168.0.0/24 -d proxydetect.com -j MARK --set-mark 1

```

My /etc/network/interfaces file:
```

auto eth0
iface eth0 inet static
    address 192.168.0.8
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
# oi
auto eth1
iface eth1 inet static
    address 192.168.254.18
    netmask 255.255.255.0
    network 192.168.254.0
    broadcast 192.168.254.255
    gateway 192.168.254.254
    dns-nameservers 201.10.120.2 201.10.128.3 8.8.8.8 8.8.4.4
    dns-search transardo
# copel
auto eth2
iface eth2 inet static
    address 177.x.x.179
    netmask 255.255.255.248
    network 177.x.x.176
    broadcast 177.x.x.183
    gateway 177.x.x.177    
    dns-nameservers 200.195.159.100 200.195.159.101 

```

---

