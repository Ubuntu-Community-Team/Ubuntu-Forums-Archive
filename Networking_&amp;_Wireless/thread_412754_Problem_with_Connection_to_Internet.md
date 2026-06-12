---
title: "Problem with Connection to Internet"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by jcooper23 on 2007-04-18
Hello Ubuntu World.  I have just installed 6.1 for the firsts time, and I am brand new to linux.  Everything is working well except I cannot get a connection to the internet.  Here are some early diag results...

jcooper@jcooper-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:24:D1:84:3C  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:24ff:fed1:843c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:399576 (390.2 KiB)  TX bytes:2291 (2.2 KiB)
          Interrupt:11 Base address:0x1440 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


jcooper@jcooper-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

jcooper@jcooper-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1

jcooper@jcooper-desktop:~$ host google.com
;; connection timed out; no servers could be reached


Any help that you could provide would be wonderful.

Thanks,
JC

---

