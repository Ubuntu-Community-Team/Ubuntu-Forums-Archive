---
title: "Chrome has access to the internet but the terminal and Firefox don't"
date: 2017-09-25
forum: Networking &amp; Wireless
---

### Post by razz47 on 2017-09-25
When I type ```
ping google.com
``` this is the response I get -> ```
ping: google.com: Name or service not known
``` 

So i tried the following but couldn't tell what the problem is, hope it helps

ifconfig
```
enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        ether 98:e7:f4:8d:aa:d7  txqueuelen 1000  (Ethernet)
        RX packets 55  bytes 6679 (6.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 146626  bytes 9173450 (9.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 146626  bytes 9173450 (9.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.7  netmask 255.255.255.0  broadcast 192.168.1.255
        ether cc:b0:da:7a:f8:03  txqueuelen 1000  (Ethernet)
        RX packets 26467  bytes 17837301 (17.8 MB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 22905  bytes 4003493 (4.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

ping 8.8.8.8
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=1330 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=1464 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=54 time=1932 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=54 time=1743 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=54 time=1409 ms
 64 bytes from 8.8.8.8: icmp_seq=7 ttl=54 time=1487 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=54 time=384 ms
^C
--- 8.8.8.8 ping statistics ---
10 packets transmitted, 7 received, 30% packet loss, time 9016ms
rtt min/avg/max/mdev = 384.956/1393.217/1932.504/454.806 ms, pipe 2



```


and I can't type ```
sudo apt update
``` it returns errors :s 

How do I fix this?

---

### Post by wildmanne39 on 2017-09-25
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags. 

Just saying it returns errors does not help us, we need them posted here.

Thanks

---

