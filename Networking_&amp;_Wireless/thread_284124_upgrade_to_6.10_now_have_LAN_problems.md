---
title: "upgrade to 6.10 now have LAN problems"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by Funboy63 on 2006-10-25
Hi to all,

Have an odd one which I as yet can not work out what's gone wrong. I have upgraded my laptop from 5.10 to 6.10 and seem to have lost my LAN by this I mean file share via gFTP or direct Firefox IP address to other equipment.

I can still access the internet both wired and wireless plus gftp to my websites just none of the LAN boxes ](*,) 

Here is my ifconfig print out,

eth0      Link encap:Ethernet  HWaddr 00:90:F5:38:54:3C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14160 (13.8 KiB)  TX bytes:14160 (13.8 KiB)

ra0       Link encap:Ethernet  HWaddr 00:13:D3:6F:B4:83  
          inet addr:192.168.200.2  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe6f:b483/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8553 errors:4 dropped:4 overruns:0 carrier:0
          collisions:83 txqueuelen:1000 
          RX bytes:18474165 (17.6 MiB)  TX bytes:910768 (889.4 KiB)
          Interrupt:201 Base address:0xc000 

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

When setting up 5.10 to get internet access I needed to insert my providers DNS settings so other than this all should be as standard less my network setup which is as follows,

Gateway 192.168.200.1
Subnet 255.255.255.0
wireless (Static) 192.168.200.2

Firefox error after typing ([http://192.168.200.7/](http://192.168.200.7/)) into address bar,

> Firefox can't establish a connection to the server at 192.168.200.7.

Any light you can shine on this would be great help as I feel currently lost in the dark. :) 

Cheers

PS Go easy on me if it's something really stupid and easy that I need to do. ;)

---

### Post by Funboy63 on 2006-10-25
I feel sick now :mrgreen: 

The problem has been resolved and was my router. Now don't ask me why but I decided to reboot it and the problem seem to have sorted itself. So not sure if upgrading to 6.10 with a static IP caused the error or just very bad timing on the part of my router playing up on me.

So looks like I have made a fool of myself as should have check the router before posting. [-( 

Cheers

---

