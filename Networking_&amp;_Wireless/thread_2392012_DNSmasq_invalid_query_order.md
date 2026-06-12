---
title: "DNSmasq invalid query order"
date: 2018-05-15
forum: Networking &amp; Wireless
---

### Post by pczekalski on 2018-05-15
Hello everyone,

I'm experiencing the problem with dnsmasq with invalid DNS querying order.

The following is a configuration (Ubuntu & QNAP <->(192.168.1.1 - private network, behind NAT) [Mikrotik Router] (188.x.x.x - public IP)<->Internet.
- Mikrotik Router has DNS serwer on the 192.168.1.1, resolving "somednsname" to 192.168.1.18 (QNAP). QNAP is also exposed via port forwarding from private to public IP through the router and visible on the public IP 188.x.x.x - there is another DNS server (OVH, public) resolving "somednsname".

Windows, and "not dnsmasq" machines on my private network work well, resolving "somednsname" to 192.168.1.18 when in private network. 
Problem is with with Ubuntu machine (18.04, formerly 17.10) running dnsmasq- instead of querying local DNS on router, it queries OVH DNS thus obtains "188.x.x.x" instead of local address.

Is there any method to force dnsquery local server first?

Problem is with SSL certificates: to access from under Ubuntu when in private network, my QNAP server I need to force URL via IP, instead of via domain name, thus it causes SSL error.

Regards,

Piotr

---

### Post by ralen1225 on 2018-05-23
I am curious. What is your need for dnsmasq? I tried it out when I decided to route my internet through my ubuntu machine, but removed it and opted for bind9 and isc-dhcpd instead. I found both to be easier to configure and manage.

---

