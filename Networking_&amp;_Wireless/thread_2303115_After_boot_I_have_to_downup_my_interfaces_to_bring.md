---
title: "After boot I have to down/up my interfaces to bring them up"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by matthew121 on 2015-11-16
I have a slightly special setup (open stack setup) but what is happening on boot I have to log in to the serial port then do ifconfig eth0-5 down/up to bring the interfaces up.

Here is my etc/network/interfaces output :

```
root@aioc:/etc/network# more interfaces
auto lo
iface lo inet loopback

allow-hot-plug eth0
auto eth0
iface eth0 inet manual
        pre-up ip link set $IFACE up
        pre-down ip link set $IFACE down

allow-hot-plug eth1
auto eth1
iface eth1 inet manual
        pre-up ip link set $IFACE up
        pre-down ip link set $IFACE down

allow-hot-plug eth2
auto eth2
iface eth2 inet manual
        pre-up ip link set $IFACE up
        pre-down ip link set $IFACE down

allow-hot-plug eth3
auto eth3
iface eth3 inet manual
        pre-up ip link set $IFACE up
        pre-down ip link set $IFACE down

allow-hot-plug eth4
auto eth4
iface eth4 inet manual
        pre-up ip link set $IFACE up
        pre-down ip link set $IFACE down

allow-hot-plug eth5
auto eth5
iface eth5 inet manual
        pre-up ip link set $IFACE up
        pre-down ip link set $IFACE down



auto mng
iface mng inet dhcp
        bridge_ports eth0
        bridge_maxwait 0

auto os_control
iface os_control inet static
        bridge_ports pnid.i.3 os_control.i eth1
        bridge_maxwait 0
        address 192.168.0.11
        netmask 255.255.255.0
        pre-up /root/bin/all-in-one/connectivity.sh
        post-up ip route add 192.168.0.128/25 via 192.168.0.50;

auto os_control:0
iface os_control:0 inet static
        address 192.168.0.1
        netmask 255.255.255.0

auto pnid_mng
iface pnid_mng inet static
        bridge_ports eth2 eth3
        bridge_maxwait 0
        address 192.168.2.1
        netmask 255.255.255.0


```

