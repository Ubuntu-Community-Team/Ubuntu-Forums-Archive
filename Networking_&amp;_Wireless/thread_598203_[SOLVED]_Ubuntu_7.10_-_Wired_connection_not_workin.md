---
title: "[SOLVED] Ubuntu 7.10 - Wired connection not working (Wireless up ok)"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by GreaseMonkey on 2007-10-31
I've looked in the other threads about wired connections not running and didn't find much that applied.

My wireless dongle works fine and connects through to my Belkin G+ router first time, every time.

The problem is that my wired (faster) connection doesn't come up no matter what I do. Does Linux only use one of the connections, rather than both like my WinXP system? I've never run a box with both networking options on Linux before and can't find any info that says whether this is the problem or not.

I've pasted my ifconfig result below and would like to point out that I have no idea what that extra bit on the** eth0:avah** is talking about as I have no 169 network here *grins*

Obviously eth0 is wired and eth1 is my dongle.

I'm just an author, I use Linux to work on because that way I don't load up as many games *blushes* and I actually get more done :)

> 
eth0      Link encap:Ethernet  HWaddr 00:15:58:6F:45:D5  
          inet6 addr: fe80::215:58ff:fe6f:45d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:02:72:5D:DA:59  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe5d:da59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7617 errors:1422 dropped:70 overruns:1 frame:1417
          TX packets:7242 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8850259 (8.4 MB)  TX bytes:703038 (686.5 KB)

eth0:avah Link encap:Ethernet  HWaddr 00:15:58:6F:45:D5  
          inet addr:169.254.7.80  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1302 (1.2 KB)  TX bytes:1302 (1.2 KB)

---

### Post by CHFFriday on 2007-10-31
Greasemonky,
Please note the Interrupt on etho:avah and etho are the same. Somewhere on this form I read how you can remove one of these as you can not have the same interrupt on two diferent nics. Most likly yoy need to remove avah.

CHFFriday

---

### Post by GreaseMonkey on 2007-10-31
I can't find a post detailing that particular solution, CHFFriday - I searched two different ways for it.

I did come across a post suggesting that I needed to use the admin network tool to reset the eth0 to DHCP and then restart the network which I did, but it didn't work. Output reproduced below:

> xxxx@xxxx-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for xxxx:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5739
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:6f:45:d5
Sending on   LPF/eth0/00:15:58:6f:45:d5
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:6f:45:d5
Sending on   LPF/eth0/00:15:58:6f:45:d5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                            

It's not a huge problem, as I said, but it just puzzles me why the wireless works first time and the 'obvious' wired connection fails :)

---

### Post by pwkm on 2007-10-31
Hello 

I have got the same problem. Your eth0 isn't getting any ip address.
 I don't know why we don't get an Ip address.

You can give him a fix ip address, but that didn't solve my problem.

So if someone can help us , ???

thx

---

### Post by rtype on 2007-10-31
do you dual boot with win xp?

---

### Post by GreaseMonkey on 2007-11-06
> **rtype said:**
> do you dual boot with win xp?

Yes I do, and that turned out to be the problem.

I searched the forum here when I got back today and found the solution about enabling "Wake on Lan" for the wired connection in XP. That has fixed it.

Thanks to whoever figured that one out :guitar:

---

