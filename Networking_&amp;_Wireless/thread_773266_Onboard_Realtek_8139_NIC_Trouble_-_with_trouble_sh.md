---
title: "Onboard Realtek 8139 NIC Trouble - with trouble shooting info"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by prophet665 on 2008-04-28
Hello everyone.  I have an 6 year old computer with a Realtek 8139 onboard NIC.  The system is dual booted between WinXP and Ubuntu 8.04 (beta 5?  whatever the last beta was).  The NIC works just fine under windows but totally fails under Ubuntu.  After reading about 4 million posts I have done the following beginning trouble shooting.  

**deus@Ex-Machina:/etc/init.d$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:60:67:75:9c:71
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s


**root@Ex-Machina:/etc/init.d# ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:60:67:75:9c:71  
          inet6 addr: fe80::260:67ff:fe75:9c71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd400 

eth0:avahi Link encap:Ethernet  HWaddr 00:60:67:75:9c:71  
          inet addr:169.254.7.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63608 (62.1 KB)  TX bytes:63608 (62.1 KB)


**root@Ex-Machina:/etc/init.d# dhclient**
There is already a pid file /var/run/dhclient.pid with pid 5663
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:60:67:75:9c:71
Sending on   LPF/eth0/00:60:67:75:9c:71
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


**root@Ex-Machina:/etc/init.d# dhclient**
There is already a pid file /var/run/dhclient.pid with pid 5663
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:60:67:75:9c:71
Sending on   LPF/eth0/00:60:67:75:9c:71
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


**root@Ex-Machina:/etc/init.d# ls -l | grep net**
-rwxrwxrwx 1 root root  1772 2007-12-03 14:50 networking

**I used the chmod command to change the permissions on the *networking* file just to make sure that wasn't the problem.**

**root@Ex-Machina:/etc/init.d# networking stop**
bash: networking: command not found


It almost seems to me that the NIC drivers aren't loading, but I don't know how to start them.

As a side question:
The USB ports are not working either and I wonder if the problems are related.  Of course they are working under WinXP.

Any help is greatly appreciated.

---

### Post by prophet665 on 2008-04-29
Sorry about replying to my own post.  It seems that the Realtek card, wireless or wired, seem to have a lot of problems.  

If I am creating a new system build in the future, should I just look for motherboards that do not have Realtek chipsets in them?

---

