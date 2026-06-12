---
title: "New to ubuntu - no wired connection! Help!"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by ryanvh78 on 2008-01-27
Hi everyone.  I think this could be an easily solvable problem, but I am at a loss.  I have installed Ubuntu 7.10 on my Sony Vaio, and for the most part everything is working good.  However I am having trouble getting an internet connection through my wired connection.  Wireless works fine.  The cable modem that I am plugging up works on other computers running windows.  I believe that Ubuntu is identifying my Ethernet card correctly.  Here is its result from lspci:

[PHP]06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
[/PHP]

And here is the result of ifconfig:

[PHP]eth0      Link encap:Ethernet  HWaddr 00:1A:80:41:6A:45  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2755640 (2.6 MB)  TX bytes:32662 (31.8 KB)
          Interrupt:18 Base address:0x2000 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:80:41:6A:45  
          inet addr:169.254.4.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11984 (11.7 KB)  TX bytes:11984 (11.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1D:E0:1F:D2:D7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-1F-D2-D7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/PHP]

Finally, here is sudo dhclient eth0:

[PHP]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:80:41:6a:45
Sending on   LPF/eth0/00:1a:80:41:6a:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/PHP]

I have also seen that the driver is installed and recognized for my Ethernet card.  Does anyone have any suggestions on what setting/configuration will get my wired connection working properly?

Thanks!

---

### Post by jstableford on 2008-01-27
I am having the exact same problem with my wired connection. Unfortunately, my wireless doesn't work as well, so I'm at a total loss. Any help you find would be much appreciated!

---

