---
title: "Default Route from class b to class c network"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by ibizatunes on 2015-08-22
Basically I want to pass all traffic from 172.16.1.2 eth1    to     192.168.0.1  eth0
172.16.1.2 is the ip address of eth1
192.168.0.1 is my internet connected router connected on eth0

```
sudo route add -net 172.16.0.0 netmask 255.255.0.0 gw 192.168.0.1 eth0
```

As soon as run the above command i cant ping my switch on the network address 172.16.1.1

I also want the route to last after reboot also


Current Route = 
172.16.0.0      *               255.255.0.0     U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0

---

