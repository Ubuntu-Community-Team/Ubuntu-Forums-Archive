---
title: "Two interfaces, one of them bridged. Strange behavior of DHCP and ARP"
date: 2016-01-18
forum: Networking &amp; Wireless
---

### Post by kurnosem on 2016-01-18
I have an Ubuntu Server with this config:
```

$ lspci -D | grep -i ether
0000:01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe
0000:01:00.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5720 Gigabit Ethernet PCIe

```

Interfaces
```

$ cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports em1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0


auto em2
iface em2 inet dhcp

```

ifconfig:
```

administrador@panzer:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr f8:bc:12:41:54:2c
          inet addr:10.105.3.174  Bcast:10.105.3.255  Mask:255.255.252.0
          inet6 addr: fe80::fabc:12ff:fe41:542c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77789991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41390779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:84304733531 (84.3 GB)  TX bytes:6216347836 (6.2 GB)

em1       Link encap:Ethernet  HWaddr f8:bc:12:41:54:2c
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29384966 errors:5 dropped:0 overruns:0 frame:3
          TX packets:13576438 errors:334 dropped:0 overruns:0 carrier:0
          collisions:1355756 txqueuelen:1000
          RX bytes:12093830764 (12.0 GB)  TX bytes:3537483510 (3.5 GB)
          Interrupt:16

em2       Link encap:Ethernet  HWaddr f8:bc:12:41:54:2e
          inet addr:10.105.2.85  Bcast:10.105.3.255  Mask:255.255.252.0
          inet6 addr: fe80::fabc:12ff:fe41:542e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10255179 errors:1 dropped:0 overruns:0 frame:2
          TX packets:4216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:958268827 (958.2 MB)  TX bytes:1440078 (1.4 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:395676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:395676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:87588921 (87.5 MB)  TX bytes:87588921 (87.5 MB)

tap0      Link encap:Ethernet  HWaddr f6:8f:c2:4d:0c:80
          inet addr:192.168.100.155  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::f48f:c2ff:fe4d:c80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:9332346 (9.3 MB)  TX bytes:197915 (197.9 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:5a:59:c3
          inet6 addr: fe80::fc54:ff:fe5a:59c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67431218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57786593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:83832715432 (83.8 GB)  TX bytes:13897618779 (13.8 GB)



```

In the ifconfig the "collisions" are really high. The problem is that sometimes we lost connection to interface with IP 10.105.2.85 and I don't know why, the connection is lost for small period of time of some minutes. The other problem is that if I list the arp list in any other computer the result is:
```

C:\Users\ufd>arp -a|findstr /R /C:"f8-bc-12"
  10.105.2.85           f8-bc-12-41-54-2c     dynamic
  10.105.3.174          f8-bc-12-41-54-2c     dynamic

```

The MAC is the same for both!

---

