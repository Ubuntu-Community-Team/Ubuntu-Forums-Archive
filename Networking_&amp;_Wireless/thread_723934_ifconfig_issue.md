---
title: "ifconfig issue"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by metallicatony on 2008-03-14
I have a wired network card, wireless network card and bluetooth in my system. Im using only wireless network which is configured and works fine. Once i boot up the system until GDM (X Login)  the system is fast. After i login into gdm, the gnome desktop takes quite a long time to show the desktop. I found out that its fast after i restart the network service in tty and login into GDM. I dont know why.
When i did a ifconfig before login into GDM, the output is
[metallicatony @ Zion ~]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:60:CF:AC:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:40 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18024 (17.6 KB)  TX bytes:546 (546.0 b)
          Interrupt:10 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1C:23:F9:1E:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:60:CF:AC:50  
          inet addr:169.254.7.139  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0  
          RX bytes:1098 (1.0 KB)  TX bytes:1098 (1.0 KB)

I dont know why its showing up eth1 and eth0:avah devices though i have only eth0 configured in my interfaces file. See below.

[metallicatony @ Zion ~]$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp
wpa-psk cde07efcab836fe01633b65eb213a2e33d1f574bbb80f0cb7c150d845783be7c
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Corleone

[metallicatony @ Zion ~]$ cat interfaces.txt 
eth0      Link encap:Ethernet  HWaddr 00:1D:60:CF:AC:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:40 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18024 (17.6 KB)  TX bytes:546 (546.0 b)
          Interrupt:10 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1C:23:F9:1E:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:60:CF:AC:50  
          inet addr:169.254.7.139  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1098 (1.0 KB)  TX bytes:1098 (1.0 KB)


After I restart the network service
[metallicatony @ Zion ~]$ sudo /etc/init.d/networking restart
[sudo] password for metallicatony:
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth0.pid with pid 6070
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:60:cf:ac:50
Sending on   LPF/eth0/00:1d:60:cf:ac:50
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:60:cf:ac:50
Sending on   LPF/eth0/00:1d:60:cf:ac:50
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.3 -- renewal in 942010113 seconds.
                                                                                                                                                   [ OK ]

Now when i did a ifconfig
[metallicatony @ Zion ~]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:60:CF:AC:50  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4025 errors:0 dropped:62572 overruns:0 frame:0
          TX packets:3843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3330452 (3.1 MB)  TX bytes:678066 (662.1 KB)
          Interrupt:10 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:1C:23:F9:1E:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1098 (1.0 KB)  TX bytes:1098 (1.0 KB)


The eth0-avah device disappeared. So, Im assuming that its the culprit here and its loading creates problems which in turn is not leasing IP properly to my eth0 (wireless) device which finally slows down my GDM login and GNOME desktop.

How can i get rid of it? Where should i disable it? Is there anything else which is creating this slowness problem?

---

