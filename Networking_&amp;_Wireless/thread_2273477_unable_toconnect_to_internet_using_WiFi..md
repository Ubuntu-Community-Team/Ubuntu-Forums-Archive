---
title: "unable toconnect to internet using WiFi."
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by lokesh_chakka on 2015-04-13
hai,

I was using wifi dongle for connecting to Internet. I am able to connect to WiFi. But I am unable to connect to Internet.

I am sure there is some problem with network settings in my ubuntu 14.04 LTS.
[HTML]lokesh@lokesh-Vostro-1550:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 24:b6:fd:10:c8:1e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:221209 (221.2 KB)  TX bytes:221209 (221.2 KB)

wlan0     Link encap:Ethernet  HWaddr e4:d5:3d:e9:8e:e3  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fee9:8ee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:539084 (539.0 KB)  TX bytes:317196 (317.1 KB)

[/HTML]

when I try to ping 192.168.1.1, I am seeing the following:
[HTML]
ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable
From 192.168.1.100 icmp_seq=4 Destination Host Unreachable
From 192.168.1.100 icmp_seq=5 Destination Host Unreachable
From 192.168.1.100 icmp_seq=6 Destination Host Unreachable
[/HTML]

but it is supposed to ping from wlan0 instead of eth0.

i tried to do "resolvconf -a wlan0" but it is hanging over there.
can some one please help in fixing the issue ?

---

### Post by michi1983 on 2015-04-14
So, cable is working, wifi is not?
To resolve this, please only use one method at a time. Use either either the eth0 port or use the wlan0 interface for testing.
What is your computer connected to? Your ISP Modem/Router?

---

### Post by lokesh_chakka on 2015-04-14
earlier  /etc/network/interfaces is holding the following three lines:

auto eth0
iface eth0 inet static
address 192.168.1.100

I commented all those three lines.

now I am able to connect to wifi and internet. I don't know the extact reason why it is working now. but My problem is solved.

---

### Post by michi1983 on 2015-04-14
because you haven't defined dns and gateway ;)

---

