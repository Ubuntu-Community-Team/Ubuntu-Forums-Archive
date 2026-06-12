---
title: "OpenVPN configuration: can ping VPN server, but not server-side LAN"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by ozzie1 on 2015-11-23
I've set up OpenVPN on my server, a box with just a single NIC running Ubuntu MATE 15.10. I'm configuring it as a routed VPN, config files and routing info will be posted below. The network looks something like this:

VPN Server - LAN 10.31.12.15 - VPN 10.31.11.1
LAN router (running dd-wrt) - LAN 10.31.12.1 - WAN PPPoE DHCP (DDNS to access VPN)
Client - Running Windows 7 - LAN 192.168.0.x - VPN 10.31.11.x

From the client, I can ping the server at 10.31.11.1, but not at 10.31.12.15 or the router at 10.31.12.1. IP forwarding is enabled on the server.

Any help would be greatly appreciated, this was a fallback plan after the VPN server on the netgear router I was setting up failed to work as expected, and I need to get it up and running ASAP.


server config:
```
port 1194
proto udp
dev tun

ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret
dh /etc/openvpn/keys/dh2048.pem
tls-auth /etc/openvpn/keys/ta.key 0 # This file is secret

topology subnet

server 10.31.11.0 255.255.255.0
push "route 10.32.12.0 255.255.255.0"
push "dhcp-option DNS 10.31.12.1"
push "dhcp-option WINS 10.31.12.15"
ifconfig-pool-persist ipp.txt
client-to-client

keepalive 10 120
cipher AES-256-CBC   # AES
comp-lzo

max-clients 20
persist-key
persist-tun

status openvpn-status.log
verb 3
```

server routes:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default            dd-wrt          0.0.0.0         UG    100    0        0 eth0
10.31.11.0      *               255.255.255.0   U     0      0        0 eth0
10.31.11.0      *               255.255.255.0   U     0      0        0 tun0
10.31.12.0      *               255.255.255.0   U     100    0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 tun0
```

server iptables:
```
root@server:/etc/openvpn# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  10.32.12.0/24        anywhere             ctstate NEW
ACCEPT     all  --  10.31.11.0/24        anywhere             ctstate NEW
ACCEPT     all  --  10.31.11.0/24        10.31.12.0/24        ctstate NEW

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

root@pattern:/etc/openvpn# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  10.32.12.0/24        anywhere             ctstate NEW
ACCEPT     all  --  10.31.11.0/24        anywhere             ctstate NEW
ACCEPT     all  --  10.31.11.0/24        10.31.12.0/24        ctstate NEW

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

client config:
```
client
dev tun
proto udp
remote xxx.duckdns.org 1194
resolv-retry infinite
nobind
persist-key
persist-tun

ca ca.crt
cert client.crt
key client.key

remote-cert-tls server
tls-auth ta.key 1

cipher AES-256-CBC
comp-lzo
verb 3
route-method exe
route-delay 2
```

client routes:
```
IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.0.1     192.168.0.58     20
       10.31.11.0    255.255.255.0         On-link        10.31.11.2    276
       10.31.11.2  255.255.255.255         On-link        10.31.11.2    276
     10.31.11.255  255.255.255.255         On-link        10.31.11.2    276
       10.32.12.0    255.255.255.0       10.31.11.1       10.31.11.2     21
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      192.168.0.0    255.255.255.0         On-link      192.168.0.58    276
     192.168.0.58  255.255.255.255         On-link      192.168.0.58    276
    192.168.0.255  255.255.255.255         On-link      192.168.0.58    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link      192.168.0.58    276
        224.0.0.0        240.0.0.0         On-link        10.31.11.2    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link      192.168.0.58    276
  255.255.255.255  255.255.255.255         On-link        10.31.11.2    276
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0      192.168.1.1       1
          0.0.0.0          0.0.0.0      192.168.1.1  Default
```

I even added a route to the router:
```
10.21.1.1    255.255.255.255    0.0.0.0    UH    0    ppp0
10.31.11.0    255.255.255.0    10.31.12.15    UG    0    LAN & WLAN
10.31.12.0    255.255.255.0    0.0.0.0    U    0    LAN & WLAN
169.254.0.0    255.255.0.0    0.0.0.0    U    0    LAN & WLAN
0.0.0.0    0.0.0.0    10.21.1.1    UG    0    ppp0
```

---

### Post by ozzie1 on 2015-11-25
bump

EDIT: Bah, found the problem, I had

```
push "route 10.32.12.0 255.255.255.0"
```

when it should have been 10.**31**.12.0. In hindsight, that's a really obvious typo, and it's far from the first time I've made it. Guess that explains why I wasn't seeing anything on tun0 with tcpdump when pinging the lan. The route in the router isn't necessary to ping from the VPN to the local net, but is necessary for traffic going the other way. masquerade was supposed to make that Just Work (tm), but apparently it didn't.

---

