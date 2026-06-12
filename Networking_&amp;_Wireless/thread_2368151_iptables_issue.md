---
title: "iptables issue"
date: 2017-08-07
forum: Networking &amp; Wireless
---

### Post by Matthew_Swyrydenko on 2017-08-07
I've been struggling with this ever since I switched from Debian to Ubuntu...


I can reliably connect one machine (windows) to Ubuntu machine that connects to a VPN on a clients network.

When a second machine attempts to connect to the connection.  The first user drops their connection.

I've been having nothing but issues with this for a while.  I've determined it is an iptable issue.  But, I don't know what else to change to make this work properly.



sysctl -w net.ipv4.ip_forward=1

iptables -I FORWARD -i tun0 -o eth0 \
         -s 10.8.0.0/24 -d 192.168.0.0/24 \
         -m conntrack --ctstate NEW -j ACCEPT
 iptables -I FORWARD -i tun0 -o eth1 \
         -s 10.8.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
 iptables -I FORWARD -i eth0 -o eth1 \
         -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
 iptables -I FORWARD -m conntrack --ctstate RELATED,ESTABLISHED \
         -j ACCEPT
 iptables -t nat -I POSTROUTING -o eth1 \
          -s 10.8.0.0/24 -j MASQUERADE
 iptables -t nat -I POSTROUTING -o eth1 \
          -s 192.168.0.0/24 -j MASQUERADE

---

### Post by Matthew_Swyrydenko on 2017-08-10
Major change to above post

---

