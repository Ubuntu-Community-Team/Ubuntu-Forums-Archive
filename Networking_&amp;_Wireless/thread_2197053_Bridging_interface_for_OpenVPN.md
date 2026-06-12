---
title: "Bridging interface for OpenVPN"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by meagarcia315 on 2014-01-02
Hi, I am trying to setup a VPN server on my Ubuntu 12.04 LTS.
I am having problem on bridging network. I am not sure what to do.
Now I have bridged my network successfully but the main problem that I have is I am losing internet connection once my eth0 is bridged. But I am still able to connect from my remote client to the OpenVPN and can also ping any device on the same network of the server.
Once I take off the bridge, internet will work just fine. 
Any suggestions? I am not sure if I am just missing routes for it..
So the main goal is to have bridging working with internet along with OpenVPN server.
Thank you.

Here is my bridge config /etc/network/interfaces

> 
auto lo br0


iface lo inet loopback


iface br0 inet static
  address 192.168.1.100
  netmask 255.255.255.0
  gateway 192.168.1.1
  broadcast 192.168.1.255
  bridge_ports eth0


iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off


route

> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 br0




ifconfig


> br0       Link encap:Ethernet  HWaddr 00:11:43:dc:ad:c9            inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fedc:adc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:615589 (615.5 KB)  TX bytes:848493 (848.4 KB)


eth0      Link encap:Ethernet  HWaddr 00:11:43:dc:ad:c9  
          inet6 addr: fe80::211:43ff:fedc:adc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:778994 (778.9 KB)  TX bytes:863341 (863.3 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:298136 (298.1 KB)  TX bytes:298136 (298.1 KB)


tap0      Link encap:Ethernet  HWaddr 46:de:53:1d:94:06  
          inet6 addr: fe80::44de:53ff:fe1d:9406/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13936 (13.9 KB)  TX bytes:51246 (51.2 KB)




---

### Post by meagarcia315 on 2014-01-02
Woops, I figured it out. I was trying to ping google.com and it was showing me an error of "ping: unknown host google.com"
so I tried pinging it with the IP address, it was working but it wasn't resolving any hostnames. 
So I checked my resolv.conf and there wasn't any there so I had to specify it on my interfaces

final conf /etc/network/interfaces

> auto lo

iface lo inet loopback


auto br0
iface br0 inet static
  address 192.168.1.100
  netmask 255.255.255.0
  gateway 192.168.1.1
  broadcast 192.168.1.255
  dns-nameservers 192.168.1.1
  bridge_ports eth0


iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off

Sorry about that. :)

---

