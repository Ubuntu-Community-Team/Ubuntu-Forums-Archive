---
title: "Ubuntu 20.04 wifi connects to accesspoint but not to network"
date: 2022-09-11
forum: Networking &amp; Wireless
---

### Post by hakelm on 2022-09-11
My laptop running  Ubuntu 20.04 suddenly lost network connection.
It connects to the accesspoint but neither to the local network or internet. If I try to used a wired connection via an USB-dongle or use a hotspot on my mobile I get the same behaviour.
It is some kind of software problem since networking works when I run Ubuntu from a live-USB.
Below the output from some commands.
Any help is appreciated.
H


ifconfig:


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2040  bytes 150190 (150.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2040  bytes 150190 (150.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.44  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 7c:7a:91:1c:51:47  txqueuelen 1000  (Ethernet)
        RX packets 2  bytes 304 (304.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5  bytes 498 (498.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

dmesg|grep wlp1s0:dmesg|grep wlp1s0:


[   22.105806] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[   34.840826] wlp1s0: authenticate with 10:da:43:ca:a3:8c
[   34.847484] wlp1s0: send auth to 10:da:43:ca:a3:8c (try 1/3)
[   34.850983] wlp1s0: authenticated
[   34.856040] wlp1s0: associate with 10:da:43:ca:a3:8c (try 1/3)
[   34.859226] wlp1s0: RX AssocResp from 10:da:43:ca:a3:8c (capab=0x11 status=0 aid=4)
[   34.870162] wlp1s0: associated
[   34.984824] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready




[   22.105806] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[   34.840826] wlp1s0: authenticate with 10:da:43:ca:a3:8c
[   34.847484] wlp1s0: send auth to 10:da:43:ca:a3:8c (try 1/3)
[   34.850983] wlp1s0: authenticated
[   34.856040] wlp1s0: associate with 10:da:43:ca:a3:8c (try 1/3)
[   34.859226] wlp1s0: RX AssocResp from 10:da:43:ca:a3:8c (capab=0x11 status=0 aid=4)
[   34.870162] wlp1s0: associated
[   34.984824] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready



resolv.conf:        
        nameserver 127.0.0.53
        options edns0 trust-ad
        search .

---

