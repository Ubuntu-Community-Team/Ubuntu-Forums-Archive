---
title: "Proxy-arp not working"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by ricardobarbosa on 2013-10-10
Hi all,

I am deploy router with features proxy-arp, but not working. This follow settings.

echo 1 > /proc/sys/net/ipv4/all/proxy_arp
echo 1 > /proc/sys/net/ipv4/eth0/proxy_arp
echo 1 > /proc/sys/net/ipv4/eth1/proxy_arp

This tcpdump not seen response for arp request

17:41:15.262145 ARP, Request who-has 172.16.200.3 tell 172.16.200.2, length 46
17:41:16.262597 ARP, Request who-has 172.16.200.3 tell 172.16.200.2, length 46
17:41:17.264265 ARP, Request who-has 172.16.200.3 tell 172.16.200.2, length 46


Anyone, any idea?

Regards.

---

