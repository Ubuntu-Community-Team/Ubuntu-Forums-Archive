---
title: "See router(?), but can't connect"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by aaviv on 2007-10-18
I have a 3com 3CRUSB10075 wireless card, which suppose to work "out of the box", but I can't make it work. I tried playing with many things suggested in this forum, with/without encryption, static ip/dhcp, and more. The card and router works fine on Windows. I can also connect with dhcp using wired connection to the same router.
Any help would be great!
Here are some command outputs:

**aaviv@aaviv-desktop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:54:8E:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:18:6E:2F:22:20  
          inet6 addr: fe80::218:6eff:fe2f:2220/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:46 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10778 (10.5 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:1A:4D:54:8E:B2  
          inet addr:169.254.7.99  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x6000 

eth1:avah Link encap:Ethernet  HWaddr 00:18:6E:2F:22:20  
          inet addr:169.254.2.170  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2016 (1.9 KiB)  TX bytes:2016 (1.9 KiB)

**aaviv@aaviv-desktop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"KK"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0E:2E:C2:F8:2F   
          Bit Rate=11 Mb/s   
          Link Quality=98/100  Signal level=32/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**aaviv@aaviv-desktop:~$ sudo ifup eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:6e:2f:22:20
Sending on   LPF/eth1/00:18:6e:2f:22:20
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**aaviv@aaviv-desktop:~$ iwevent**
Waiting for Wireless Events from interfaces...
10:30:11.896695   eth1     Set ESSID:off/any
10:30:11.896736   eth1     New Access Point/Cell address:Not-Associated
10:30:14.020920   eth1     Set ESSID:"KK"
10:30:14.031068   eth1     Custom driver event:authenticated
10:30:14.050166   eth1     New Access Point/Cell address:00:0E:2E:C2:F8:2F

Thanks

---

### Post by aaviv on 2007-10-19
After 2 days of struggle, I reinstalled Gutsy 32bit, instead of Fiesty 64bit. And everything works well.

---

