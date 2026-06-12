---
title: "Problem with internect connection sharing"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by nerull2 on 2014-12-16
Hi, first up im pretty new to ubuntu/linux in general. I have a ubuntu 14.04 server with 2 nics in it. eth0 (with subnet 192.168.0.0) is connected directly to my router for internet and eth1 (192.168.1.0) is connected my a switch thats connected to my lan. I have followed the 2 guides below (amongst others) and i can get the internal network working fine, all the computers connected to my switch can ping each other and the server but cannot access the internet or ping any on the 0 subnet (which from what i can tell is how it should be). Im using my routers dhcp on the eth0 network cause it serves my wireless, and ive set my cisco sg300 switch to bethe dhcp server on the other subnet. Once i get things working right i plan to replace them with a dhcp/dns server on my ubuntu server.

On my windows machine my samba shares and everything work fine and i can access my server fine but i get "Limited" show up on my ethernet connection, says i dont have net connection. I go to diagnose and it says "The connection between your access point,router, or cable modem and the Internet is broken"

Any help would be greatly appreciated as after spending my whole weekend trying to get it to work im starting to get mildly agitated :)

this is my interfaces

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.254
dns-nameservers 192.231.203.132

auto eth1
iface eth1 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    dns-nameservers 192.231.203.132
```

ip route

```
default via 192.168.0.254 dev eth0 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.1 
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.1 


```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1


```

ifconfig 

```
eth0      Link encap:Ethernet  HWaddr ec:22:80:eb:b3:b8  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ee22:80ff:feeb:b3b8/64 Scope:Link
          inet6 addr: 2001:44b8:212c:8a00:ee22:80ff:feeb:b3b8/64 Scope:Global
          inet6 addr: 2001:44b8:212c:8a00:15a6:6d0e:d562:d3fb/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10708 errors:0 dropped:1 overruns:0 frame:0
          TX packets:11749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4669756 (4.6 MB)  TX bytes:1672037 (1.6 MB)

eth1      Link encap:Ethernet  HWaddr 54:04:a6:28:d3:09  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe28:d309/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133402 (133.4 KB)  TX bytes:354483 (354.4 KB)
          Interrupt:20 Memory:f7e00000-f7e20000 


```
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

