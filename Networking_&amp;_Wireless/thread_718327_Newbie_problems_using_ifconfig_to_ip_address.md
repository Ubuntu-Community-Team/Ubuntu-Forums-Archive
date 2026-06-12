---
title: "Newbie problems using ifconfig to ip address"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by sonnychee on 2008-03-08
Hey Guys,

I'm having problems changing the ip address on my install of Ubuntu (running within a vmplayer with bridged networking). Once I make the change, the internet becomes unavailable...  I've used the following commands:

$> sudo ifconfig eth3 192.168.127.88 netmask 255.255.255.0
$> sudo ifconfig eth3 
eth3      Link encap:Ethernet  HWaddr 00:0C:29:9D:A8:56  
          inet addr:192.168.127.88  Bcast:192.168.127.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe9d:a856/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10468067 (9.9 MB)  TX bytes:2219537 (2.1 MB)
          Interrupt:18 Base address:0x1400 

$> ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Any suggestions would be really welcome by this newbie.

Sonny.

---

### Post by sonnychee on 2008-03-08
Incidentally, my Ubuntu install boots up with the following ip address assignment that *does * work.  I'm trying to change the subnet to match the host Windows system that the vmplayer is residing on.

$> sudo ifconfig eth3
eth3      Link encap:Ethernet  HWaddr 00:0C:29:9D:A8:56  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe9d:a856/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10479902 (9.9 MB)  TX bytes:2222501 (2.1 MB)
          Interrupt:18 Base address:0x1400 

---------

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.127.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.226.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Network Connect Adapter:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Wireless Network Connection 6:

        Connection-specific DNS Suffix  . : gateway.2wire.net
        IP Address. . . . . . . . . . . . : 192.168.1.115
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254

---

