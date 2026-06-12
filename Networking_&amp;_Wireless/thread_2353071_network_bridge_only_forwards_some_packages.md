---
title: "network bridge only forwards some packages"
date: 2017-02-18
forum: Networking &amp; Wireless
---

### Post by fritz7 on 2017-02-18
Hi folks,


I'm tring to bridge my "Intel 82598EB 10-Gigabit Dual Port" networkcard with onboard nics. The system is a HP DL380 G6 with Ubuntu Server 16.04.2 LTS (GNU/Linux 4.4.0-62-generic x86_64) installed.


my /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# enable jumbo packages (for bridge)
auto enp2s0f0
iface enp2s0f0 inet manual
    mtu 9000
auto enp2s0f1
iface enp2s0f1 inet manual
    mtu 9000
auto ens1f0
iface ens1f0 inet manual
    mtu 9000
auto ens1f1
iface ens1f1 inet manual
    mtu 9000
    
auto br0
iface br0 inet static
    bridge_ports enp2s0f0 enp2s0f1 ens1f1
    address 10.0.0.130
    netmask 255.255.255.0
    gateway 10.0.0.205
    dns-nameservers 8.8.8.8
    bridge_fd 5
    bridge_stp no   # unter Umständen auf 'yes' setzen - s.u.
# http://grapsus.net/blog/post/Fixing-Xen-RTNETLINK-answers%3A-File-exists-issue-with-ifup-on-Debian-when-using-network-bridge-and-static-IP
# fix to " RTNETLINK answers: file not found"
    pre-up ip addr flush dev br0 2> /dev/null || true

```


ens1f0 and ens1f1 are 10G interfaces
enp2s0f0 and enp2s0f1 are 1G onboard interfaces 


The bridge is not properly working neither for 1G copper to 1G copper nor for 1G copper to 10G SPF+. With wireshark I can capture broadcast packages (for example a Raspberry, my desktop,... which are connected to ens1f0 via a switch). Pinging the server is possible, however pinging different "bridge users" via the server/bridge or DHCP on "bridge ports" is not working.


I read the following article and googled a lot but i din't find any mistake
[http://www.microhowto.info/troubleshooting/troubleshooting_ethernet_bridging_on_linux.html](http://www.microhowto.info/troubleshooting/troubleshooting_ethernet_bridging_on_linux.html)


ip a
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp2s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc mq master br0 state UP group default qlen 1000
    link/ether 78:e7:d1:e5:db:e6 brd ff:ff:ff:ff:ff:ff
3: enp2s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc mq master br0 state UP group default qlen 1000
    link/ether 78:e7:d1:e5:db:e8 brd ff:ff:ff:ff:ff:ff
4: enp3s0f0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 78:e7:d1:e5:db:ea brd ff:ff:ff:ff:ff:ff
5: enp3s0f1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 78:e7:d1:e5:db:ec brd ff:ff:ff:ff:ff:ff
6: ens1f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 9000 qdisc mq state DOWN group default qlen 1000
    link/ether 00:1b:21:da:46:b1 brd ff:ff:ff:ff:ff:ff
7: ens1f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:1b:21:da:46:b0 brd ff:ff:ff:ff:ff:ff
9: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:60:f2:8d:dc brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 scope global docker0
       valid_lft forever preferred_lft forever
12: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c3:f0:79 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
13: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:c3:f0:79 brd ff:ff:ff:ff:ff:ff
19: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc noqueue state UP group default qlen 1000
    link/ether 00:1b:21:da:46:b0 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.130/24 brd 10.0.0.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::21b:21ff:feda:46b0/64 scope link
       valid_lft forever preferred_lft forever

```


brctl showstp br0
```

br0
 bridge id              8000.001b21da46b0
 designated root        8000.001b21da46b0
 root port                 0                    path cost                  0
 max age                  20.00                 bridge max age            20.00
 hello time                2.00                 bridge hello time          2.00
 forward delay             5.00                 bridge forward delay       5.00
 ageing time             300.00
 hello timer               0.00                 tcn timer                  0.00
 topology change timer     0.00                 gc timer                  16.18
 flags




enp2s0f0 (1)
 port id                8001                    state                forwarding
 designated root        8000.001b21da46b0       path cost                  4
 designated bridge      8000.001b21da46b0       message age timer          0.00
 designated port        8001                    forward delay timer        0.00
 designated cost           0                    hold timer                 0.00
 flags


enp2s0f1 (2)
 port id                8002                    state                forwarding
 designated root        8000.001b21da46b0       path cost                  4
 designated bridge      8000.001b21da46b0       message age timer          0.00
 designated port        8002                    forward delay timer        0.00
 designated cost           0                    hold timer                 0.00
 flags


ens1f1 (3)
 port id                8003                    state                forwarding
 designated root        8000.001b21da46b0       path cost                  2
 designated bridge      8000.001b21da46b0       message age timer          0.00
 designated port        8003                    forward delay timer        0.00
 designated cost           0                    hold timer                 0.00
 flags

```


brctl showmacs br0
```

port no mac addr                is local?       ageing timer
  1     xx:xx:xx:d2:22:94       no                40.29
  3     xx:xx:xx:58:3e:3e       no                 0.30 # this is my desktop 10G card
  1     xx:xx:xx:40:b7:54       no                99.96
  3     xx:xx:xx:da:46:b0       yes                0.00
  3     xx:xx:xx:da:46:b0       yes                0.00
  1     xx:xx:xx:00:07:0b       no                 7.91
  1     xx:xx:xx:00:08:0b       no               138.39
  1     xx:xx:xx:18:64:79       no                42.20
  1     xx:xx:xx:86:9e:a4       no               230.86
  1     xx:xx:xx:eb:6d:cf       no                 0.00
  1     xx:xx:xx:e5:db:e6       yes                0.00
  1     xx:xx:xx:e5:db:e6       yes                0.00
  2     xx:xx:xx:e5:db:e8       yes                0.00
  2     xx:xx:xx:e5:db:e8       yes                0.00
  2     xx:xx:xx:dc:43:58       no                 0.22
  1     xx:xx:xx:05:60:3a       no                 4.90
  1     xx:xx:xx:e3:d3:c3       no                90.64
  1     xx:xx:xx:5a:66:a8       no               214.57

```


sudo ebtables -t filter -L
```

[sudo] password for matthias:
Bridge table: filter


Bridge chain: INPUT, entries: 0, policy: ACCEPT


Bridge chain: FORWARD, entries: 0, policy: ACCEPT


Bridge chain: OUTPUT, entries: 0, policy: ACCEPT

```


sudo ethtool ens1f1
```

Settings for ens1f1:
        Supported ports: [ FIBRE ]
        Supported link modes:   10000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: No
        Advertised link modes:  10000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: 10000Mb/s
        Duplex: Full
        Port: Direct Attach Copper
        PHYAD: 0
        Transceiver: external
        Auto-negotiation: off
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

```


I'm very happy to hear tips for searching the error. Thx in advance!

---

