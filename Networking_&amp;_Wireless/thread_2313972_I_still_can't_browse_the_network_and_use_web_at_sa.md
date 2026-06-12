---
title: "I still can't browse the network and use web at same time"
date: 2016-02-17
forum: Networking &amp; Wireless
---

### Post by Thomaz on 2016-02-17
How can I enable to use w/ both up like Windows ?
 WIFI (cable disconnected)
netstat -rn 
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções   MSS Janela  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp5s0
192.168.124.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0

$ ifconfig -a
enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.19.24.107  netmask 255.255.254.0  broadcast 172.19.25.255
        inet6 fe80::226:9eff:feb7:4309  prefixlen 64  scopeid 0x20<link>
        ether 00:26:9e:b7:43:09  txqueuelen 1000  (Ethernet)
        RX packets 159674  bytes 15326757 (14.6 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7574  bytes 651158 (635.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Loopback Local)
        RX packets 581  bytes 45380 (44.3 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 581  bytes 45380 (44.3 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.124.1  netmask 255.255.255.0  broadcast 192.168.124.255
        ether 52:54:00:3e:5a:f7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1  bytes 54 (54.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0-nic: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 52:54:00:3e:5a:f7  txqueuelen 500  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp5s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:d6:58:c5:d0  txqueuelen 1000  (Ethernet)
        RX packets 86348  bytes 61251657 (58.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 65477  bytes 11223667 (10.7 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


WIRED (Wifi off)
$ netstat -rn
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções   MSS Janela  irtt Iface
0.0.0.0         172.26.26.1     0.0.0.0         UG        0 0          0 enp8s0
172.19.24.0     0.0.0.0         255.255.254.0   U         0 0          0 enp8s0
172.26.26.1     0.0.0.0         255.255.255.255 UH        0 0          0 enp8s0
192.168.124.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0

$ ifconfig -a
enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.19.24.107  netmask 255.255.254.0  broadcast 172.19.25.255
        inet6 fe80::226:9eff:feb7:4309  prefixlen 64  scopeid 0x20<link>
        ether 00:26:9e:b7:43:09  txqueuelen 1000  (Ethernet)
        RX packets 159674  bytes 15326757 (14.6 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7574  bytes 651158 (635.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Loopback Local)
        RX packets 581  bytes 45380 (44.3 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 581  bytes 45380 (44.3 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.124.1  netmask 255.255.255.0  broadcast 192.168.124.255
        ether 52:54:00:3e:5a:f7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1  bytes 54 (54.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0-nic: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 52:54:00:3e:5a:f7  txqueuelen 500  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp5s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:d6:58:c5:d0  txqueuelen 1000  (Ethernet)
        RX packets 86348  bytes 61251657 (58.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 65477  bytes 11223667 (10.7 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

When cabled, can reach internal machines, butcant't navigate.
When wireless, the opposite.


Thanks

Because when I make clones, the user won't like, if has to change manually. Because Windows do it automatically now. The reason to choose UBUNTU is the Windows similarity.

---

### Post by newbie-user on 2016-02-18
From your routing info, it looks like you have two default routes to the Internet. That's generally not allowed unless you configure some advanced routing. See here: [http://www.rjsystems.nl/en/2100-adv-routing.php]("http://www.rjsystems.nl/en/2100-adv-routing.php")

---

