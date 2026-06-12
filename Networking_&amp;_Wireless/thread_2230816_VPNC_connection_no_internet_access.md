---
title: "VPNC connection no internet access"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by luis-ssilva-1978 on 2014-06-21
Hi there,

I used vpnc to connect to a cisco vpn server and I was unable to access internet when connection is started.
I access to lan without a problem .
The routing table before connection is :

Here I can access to internet without problem
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         100.10.20.1          0.0.0.0     UG    100    0        0 eth1
100.0.0.0        *               255.255.255.0   U     0      0        0 eth1
100.0.0.0        *               255.255.255.0   U     0      0        0 eth0


The routing table after connection:

Here I cannot connect to internet.



Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *                      0.0.0.0         U     0      0        0 tun0
default         100.10.20.1      0.0.0.0         UG    100    0        0 eth1
10.0.0.0        *                    255.255.255.0   U     0      0        0 eth1
10.0.0.0        *                    255.255.255.0   U     0      0        0 eth0
192.168.0.10    100.10.20.1     255.255.255.255 UGH   0      0        0 eth0

---

