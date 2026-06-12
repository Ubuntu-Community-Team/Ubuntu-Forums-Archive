---
title: "Access server over PPTP"
date: 2015-12-21
forum: Networking &amp; Wireless
---

### Post by evvdcaec on 2015-12-21
Server A at Site A is connected to a private VPN provider (IPVanish) via OpenVPN. I want all internet traffic to go over this VPN, which it does. This is good.

Client B at Site B can SSH into Server A as well as access it's web UIs using Server A's ISP's public IP address. This is good.

From Site B I can connect to Server A with PPTP and I can access all the network resources at Site A. This is good. 

I cannot, however, access any resources from Server A itself when I am connected to it via PPTP from Site B. This is bad. I would appreciate some help in fixing this.

---

### Post by evvdcaec on 2015-12-21
Additional details which may or may not help

OpenVPN .conf file
```
client
dev tun
proto udp
remote nyc-a01.ipvanish.com 443
resolv-retry infinite
nobind
persist-key
persist-tun
persist-remote-ip
ca ca.ipvanish.com.crt
tls-remote nyc-a01.ipvanish.com
auth-user-pass pass.txt
comp-lzo
verb 3

```

I then run this to restore the ability to ssh in:
```
ip rule add from 10.26.0.156 table 128
ip route add table 128 to 10.26.0.0/24 dev eth2
ip route add table 128 default via 10.26.0.1

```

output of 'route -n'
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.16.1     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.26.0.1       0.0.0.0         UG    0      0        0 eth2
10.26.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth2
128.0.0.0       172.20.16.1     128.0.0.0       UG    0      0        0 tun0
172.20.16.0     0.0.0.0         255.255.252.0   U     0      0        0 tun0
216.151.180.2   10.26.0.1       255.255.255.255 UGH   0      0        0 eth2

```

pptpd.conf
```
option /etc/ppp/pptpd-options

logwtmp

localip 10.26.0.156
remoteip 10.26.0.190-199

```

pptpd-options
```
name fileserver
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 8.8.8.8
ms-dns 8.8.4.4
proxyarp
nodefaultroute
lock
nobsdcomp
novj
novjccomp
nologfd

```

---

### Post by evvdcaec on 2015-12-24
Merry Christmas!*

[SIZE=1]*shameless self bump.[/SIZE]

---

