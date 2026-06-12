---
title: "vnc networking iptables no longer working for me."
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by ulao3 on 2017-02-11
I have a new network set up. All inbound and out bound traffic to the net is on eth3. All internal traffic is 192.168/.. is on eth0

I had a script for my tables for my old set up (eth0 and eth0:1) but was using a virtual card. Now that I have it on my new set up the vnc portion is not working right. 


iptables -t nat -A POSTROUTING -o eth3  -j MASQUERADE
iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

echo 1 > /proc/sys/net/ipv4/ip_forward


iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 5925 -j DNAT --to-destination 192.168.0.25:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 5927 -j DNAT --to-destination 192.168.0.27:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 5929 -j DNAT --to-destination 192.168.0.29:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 5931 -j DNAT --to-destination 192.168.0.31:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 5910 -j DNAT --to-destination 192.168.0.10:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 5921 -j DNAT --to-destination 192.168.0.21:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 59137 -j DNAT --to-destination 192.168.0.137:5900
iptables -t nat -A PREROUTING -i eth3 -p tcp --dport 59110 -j DNAT --to-destination 192.168.0.110:5900

Anyone see something I missed here?

---

