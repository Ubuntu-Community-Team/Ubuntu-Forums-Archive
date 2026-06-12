---
title: "Cannot ping router from Ubuntu 20.04, can access internet."
date: 2023-09-24
forum: Networking &amp; Wireless
---

### Post by rezendes on 2023-09-24
[COLOR=#D0CCC6][FONT=&amp]I cannot ping my router's ip from my Ubuntu 20.04 machine but I can access the internet from it. My other windows machines on the network Cannot ping the Ubuntu machine's ip but they Can ping the router's ip. UFW is disabled. Some of the other network stuff is from Docker and Virtual Machine.
[/FONT][/COLOR]
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp7s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 virbr0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 lxcbr0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp7s0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
ip r
default via 192.168.1.254 dev enp7s0 proto dhcp metric 100 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 
192.168.1.0/24 dev lxcbr0 proto kernel scope link src 192.168.1.64 linkdown 
192.168.1.0/24 dev enp7s0 proto kernel scope link src 192.168.1.90 metric 100 
192.168.100.0/24 dev virbr0 proto kernel scope link src 192.168.100.1 linkdown 
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp7s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether d0:50:99:d0:1d:4b brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.90/24 brd 192.168.1.255 scope global dynamic noprefixroute enp7s0
       valid_lft 85693sec preferred_lft 85693sec
    inet6 2600:1700:5ac1:4d90::49/128 scope global dynamic noprefixroute 
       valid_lft 2897sec preferred_lft 2897sec
    inet6 2600:1700:5ac1:4d90:2c69:c0b4:6494:ffe1/64 scope global temporary dynamic 
       valid_lft 3171sec preferred_lft 3171sec
    inet6 2600:1700:5ac1:4d90:6c2b:da86:1f80:4688/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3171sec preferred_lft 3171sec
    inet6 fe80::4ee3:45c8:948:8ffe/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:b7:01:dc brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.1/24 brd 192.168.100.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:b7:01:dc brd ff:ff:ff:ff:ff:ff
5: lxcbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 00:16:3e:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.64/24 brd 192.168.1.255 scope global lxcbr0
       valid_lft forever preferred_lft forever
6: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:1b:42:8c:67 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:1bff:fe42:8c67/64 scope link 
       valid_lft forever preferred_lft forever
10: veth862d46f@if9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 7a:dd:74:31:26:0e brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::78dd:74ff:fe31:260e/64 scope link 
       valid_lft forever preferred_lft forever
16: vethfd3cf83@if15: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether ea:a8:7a:8a:db:cb brd ff:ff:ff:ff:ff:ff link-netnsid 2
    inet6 fe80::e8a8:7aff:fe8a:dbcb/64 scope link 
       valid_lft forever preferred_lft forever
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
ifconfig
docker0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        inet6 fe80::42:1bff:fe42:8c67  prefixlen 64  scopeid 0x20<link>
        ether 02:42:1b:42:8c:67  txqueuelen 0  (Ethernet)
        RX packets 280147341  bytes 382351977660 (382.3 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 128313437  bytes 30336506233 (30.3 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.90  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4ee3:45c8:948:8ffe  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1700:5ac1:4d90:6c2b:da86:1f80:4688  prefixlen 64  scopeid 0x0<global>
        inet6 2600:1700:5ac1:4d90:2c69:c0b4:6494:ffe1  prefixlen 64  scopeid 0x0<global>
        inet6 2600:1700:5ac1:4d90::49  prefixlen 128  scopeid 0x0<global>
        ether d0:50:99:d0:1d:4b  txqueuelen 1000  (Ethernet)
        RX packets 131044511  bytes 30751638500 (30.7 GB)
        RX errors 0  dropped 147907  overruns 0  frame 0
        TX packets 292466602  bytes 404479703137 (404.4 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xdf200000-df27ffff  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 13007  bytes 1344535 (1.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13007  bytes 1344535 (1.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lxcbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.1.64  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 00:16:3e:00:00:00  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

veth862d46f: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::78dd:74ff:fe31:260e  prefixlen 64  scopeid 0x20<link>
        ether 7a:dd:74:31:26:0e  txqueuelen 0  (Ethernet)
        RX packets 106  bytes 6852 (6.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6743  bytes 1332033 (1.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vethfd3cf83: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::e8a8:7aff:fe8a:dbcb  prefixlen 64  scopeid 0x20<link>
        ether ea:a8:7a:8a:db:cb  txqueuelen 0  (Ethernet)
        RX packets 246301107  bytes 341269771154 (341.2 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 119991124  bytes 29171299948 (29.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.100.1  netmask 255.255.255.0  broadcast 192.168.100.255
        ether 52:54:00:b7:01:dc  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
sudo nano /etc/netplan/01-network-manager-all.yaml
 Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
sudo nano /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
ip neighbor show
192.168.1.100 dev enp7s0 lladdr 04:42:1a:f1:33:6a STALE
192.168.1.100 dev lxcbr0  FAILED
192.168.1.66 dev lxcbr0  FAILED
192.168.1.72 dev lxcbr0  FAILED
172.17.0.2 dev docker0 lladdr 02:42:ac:11:00:02 REACHABLE
192.168.1.176 dev lxcbr0  FAILED
192.168.1.1 dev lxcbr0  FAILED
192.168.1.66 dev enp7s0 lladdr ac:12:03:71:52:73 STALE
192.168.1.68 dev lxcbr0  FAILED
192.168.1.108 dev lxcbr0  FAILED
192.168.1.254 dev lxcbr0  FAILED
172.17.0.3 dev docker0 lladdr 02:42:ac:11:00:03 STALE
192.168.1.123 dev lxcbr0  FAILED
192.168.1.90 dev lxcbr0  FAILED
192.168.1.183 dev lxcbr0  FAILED
192.168.1.103 dev lxcbr0  FAILED
192.168.1.254 dev enp7s0 lladdr 38:a0:67:cf:21:52 REACHABLE
192.168.1.70 dev lxcbr0  FAILED
2600:1700:5ac1:4d90::1 dev enp7s0 lladdr 38:a0:67:cf:21:52 router STALE
fe80::3aa0:67ff:fecf:2152 dev enp7s0 lladdr 38:a0:67:cf:21:52 router REACHABLE
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
sudo iptables -L -v -n
Chain INPUT (policy ACCEPT 4709 packets, 2757K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  lxcbr0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:53
    0     0 ACCEPT     udp  --  lxcbr0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:53
    0     0 ACCEPT     tcp  --  lxcbr0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:67
    0     0 ACCEPT     udp  --  lxcbr0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
 326K  128M LIBVIRT_INP  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 409M  411G DOCKER-USER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 409M  411G DOCKER-ISOLATION-STAGE-1  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 129M   29G ACCEPT     all  --  *      docker0  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
  241 13164 DOCKER     all  --  *      docker0  0.0.0.0/0            0.0.0.0/0           
 281M  383G ACCEPT     all  --  docker0 !docker0  0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  docker0 docker0  0.0.0.0/0            0.0.0.0/0           
    8   408 ACCEPT     all  --  *      lxcbr0  0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  lxcbr0 *       0.0.0.0/0            0.0.0.0/0           
    0     0 LIBVIRT_FWX  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LIBVIRT_FWI  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LIBVIRT_FWO  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 3227 packets, 921K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 174K   53M LIBVIRT_OUT  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain DOCKER (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   12   624 ACCEPT     tcp  --  !docker0 docker0  0.0.0.0/0            172.17.0.3           tcp dpt:9443
    0     0 ACCEPT     tcp  --  !docker0 docker0  0.0.0.0/0            172.17.0.3           tcp dpt:9000
    0     0 ACCEPT     tcp  --  !docker0 docker0  0.0.0.0/0            172.17.0.3           tcp dpt:8000
   90  4776 ACCEPT     tcp  --  !docker0 docker0  0.0.0.0/0            172.17.0.2           tcp dpt:9091

Chain DOCKER-ISOLATION-STAGE-1 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 281M  383G DOCKER-ISOLATION-STAGE-2  all  --  docker0 !docker0  0.0.0.0/0            0.0.0.0/0           
 409M  411G RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain DOCKER-ISOLATION-STAGE-2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      docker0  0.0.0.0/0            0.0.0.0/0           
 281M  383G RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain DOCKER-USER (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 409M  411G RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LIBVIRT_FWI (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      virbr0  0.0.0.0/0            192.168.100.0/24     ctstate RELATED,ESTABLISHED
    0     0 REJECT     all  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain LIBVIRT_FWO (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  virbr0 *       192.168.100.0/24     0.0.0.0/0           
    0     0 REJECT     all  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain LIBVIRT_FWX (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  virbr0 virbr0  0.0.0.0/0            0.0.0.0/0           

Chain LIBVIRT_INP (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:53
    0     0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:53
    0     0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:67

Chain LIBVIRT_OUT (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            udp dpt:53
    0     0 ACCEPT     tcp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            tcp dpt:53
    0     0 ACCEPT     udp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            udp dpt:68
    0     0 ACCEPT     tcp  --  *      virbr0  0.0.0.0/0            0.0.0.0/0            tcp dpt:68
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
sudo nano /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 1.1.1.1
nameserver 8.8.8.8
nameserver 127.0.0.53
search attlocal.net
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
lspci -k
07:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
    Subsystem: ASRock Incorporation I210 Gigabit Network Connection
    Kernel driver in use: igb
    Kernel modules: igb
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=16.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=15.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=17.5 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=16.0 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=57 time=18.1 ms
[COLOR=#D0CCC6][FONT=&amp]
[/FONT][/COLOR]
ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.64 icmp_seq=1 Destination Host Unreachable
From 192.168.1.64 icmp_seq=2 Destination Host Unreachable
From 192.168.1.64 icmp_seq=5 Destination Host Unreachable
From 192.168.1.64 icmp_seq=6 Destination Host Unreachable
From 192.168.1.64 icmp_seq=7 Destination Host Unreachable


*****RESOLVED******

Deleted lxcbr0 and now everything works as expected.


[LIST=1]
[*]brctl show
[*]ip link set lxcbr0 down
[*]brctl delbr lxcbr0
[/LIST]

---

