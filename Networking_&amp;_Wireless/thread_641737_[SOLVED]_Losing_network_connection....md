---
title: "[SOLVED] Losing network connection..."
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by CD Baric on 2007-12-15
Hi:

Over the last couple weeks I have been experiencing a problem with Ubuntu dropping the network connection to my router and bringing up a bizare IP address that doesn't work.

Here is what ifconfig says when the connection is working:

user@black:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:6E:11:07  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe6e:1107/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1139692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1386674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:430124984 (410.1 MiB)  TX bytes:939453764 (895.9 MiB)
          Interrupt:18 Base address:0xe400 


After a few days or even hours:

user@black:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:6E:11:07  
          inet6 addr: fe80::20d:87ff:fe6e:1107/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1139087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1385769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:429941356 (410.0 MiB)  TX bytes:939351825 (895.8 MiB)
          Interrupt:18 Base address:0xe400 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:87:6E:11:07  
          inet addr:169.254.2.205  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe400 

I have to manually reset the network connection.

I am running Ubuntu 7.04 and this development is relatively new. I suspect some upgrade has skewed my network manager.

No other computer connected to the same router is experiencing any problem - my Slackware 12 box has been up and running for over 3 months running dhcpcd and has experienced no problem maintaining it's lease.

HELP!

CD 'Bar' Baric
.

Help!

---

### Post by CD Baric on 2007-12-17
I repaired the situation by first of all killing off the Network Manger applet because it is a piece of crap amd installing dhcpcd in it's stead.

At the command line # sudo dhcpcd eth0

Now Ubuntu holds it's IP address lease without a problem.

Perhaps somebody should do something about Network Manager - it is CRAP!

CD Baric

---

