---
title: "Dynex WGDTC"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by hdensley on 2007-06-10
I'm having a heck of a time getting this wireless card to work on 7.04 - despite the fact that many in the linux community say it should work 'out of the box'.  I would greatly appreciate some professional intervention at this point.

On a related note, I tried re-compiling madwifi, with not much luck.  Essentially it ignores the ./configure command, even with having the following installed - headers, build essentials, gtk

-----------------------------------------------
> ubuntu@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:20:ED:70:90:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:19 

eth0:avah Link encap:Ethernet  HWaddr 00:20:ED:70:90:83  
          inet addr:169.254.8.26  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:10812 (10.5 KiB)  TX bytes:10812 (10.5 KiB) 

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
-----------------------------------------------

---

