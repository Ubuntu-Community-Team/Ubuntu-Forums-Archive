---
title: "Network disconnectes randomly ubutnu 18.10"
date: 2018-12-30
forum: Networking &amp; Wireless
---

### Post by kevinred112 on 2018-12-30
Hi, I am a relatively new guy in networking scenarios in ubuntu.

My ethernet connection loose its connections randomly after some time, i dont know why this is happening.

here is my content of the `\etc\network\interfaces`
> # interfaces(5) file used by ifup(8) and ifdown(8)
# auto lo
# iface lo inet loopback
auto eth0
iface eth0 inet dhcp


and this is my `ifconfig` content
```
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:9c:f3:09:e4  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.252  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::e269:95ff:fe91:55f5  prefixlen 64  scopeid 0x20<link>
        ether e0:69:95:91:55:f5  txqueuelen 1000  (Ethernet)
        RX packets 66029  bytes 81768072 (81.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 47921  bytes 5369066 (5.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xfe600000-fe620000  


enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:0a:eb:68:18:a2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 9170  bytes 715878 (715.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9170  bytes 715878 (715.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:82:1b:57  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```



if anytrhing else is needed please tell me, i don't know how to fix this issue, please help

---

### Post by praseodym on 2018-12-31
Hi, revert the changes of that file:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot.

---

