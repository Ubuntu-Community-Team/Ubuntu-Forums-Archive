---
title: "Issues with dual NIC and network connectivity"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by rojmab on 2008-04-01
I'm having issues without my wired connection and wireless...
Both connect just fine, the wired connection has a static IP (10.4.18.100), wireless is DHCP. I cannot ping or access the machine in any way from anywhere except my local network. Ex: From 10.1.1.0 or 10.4.5.0
I can get to the internet from the box, but that's about it. I'm a n00b... please help. I want to use Eth0 for primary connection. I'm thinking it's something to do with the routes, but I'm not sure.

Local segment: 10.4.18.0
Eth0= Wired
Eth2= Wireless

ryan@ryan-desktop:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.4.18.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.4.18.0       0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.4.18.1       0.0.0.0         UG    100    0        0 eth2
0.0.0.0         10.4.18.1       0.0.0.0         UG    100    0        0 eth0

ryan@ryan-desktop:/$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.18.100
netmask 255.255.255.0
network 10.4.18.0
broadcast 10.4.18.255
gateway 10.4.18.1
dns-nameservers 10.1.1.20 10.1.1.23

auto eth2
iface eth2 inet dhcp
wpa-psk 9e7592f72afdd90e9902aa78fd3df563b0cd2922ac0f2e8cbc0a49526979d5d5
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid rjcdbf

ryan@ryan-desktop:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:AD:A5:38
          inet addr:10.4.18.100  Bcast:10.4.18.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fead:a538/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:311224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:113685699 (108.4 MB)  TX bytes:3460095 (3.2 MB)
          Interrupt:16 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:26:54:12:0C:44
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x4000

eth2      Link encap:Ethernet  HWaddr 00:0F:66:6E:52:B5
          inet addr:10.4.18.103  Bcast:10.4.18.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe6e:52b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13153 errors:0 dropped:37866 overruns:0 frame:0
          TX packets:5387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11329244 (10.8 MB)  TX bytes:336435 (328.5 KB)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:145728 (142.3 KB)  TX bytes:145728 (142.3 KB)


Thanks!!

---

