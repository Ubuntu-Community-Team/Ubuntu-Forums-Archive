---
title: "iptables and IGMP/Multicast"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by ah6511 on 2007-11-15
Hi,

I am new to Ubuntu/Linux. I have a Ubuntu gateway, eth0 connects to Corp network, eth1 connects to local subnet, and I used following script to enable IP forwarding:

iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
 
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface tun0 -j ACCEPT
 
echo 1 > /proc/sys/net/ipv4/ip_forward

But when one computer on the local subnet tries to join multicast group to receive multicast data, the IGMP packet is never forwarded to eth0. Any specific thing I need to do? TIA.

---

