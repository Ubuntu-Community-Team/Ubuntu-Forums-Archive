---
title: "Dell Vostro 1500 New to Ubuntu"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by kn1ghtus on 2009-02-08
I have even donated money to ubuntu over the years, however in my work I have only had the time to use windows, I am now able to work with ubuntu, and would like to get some things working, then I plan on helping out where I can, as a sysadmin for 15 years (in windows however)  So first of happy shout out from california, 

Okay I have gotten through the install pretty easily, shocked how well that worked out, to dual boot from windows.  I am running 8.10, everything on my lappy seems to be happy, EXCEPT the wireless network.  Which is the biggest thing on a laptop (obviously)  

I am guessing the problem is with the driver???  any help would be very appreciated!  sorry for the length of this, but I would rather give MORE information then not enough information...
 

I have the proprietary driver WL running, but it says it is enabled and is happy...


hardware test does show the wireless network card...

Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)



ifconfig -a shows

eth0      Link encap:Ethernet  HWaddr 00:1d:09:bc:24:5c  
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:febc:245c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4495684 (4.4 MB)  TX bytes:581978 (581.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19456 (19.4 KB)  TX bytes:19456 (19.4 KB)

pan0      Link encap:Ethernet  HWaddr d6:90:20:bb:01:61  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:a1:f7:47  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-4C-A1-F7-47-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by yeats on 2009-02-08
What happens when you open a terminal and do

```

sudo dhclient wlan0

```

?

---

### Post by kn1ghtus on 2009-02-08
thanks for your prompt attention to this, I love this community, and again, once I get started I am going to do my best to return favors... without further adieu,

 sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:4c:a1:f7:47
Sending on   LPF/wlan0/00:1e:4c:a1:f7:47
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

