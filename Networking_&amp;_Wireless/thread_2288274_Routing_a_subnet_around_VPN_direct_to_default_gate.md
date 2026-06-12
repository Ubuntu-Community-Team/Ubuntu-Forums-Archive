---
title: "Routing a subnet around VPN direct to default gateway"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by Frozen Forest on 2015-07-25
I connected to a commercial VPN for which all traffic is routed, the system does also forward traffic from a subnet this traffic from the subnet are currently routed through the VPN.

What I which to happen is that all the network from the subnet get routed directly to the default gateway, bypassing the VPN.

Found these two guides but does not understand exactly how to combine it
[http://superuser.com/questions/376667/how-to-route-only-specific-subnet-source-ip-to-a-particular-interface](http://superuser.com/questions/376667/how-to-route-only-specific-subnet-source-ip-to-a-particular-interface)
[http://serverfault.com/questions/487468/bypass-openvpn-for-particular-ip](http://serverfault.com/questions/487468/bypass-openvpn-for-particular-ip)

How do I route the subnet through the default gateway, the default gateway is 192.168.1.1, subnet is 172.16.0.0/16

I tried this command but this wont use the gateway
ip rule add from 172.16.0.0/16 table main
ip route add 172.16.0.0/16 table main dev eth0

---

### Post by Frozen Forest on 2015-07-26
[http://blog.scottlowe.org/2013/05/29/a-quick-introduction-to-linux-policy-routing/](http://blog.scottlowe.org/2013/05/29/a-quick-introduction-to-linux-policy-routing/)

Explains how to solve it

---

