---
title: "netplan 2nd if ip address (24.04 beta)"
date: 2024-04-21
forum: Networking &amp; Wireless
---

### Post by gerd-li on 2024-04-21
hi !

Im playing around with the actual beta (in 4 days its official)
i have 2 ethernet devices, i setup one which is working which also includes default gateway. Now i want to add a 2nd segment and i made setup in netplan regarding Docu.
netplann generate neither netplan apply croaks in debug mode for any failue but the 2nd ip address does not appear on the interface.

the netplan config
```
network:
    ethernets:
        enp1s0:
            addresses:
            - 192.168.1.2/24
        enp2s0:
            addresses:
            - 192.168.63.251/24
            nameservers:
             search: [domain.tld]
             addresses: [192.168.63.1, 192.168.63.254]
            routes:
              - to: default
                via: 192.168.63.254
 version: 2

```

but ip address for enp1s0 is not set

```
enp1s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:d0:b4:02:40:24  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0x80e00000-80efffff

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.63.251  netmask 255.255.255.0  broadcast 192.168.63.255
        inet6 fe80::2d0:b4ff:fe02:4025  prefixlen 64  scopeid 0x20<link>
        ether 00:d0:b4:02:40:25  txqueuelen 1000  (Ethernet)
        RX packets 1888295  bytes 1372768091 (1.3 GB)
        RX errors 0  dropped 224009  overruns 0  frame 0
        TX packets 498157  bytes 136051635 (136.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0x80b00000-80bfffff

```

Did i missed an entry ?

Ciaso Gerd

---

