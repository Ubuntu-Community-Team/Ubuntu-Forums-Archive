---
title: "3 network interfaces on same subnet-only works from boot with two interfaces enabled"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by linux_driver on 2014-11-24
I have s fairly simple Ubuntu 12 install on a Zotac.  the Zotac has two  on board network interfaces (eth0, eth1).  The are both set to DHCP.   they both work fine.  Now, when I add a TrendNet USB adapter as eth2  (static IP - 192.168.69.157), networking does not work (ie can't ping the  interfaces by ip).  ifconfig (see below) shows all adapters up.

here's the interesting part and hopefully of use to the experts out there.
When i ifconfig eth2 down, the networking works.
I can also execute ifconfig eth2 up, and networking still works.

ifconfig, netstat -rn, and /etc/network/interfaces are below

Thanks for any assistance!

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:2e:4c:af:3f
          inet addr:192.168.69.21  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe4c:af3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2301017 (2.3 MB)  TX bytes:27086 (27.0 KB)
          Interrupt:47

eth1      Link encap:Ethernet  HWaddr 00:01:2e:4c:af:40
          inet addr:192.168.69.18  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe4c:af40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2288141 (2.2 MB)  TX bytes:5748 (5.7 KB)
          Interrupt:48 Base address:0x2000

eth2      Link encap:Ethernet  HWaddr 00:14:d1:b0:d2:51
          inet addr:192.168.69.157  Bcast:192.168.69.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33250 (33.2 KB)  TX bytes:33250 (33.2 KB)

====================================
netstat -nr

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.69.1    0.0.0.0         UG        0 0          0 eth2
192.168.69.0    0.0.0.0         255.255.255.0   U         0 0          0 eth2
192.168.69.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.69.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1

==============================================
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet static
address 192.168.69.157
gateway 192.168.69.1
netmask 255.255.255.0

---

