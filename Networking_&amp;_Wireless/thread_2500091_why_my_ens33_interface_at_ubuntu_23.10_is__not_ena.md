---
title: "why my ens33 interface at ubuntu 23.10 is  not enabled  as boot"
date: 2024-08-22
forum: Networking &amp; Wireless
---

### Post by alex5956 on 2024-08-22
hello,
why my ens33 interface at ubuntu 23.10 boot and as kernel: 6.9.9-060909-generic
 is not enabled on my vmware 16.x machine with vmware wokstation 17.x? : ```
ens33: flags=4419<UP,BROADCAST,RUNNING,PROMISC,MULTICAST>  mtu 1500
        inet 192.168.1.48 netmask 255.255.255.0 diffusion 192.168.1.255
        ether 00:0c:29:8b:91:22 txqueuelen 1000  (Ethernet)
        RX 1188539 bytes 1620041574 (1.6 GB) Packages
        RX errors 0 overruns of 1580 deleted 0 frame 0
        TX Packages 28792 bytes 3494784 (3.4 MB)
        Errors TX 0 Fall 0 Overruns 0 Carrier 0 Collisions 0

ens37: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  1500 mtu
        inet 192.168.1.36 netmask 255.255.255.0 broadcast 192.168.1.255
        ether 00:0c:29:8b:91:2c txqueuelen 1000  (Ethernet)
        RX 137316 bytes 148649057 (148.6 Mo) packages
        RX errors 0 overruns of 976 deleted 0 frame 0
        TX Packages 37846 bytes 16826331 (16.8 MB)
        Errors TX 0 Fall 0 Overruns 0 Carrier 0 Collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1 netmask 255.0.0.0.0
        inet6::1 prefixlen 128 scopeid 0x10<host>
        loop txqueuelen 1000  (local loop)
        Packages RX 88316 bytes 11370208 (11.3 MB)
        Errors RX 0 Drop 0 Overshoot 0 Frame 0
        Packages TX 88316 bytes 11370208 (11.3 MB)
        Errors TX 0 Fall 0 Overruns 0 Carrier 0 Collisions 0
```


```
alexandre@alexandre-developpeur:/opt/Qt$ nmcli --version
outil nmcli, version 1.44.2
alexandre@alexandre-developpeur:/opt/Qt$ NetworkManager --version
1.44.2
alexandre@alexandre-developpeur:/opt/Qt$ 

```
Regards

---

### Post by currentshaft on 2024-08-22
bin

---

