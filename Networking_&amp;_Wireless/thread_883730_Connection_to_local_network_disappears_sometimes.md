---
title: "Connection to local network disappears sometimes"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by wl2776 on 2008-08-08
Kubuntu 8.04.1

Sometimes pings don't go to hosts on a local network.
ping just sits and waits for something, and doesn't display anything.

At the same time pings to the hosts on the internet go succsessfully.
That has begun recently after I have configured host networking for Windows XP running in VirtualBox.

Changing from host networking back to NAT in the VirtualBox didn't help.
Removing bridge-utils and uml-utilities also didn't help. Instead I have lost almost all connectivity.

Also, I don't use NetworkManager, it was removed a long time ago.

Here are some commands showing my system configuration: 

```
$ cat /etc/network/interfaces
auto lo eth0

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet manual

auto tap0
iface tap0 inet manual
tunctl_user wl
uml_proxy_arp wl.company-domain.ru
uml_proxy_ether eth0

auto br0
iface br0 inet dhcp
bridge_ports eth0 tap0
bridge_maxwait 0

$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:1b:78:a9:7e:3b
          inet addr:192.168.24.130  Bcast:192.168.24.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5832108 (5.5 MB)  TX bytes:1415234 (1.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:1b:78:a9:7e:3b
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6530506 (6.2 MB)  TX bytes:1486104 (1.4 MB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28578 (27.9 KB)  TX bytes:28578 (27.9 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:c5:4c:15:ae
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14922 errors:0 dropped:217 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:25282 (24.6 KB)  TX bytes:1400214 (1.3 MB)
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localhost       *               255.255.255.255 UH    0      0        0 tap0
192.168.24.0    *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         192.168.24.1    0.0.0.0         UG    100    0        0 br0

$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
127.0.0.1       0.0.0.0         255.255.255.255 UH        0 0          0 tap0
192.168.24.0    0.0.0.0         255.255.255.0   U         0 0          0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 br0
0.0.0.0         192.168.24.1    0.0.0.0         UG        0 0          0 br0


```

If I call route during that connect disappearing, it displays first 3 lines and waits for something instead of printing default gateway information.

netstat -nr prints everything without delays.

What's the problem?

---

