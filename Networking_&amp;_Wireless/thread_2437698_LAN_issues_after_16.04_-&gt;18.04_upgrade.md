---
title: "LAN issues after 16.04 -&gt;18.04 upgrade"
date: 2020-02-27
forum: Networking &amp; Wireless
---

### Post by moldiver on 2020-02-27
After upgrading from 16.04 to 18.04, I had wired network issues.  I fixed it and now I have Internet.  However I can't see other machines on my LAN and vice versa.  No issues pre upgrade.  I checked the routing and ufw and that does not seem to be the issue.  Any help is appreciated.  Below are some outputs for diagnostics.

```
$ ifconfig -a
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.50  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::230:67ff:fed5:6000  prefixlen 64  scopeid 0x20<link>
        ether xx:xx:xx:xx:xx:xx  txqueuelen 1000  (Ethernet)
        RX packets 312  bytes 82309 (82.3 KB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 298  bytes 35138 (35.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 50  bytes 4833 (4.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 50  bytes 4833 (4.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```


```
$ sudo ip route show
default via 192.168.2.1 dev enp2s0 onlink 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.2.0/24 dev enp2s0 proto kernel scope link src 192.168.2.50 
```

```
$ ping 192.168.2.59
PING 192.168.2.59 (192.168.2.59) 56(84) bytes of data.
From 192.168.2.50 icmp_seq=1 Destination Port Unreachable
From 192.168.2.50 icmp_seq=2 Destination Port Unreachable
From 192.168.2.50 icmp_seq=3 Destination Port Unreachable
```

```
$ sudo ufw status

Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
443                        ALLOW       Anywhere                  
Anywhere                   ALLOW       192.168.2.0/24
```

---

### Post by wildmanne39 on 2020-02-27
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

