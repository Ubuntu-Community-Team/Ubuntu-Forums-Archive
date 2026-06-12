---
title: "network not working 8.0.4"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by john82q on 2008-06-30
hi, I am new to ubuntu new to this list

I downloaded and installed 8.04 desktop and I can not make a Ethernet connection. The ASUS motherboard has a Attansic nic. On reading this thread [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845&page=8](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845&page=8)

I believed the driver although installed to be bad so fitted a Intel pro 100 nic from the scrap box. After much fiddling around with my limited knowledge of all things nix I could not get this to work either. I gave up and installed fedora to test things the intel nic worked but there was no driver for the attansic.

So now I have reinstalled unbuntu but still no joy.
The environment is a LAN the DHCP server is WIN 2003 I have tried both cards configured static and DHCP neither works either way. got me stumped.

Any Suggestions or the embarrassingly obvious?

note: real ip addrs masked to protect the innocent

john@john-desktop:/home$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:d0:b7:4d:56:c6  
          inet addr:xx.xx.32.208  Bcast:xx.xx.32.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:b7ff:fe4d:56c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:d0:8e:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dffc0000-e0000000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1e:8c:d0:8e:99  
          inet addr:169.254.8.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55932 (54.6 KB)  TX bytes:55932 (54.6 KB)

john@john-desktop:/home$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1

iface eth0 inet static
address xx.xx.32.208
netmask 255.255.255.0
gateway xx.xx.32.2

auto eth0
john@john-desktop:/home$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: a0
       serial: 00:1e:8c:d0:8e:99
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 08
       serial: 00:d0:b7:4d:56:c6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A ip=xx.xx.32.208 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


john@john-desktop:/home$ sudo mii-tool
eth0: negotiated 100baseTx-HD, link ok
eth1: negotiated 100baseTx-HD, link ok

john@john-desktop:/home$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 13427
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1e:8c:d0:8e:99
Sending on   LPF/eth1/00:1e:8c:d0:8e:99
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
RTNETLINK answers: No such process
grep: /etc/resolv.conf: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1e:8c:d0:8e:99
Sending on   LPF/eth1/00:1e:8c:d0:8e:99
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]
john@john-desktop:/home$ ping xx.xx.32.2
PING xx.xx.32.2 (xx.xx.32.2) 56(84) bytes of data.
From xx.xx.32.208 icmp_seq=1 Destination Host Unreachable
From xx.xx.32.208 icmp_seq=2 Destination Host Unreachable
From xx.xx.32.208 icmp_seq=3 Destination Host Unreachable

--- xx.xx.32.2 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4017ms
, pipe 3
john@john-desktop:/home$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xx.xx.32.0      *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
default         xx.xx.32.2      0.0.0.0         UG    100    0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1
john@john-desktop:/home$

---

### Post by chili555 on 2008-07-01
eth1, your Attansic, is likely not to work until a better module is written. I suggest amending your */etc/network/interfaces* to look like:```
auto lo
iface lo inet loopback

#auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address xx.xx.32.208
netmask 255.255.255.0
gateway xx.xx.32.2
```The # will stop eth1, your Attansic, from starting, and *auto eth0* should start eth0. Now do:```
sudo ifdown eth0 && sudo ifup eth0
ping -c3 xx.xx.32.2
```Substitute your actual gatewy address, of course. Are you connected?

---

### Post by john82q on 2008-07-01
hi,
In other words your suggesting the L2 module is preventing the intel from working ? Sadly no.

For good measure I tried you suggestion, but the intel nic will still not work.

I went one further and disabled the attansic in the BIOs so the module wont even load but still no luck.

I am missing somthing here , (talking about  intel nic now )
Card seems to be configured, interface is started running, yet nothing at all comes from or goes into this box.

---

