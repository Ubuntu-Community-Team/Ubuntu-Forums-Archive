---
title: "ethernet internet problem"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by volpne on 2008-10-27
Hi 
Having problems with ethernet connection. 
Everything was ok untill we changed internet providers and started using the new modem, unfortunatly there was a conflict between our old modem and our new provider. 

New modem Siemens ADSL SL2-141-1

Desktop PC 64AMD

Having read a bit about Networks Settings, all the examples give 3 options. Wireless connection, wired connection and point to point connection. Where as I have only 2 options, wireless and point to point.

The other information I have is.

sudo ifconfig eth0 up

returns no answer.

sudo ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:19:66:60:95:e3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11440 (11.1 KB)  TX bytes:25144 (24.5 KB)
          Interrupt:248 Base address:0x4000 

sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:19:66:60:95:e3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11620 (11.3 KB)  TX bytes:27598 (26.9 KB)
          Interrupt:248 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:66:60:95:e3  
          inet addr:169.254.8.201  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:248 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92904 (90.7 KB)  TX bytes:92904 (90.7 KB)


At the moment Im using Windows with all those bleeding pop ups arrgghhhh.

Thanks, in advance.

V

---

### Post by volpne on 2008-10-27
Correction

The 2 options in Network Settings are infact wired connection and point to point, which one is applicable to ethernet. It took quite a while to notice as Im jumping between OS's.

Other information is.

$ sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 7224
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:66:60:95:e3
Sending on   LPF/eth0/00:19:66:60:95:e3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Iowan on 2008-10-27
Generally, the wired connection would be the ethernet connection.  *Might* need to cycle power on the modem to make it play nice for this MAC address.  the avahi address (169.254.8.201) means it failed to get DHCP address.

---

