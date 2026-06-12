---
title: "Dual Wan configuration problem..."
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by elmeri on 2007-06-13
Hello,
I have a problem with my current Ubuntu nat server. I cannot get it working as it should be. I am using eth0 for lan and eth1 and eth2 for internet connections. Everything works great in my Ubuntu-box, but over nat routes do not work as they should. I cannot understand what's wrong. I post everything you need to help me solve my problem.

My problem in short is that I cannot access http-feeds from my ie7 or firefox if I am using computer behind nat. But everything works like a charm in my Ubuntu box. I am **NOT LOOKING** for bond instructions for my server. I just need simple way to route few ip-ranges to eth1. By default everything should be moving with eth2 to internet. IPV6 is disabled (or I think so).

eth0: Static lan ip address range 192.168.0.0/24. DHCP server installed, DNS-server installed.
eth1: Dhcp internet connection for university.
eth2: Static wan ip address.

iptables:
# Delete all rules
iptables -F
iptables -t nat -F

# Delete all chains
iptables -X
iptables -t nat -X

# Rules
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to-source (eth1 ip address)

# FTP
iptables -t nat -I PREROUTING -p tcp --dport 20 -j DNAT --to-destination 192.168.0.XXX:20
iptables -t nat -I PREROUTING -p tcp --dport 21 -j DNAT --to-destination 192.168.0.XXX:21
*
etc...
*
--------------------------------------
Routes:
#!/bin/sh
# Route tables
ip route flush table jyu
ip route flush table adsl

# ETH1 Connection
ip route add (eth1 ip gateway address) dev eth1 scope link src (eth1 ip address) table jyu
ip route add 130.234.192.0/22 dev eth1 proto kernel scope link src (eth1 ip address) table jyu
ip route add default via (eth1 ip gateway address) table jyu

# ETH2 Connection
ip route add (eth2 ip gateway address) dev eth2 scope link src (eth1 ip address) table adsl
ip route add 217.112.249.0/22 dev eth2 proto kernel scope link src (eth1 ip address) table adsl
ip
 route add default via (eth2 ip gateway address) table adsl

# Routes
ip route add 128.214.0.0/16 dev eth1 via (eth1 ip gateway address)  src (eth1 ip address)
*
*
*
etc..

#default routes
#ip route add default via (eth1 ip gateway address)
ip route add default via (eth2 ip gateway address)

# Routing rules

ip rule add from (eth2 ip address) table adsl
ip rule add from (eth1 ip address) table jyu

ip rule add to (eth2 ip address) table adsl
ip rule add to (eth1 ip address) table jyu

# Remove unnecessary routes
route del default gw (eth1 ip gateway address) dev eth1
route del default gw (lan ip gatewat address) dev eth0

---

### Post by elmeri on 2007-06-14
Anyone? Is my problem too mysterious?

---

### Post by startlinuxtoday on 2007-08-02
beyond me. but i did notice that you had a non-routeable ip in the mix. so if you are hoping to route an "unrequested query" to your non-route-able, forget it. if that's the case, you will have to use your browsers on the routeable ip's.

---

