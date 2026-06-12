---
title: "Two ethernet cards and virtual networking"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by carlosalvatore on 2008-06-04
Hi there!

I have added an Ethernet PCI Card because i want to use it to connect my Virtualbox to the internet.
I know i can do it with my existing ethernet card using a bridge.
The fact is that wasn't working.

My actual /etc/network/interfaces file:

[QUOTE="/etc/network/interfaces"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
  iface lo inet loopback

# The primary network interface
auto eth0
  iface eth0 inet dhcp

# The secondary network interface
auto eth1
  iface eth1 inet dhcp

# The Tunnel ap                                   
#auto tap0
#  iface tap0 inet manual
#   tunctl_user carlosalvatore    <<-- carlosalvatore is my user name (i guess it's obvious, but... you never knows ;p) 
#   uml_proxy_arp 195.165.0.3   <<-- This is the IP assigned via DCHP to the secondary Ethernet device (eth1)
#   uml_proxy_ether eth1

# The bridge
#auto br0
#  iface br0 inet dhcp
#   bridge_ports eth1 tap0
#   bridge_maxwait 0[/QUOTE]

As you can see here i was trying to set the virtual networking through the eth1 (My secondary ehternet card)
It didn't work
Also i let you here my route table in case it helps.
First without the bridge
```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
195.165.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
195.165.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         195.165.0.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         195.165.0.1     0.0.0.0         UG    100    0        0 eth0
```
And finally with the bridge
```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
195.165.0.3     0.0.0.0         255.255.255.255 UH    0      0        0 tap0
195.165.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
195.165.0.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         195.165.0.1     0.0.0.0         UG    100    0        0 br0
0.0.0.0         195.165.0.1     0.0.0.0         UG    100    0        0 eth0
```

My ifconfig -a output is:
```
$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:08:c7:49:b4:5b  
          inet addr:195.165.0.3  Bcast:195.165.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe49:b45b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9484 (9.2 KB)  TX bytes:8078 (7.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:01:80:3a:e6:ff  
          inet addr:195.165.0.4  Bcast:195.165.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe3a:e6ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10661245 (10.1 MB)  TX bytes:2636776 (2.5 MB)
          Interrupt:11 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:08:c7:49:b4:5b  
          inet6 addr: fe80::208:c7ff:fe49:b45b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10236690 (9.7 MB)  TX bytes:412394 (402.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4826674 (4.6 MB)  TX bytes:4826674 (4.6 MB)

tap0      Link encap:Ethernet  HWaddr 00:ff:c0:f2:e5:d9  
          inet6 addr: fe80::2ff:c0ff:fef2:e5d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:177 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Any advice will be of help. 
Thank you!

---

