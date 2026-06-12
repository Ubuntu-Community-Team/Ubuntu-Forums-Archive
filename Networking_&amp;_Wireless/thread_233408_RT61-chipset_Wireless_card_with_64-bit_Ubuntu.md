---
title: "RT61-chipset Wireless card with 64-bit Ubuntu?"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by Bergy on 2006-08-10
Howdy, all...  I love Ubuntu so far, and am looking forward to the day when I can move my computer back out of my dining room (where I hide my wireless router) and back onto desk, where I rely on my wireless connection to get online.

I'm running an RT61-chipset card on an AMD64 machine, 2G of RAM, and plenty o' other fine things.  However, following the advice on the almost aptly named "RaLink RT61 Wireless Solved" thread ( [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980) ), I have remained unable to get my wireless card to connect.

iwconfig spits out the following:
> lo        no wireless extensions.

eth1      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


and `ifconfig -a` spits out this:
> 
(... eth0 and eth1 nonsense here ...)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I am baffled and confused--confounded, even.  When I try to run the System > Administration > Networking tool freezes if I try to view properties on the ra0 connection, and terminal becomes unresponsive if I try to run dhclient or configure any setting with iwconfig.  Other key parts of the OS also act strangely after I initiate one of these freezes--the shutdown function no longer brings up a menu, I cannot start new instantiations of most programs from dropdown menus, etc.  Does anyone have any suggestions, instructions on how to start from scratch without wiping all the other grand configgering I've done, or otherwise useful ideas?

---

### Post by SamChameleon on 2006-08-23
Hi, 

as far as I could say, there is no driver available for rt61 on amd64 (someone correct me if I am wrong). There is a very simple way to get all working: Install 32bit Ubuntu ;) This will save a lot of trouble!

For further informations, look into this thread:
[http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61+amd64](http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61+amd64)

Greetings
Chris

---

