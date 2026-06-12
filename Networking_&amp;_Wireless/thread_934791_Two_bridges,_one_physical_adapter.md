---
title: "Two bridges, one physical adapter?"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by OmahaVike on 2008-10-01
any and all help is greatly appreciated in advance.

i'm attempting to simulate a three tier architecture while being disconnected from a corporate network using virtualbox. the host being the presentation server (php), a virtualized middle biz logic server(soap), and a virtualized data server. all are running ubuntu server. thus, i'm seeking to have two virtual machines running on the host, but bridging off the same network interface -- and having all three (host, vm1, vm2) being able to communicate while not being hooked up to a network.

i have bridged the middle server vm and have it working well. when i tried to add in a bridge for the 2nd server, under br1, i'm getting a notice that eth0 is already bridged to br0 and can't enslave it to the new br1.

is there any way around this, so that i can bridge two vm's to the same host network interface? 

vinaka!

---

