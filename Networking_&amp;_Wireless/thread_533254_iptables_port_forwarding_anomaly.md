---
title: "iptables port forwarding anomaly"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by poncenby on 2007-08-23
2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

I have 1 in /proc/sys/net/ipv4/ip_forward

i have these rules for iptables

iptables -A PREROUTING -t nat -i eth1 -p udp --dport 9999 -j DNAT --to 172.16.103.128:9999
iptables -A INPUT -p udp -m state --state NEW --dport 9999 -i eth1 -j ACCEPT

i run tcpdump on the interface receiving the udp packets and can see all udp packets and a corresponding icmp port unreachable.
i run tcpdump of the second interface and can see no udp traffic.
i can ping the second interface from the first.

can anyone see why the traffic is not being forwarded between interfaces?

i know it's a wild stab in the dark but any ideas would be appreciated.

thanks

---