output of ifconfig -a
```

root@aioc:/etc/network# ifconfig -a
br-acc    Link encap:Ethernet  HWaddr 4a:1a:78:e0:92:4d
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14291 (14.2 KB)  TX bytes:0 (0.0 B)

br-ex     Link encap:Ethernet  HWaddr 6a:1c:17:a0:55:4d
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:1150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:119063 (119.0 KB)  TX bytes:672 (672.0 B)

br-int    Link encap:Ethernet  HWaddr de:5a:b5:66:53:4b
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br-mng    Link encap:Ethernet  HWaddr 92:79:16:55:81:4e
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14291 (14.2 KB)  TX bytes:0 (0.0 B)

br-net    Link encap:Ethernet  HWaddr 7e:03:41:60:79:4b
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 44:a8:42:35:07:37
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 44:a8:42:35:07:38
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:141995 (141.9 KB)  TX bytes:196797 (196.7 KB)
          Interrupt:19

eth2      Link encap:Ethernet  HWaddr 44:a8:42:35:07:39
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5583 (5.5 KB)  TX bytes:0 (0.0 B)
          Interrupt:19

eth3      Link encap:Ethernet  HWaddr 44:a8:42:35:07:3a
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7958 (7.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:16

eth4      Link encap:Ethernet  HWaddr 00:0a:f7:82:4f:a4
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:45130 (45.1 KB)  TX bytes:14030 (14.0 KB)
          Interrupt:32

eth5      Link encap:Ethernet  HWaddr 00:0a:f7:82:4f:a5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:36

eth6      Link encap:Ethernet  HWaddr 00:0a:f7:82:4f:1a
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40

eth7      Link encap:Ethernet  HWaddr 00:0a:f7:82:4f:1b
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44

host-acc  Link encap:Ethernet  HWaddr 00:0a:f7:82:4f:a4
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14291 (14.2 KB)  TX bytes:0 (0.0 B)

host-net  Link encap:Ethernet  HWaddr 02:63:8f:1d:f0:4e
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

int-br-acc Link encap:Ethernet  HWaddr b6:f8:48:1d:8f:a0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5068 (5.0 KB)  TX bytes:0 (0.0 B)

int-br-ex Link encap:Ethernet  HWaddr e6:f7:6a:37:2a:1c
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5016 (5.0 KB)  TX bytes:0 (0.0 B)

int-br-mng Link encap:Ethernet  HWaddr e6:4b:a8:63:68:c3
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5068 (5.0 KB)  TX bytes:0 (0.0 B)

int-br-net Link encap:Ethernet  HWaddr 52:62:a6:7c:3b:93
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6184054 (6.1 MB)  TX bytes:6184054 (6.1 MB)

mng       Link encap:Ethernet  HWaddr 44:a8:42:35:07:37
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mng:avahi Link encap:Ethernet  HWaddr 44:a8:42:35:07:37
          inet addr:169.254.3.251  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

os_control Link encap:Ethernet  HWaddr 44:a8:42:35:07:38
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:67027 (67.0 KB)  TX bytes:201164 (201.1 KB)

os_control:0 Link encap:Ethernet  HWaddr 44:a8:42:35:07:38
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

os_control.e Link encap:Ethernet  HWaddr a6:f6:a5:a2:74:c5
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:119291 (119.2 KB)  TX bytes:672 (672.0 B)

os_control.i Link encap:Ethernet  HWaddr 7e:ad:29:a7:d2:cb
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:672 (672.0 B)  TX bytes:119291 (119.2 KB)

ovs-system Link encap:Ethernet  HWaddr 0e:ca:04:ed:63:2e
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

phy-br-acc Link encap:Ethernet  HWaddr fa:c3:d5:95:3f:ef
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5068 (5.0 KB)

phy-br-ex Link encap:Ethernet  HWaddr 16:d6:30:9a:e1:72
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5016 (5.0 KB)

phy-br-mng Link encap:Ethernet  HWaddr ca:9b:ff:d6:6b:83
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5068 (5.0 KB)

phy-br-net Link encap:Ethernet  HWaddr 4e:17:7d:fd:53:82
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pnid.e    Link encap:Ethernet  HWaddr 56:2a:f7:c8:e7:b3
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24894 (24.8 KB)  TX bytes:43518 (43.5 KB)

pnid.i    Link encap:Ethernet  HWaddr ae:88:64:71:b9:6e
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43518 (43.5 KB)  TX bytes:24894 (24.8 KB)

pnid.i.3  Link encap:Ethernet  HWaddr ae:88:64:71:b9:6e
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40488 (40.4 KB)  TX bytes:24894 (24.8 KB)

virbr0    Link encap:Ethernet  HWaddr ee:ff:6b:50:89:b4
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```

root@aioc:/etc/network# sudo lshw -C network
PCI (sysfs)

```

---

### Post by matthew121 on 2015-11-16
root@aioc:~# lspci -nn | grep -i eth
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
02:00.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
03:00.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
04:00.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]
05:00.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe [14e4:165f]

---

### Post by matthew121 on 2015-11-19
Anyone or have I found a new way to break stuff permanently :D?

---

### Post by matthew121 on 2015-11-21
anyone?  I'm pretty stuck here.

---

### Post by Noelinho on 2015-11-21
Came across this when looking for possible solutions to a problem I was having earlier. Your setup is a bit more involved, but it seems to be essentially the same problem. Perhaps a read of the [to and fro in this thread]("http://ubuntuforums.org/showthread.php?t=2303750") may help you? It doesn't get to the bottom of what's causing it, but I got to the point where I had nowhere else I knew where to look!

---

