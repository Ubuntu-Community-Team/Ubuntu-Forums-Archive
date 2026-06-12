---
title: "NIC configuration Question"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by jamiwent on 2015-05-06
Hi, 

First of all I am new to working with ubuntu and would like to say I am having great fun playing around with it. I am currently wanting to setup a Radius server, MySql with coovachilli on the same server and have some network pre-requisites I need to meet before I can proceed. Namely the following:

[COLOR=#000000]2 NICs eth0 connected to Internet on either static or dhcp, eth1 connect to clients with no IP address

[/COLOR]Question is how do I configure the network in this manner, also I do not have eth1 when I check ipconfig I have the following: 

So I presume the fact I have a wlan0 means I cannot do this setup or? It seems I need two physical network cards and the wlan does not count?

ifconfig -a
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:0a:f3:a4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10996 (10.9 KB)  TX bytes:10996 (10.9 KB)


wlan0     Link encap:Ethernet  HWaddr 74:2f:68:ca:ad:82
          inet addr:192.168.1.179  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::762f:68ff:feca:ad82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3962721 (3.9 MB)  TX bytes:185784 (185.7 KB)

Regards,

Jamie

---

### Post by michi1983 on 2015-05-07
Hi,

here is a pretty good tutorial.
They say it's not necessary to have two eth ports, wifi should work too.

[https://help.ubuntu.com/community/WifiDocs/CoovaChilli](https://help.ubuntu.com/community/WifiDocs/CoovaChilli)

Good luck!
Greetz

---

### Post by SeijiSensei on 2015-05-07
Just give eth0 a [static address]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/") in the same subnet as the client machines.  You'll use wlan0 as the Internet-facing adapter.

---

