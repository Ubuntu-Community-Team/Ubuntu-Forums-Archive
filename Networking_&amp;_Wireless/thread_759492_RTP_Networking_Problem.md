---
title: "RTP Networking Problem"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by vhtmg108 on 2008-04-19
In my local network there is a server which transmits/broadcasts music to 10.0.0.255 by RTP, and my laptop(ip:10.0.0.2) on which RTP receiver(written in java) runs to play RTP stream.
The laptop is connected to network via the wireless ethernet device.

RTP receiver successfully plays on WindowsNT; but it doesn't play on Ubuntu, it waits for incoming stream. I also tried with JMStudio both on WndowsNT and Ubuntu, it gave the same result. 

I think there are two probable reasons of the problem:

1) My laptop has a wired(eth0) and a wireless(eth1) ethernet device. Maybe the RTP receiver and JMStudio waits for incoming stream from eth0. Both application is JAVA RTP BASED, so there should be a JAVA setting. But other network(socket) applications written in java work perfectly. 
I COULD NOT SOLVE THIS ISSUE.

[COLOR="Gray"]eth0      Link encap:Ethernet  HWaddr 00:14:22:ED:5F:AC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:21:D8:91  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe21:d891/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4469654 (4.2 MB)  TX bytes:973846 (951.0 KB)
          Interrupt:18 Base address:0xe000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:492 (492.0 b)  TX bytes:492 (492.0 b)[/COLOR]


2)The file /etc/hosts contains

[COLOR="Gray"]# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.0.0.2 DELLICAN-UBUNTU[/COLOR]

There is no loopback such as 127.0.0.1 localhost.
The solutions in [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=605514") and in [[COLOR="Blue"]here[/COLOR]]("http://forum.java.sun.com/thread.jspa?threadID=431541") do not work.

I COULD NOT SOLVE THIS ISSUE TOO.

Thanks for your interests.

---

