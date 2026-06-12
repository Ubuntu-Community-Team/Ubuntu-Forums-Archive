---
title: "DHCPv6 DECLINE not working"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by emmy2 on 2014-08-15
Hi,

I am trying to test a functionality of a DHCPv6 server that when it receives a DHCPv6 DECLINE message, it responds with a REPLY and then ADVERTISE a different IPv6 address to its client. I setup a topology with one DHCPv6 server and two Ubuntu hosts running 12.04. Initially, both get IPv6 global address from the DHCP server (e.g. Host A gets address x and host B gets address y). 

I unplugged a cable from host A and assigned a static address x to host B. When I reconnected host A to the network, it performed DAD - host A sent NS for address x and host B sent NA for address x. At this point, host A should have sent a DECLINE message since it detected a duplicated address. However, host A seems to ignore it and uses address x anyway. I replaced host A with a Windows 7 machine and repeated the same steps. Windows 7 host did send DHCPv6 DECLINE and got a different IPv6 address from the DHCPv6 server. I am new to Ubuntu and was wondering if I have to change anything on the sysctl.conf to make Ubuntu host works properly for IPv6 DAD? 

Thank you so much,

Emmy

---

