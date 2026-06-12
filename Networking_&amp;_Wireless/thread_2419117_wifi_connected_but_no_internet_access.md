---
title: "wifi connected but no internet access"
date: 2019-05-16
forum: Networking &amp; Wireless
---

### Post by abalushyno1 on 2019-05-16
hi i installed ubuntu for personal use. but i am having issues with  internet connectivity in ubuntu. i am connected through wifi and  internet gets disconnected every other minute. tried some tricks  suggested in other threads like disabling ipv6 and others. nothing seems  to work. and i am using same internet on my other devices like smart  phone . there wifi seems to work fine and also i am using ubuntu and  windows on same laptop, in windows its also working fine.

here are some details of my network interface

**lspci -nn | grep 0280**

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]

**ifconfig**

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 2c:27:d7:c4:8e:bc  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5680  bytes 563836 (563.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5680  bytes 563836 (563.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.104  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::21e:64ff:fe09:85cc  prefixlen 64  scopeid 0x20<link>
        ether 00:1e:64:09:85:cc  txqueuelen 1000  (Ethernet)
        RX packets 219328  bytes 306639193 (306.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 120816  bytes 13106941 (13.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[B]netstat -rn

[/B]Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlo1

---

