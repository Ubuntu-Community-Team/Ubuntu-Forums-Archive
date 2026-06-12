---
title: "Can't connect to wireless network during the first 5 minutes after powerup"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by bd@cb8be8510 on 2008-02-21
From time to time I don't get a connection to the wireless network after powerup. Then after approx. 5 minutes, the connection is ok.

route -n after powerup gives the following results :

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 rausb0 
0.0.0.0.0         0.0.0.0         U     1000   0        0 rausb0 

This is clearly wrong. I don't have a route to my gateway and the destination-address is wrong as well.

My ip-address is the address I obtained the last time. So my ip-address is ok.
ifconfig returns :

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0 

After a while, the connection can be established (approx. 5 to 10 minutes). From then onwards
the network is runnig fine.

route -n (if connection is established)

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 rausb0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 rausb0 

Any ideas to avoid the loss of connection after powerup? (It occurs approx. 1 time/3 powerups).
Thanks in advance for your advice.

---

### Post by bd@cb8be8510 on 2008-02-22
Under: System-->Administration-->Services, I disabled  the option **Multicast DNS Service Discovery**. This seems to help. It think that the avahi-daemon is using the address 169.254.0.0 and that in some cases it takes too long to obtain the ip-adress of the gateway involved? #-o.

---

