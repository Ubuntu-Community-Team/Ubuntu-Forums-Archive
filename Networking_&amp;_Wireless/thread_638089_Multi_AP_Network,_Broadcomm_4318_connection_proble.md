---
title: "Multi AP Network, Broadcomm 4318 connection problems."
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by beorn! on 2007-12-11
I was wondering if you could lend me some help. I am running Ubuntu 7.10 and Windows XP dual boot on a Gateway MX3215 with a Broadcom 4318 wireless card. In Windows I have no issues. In Linux I have had limited success using both NDISwrapper and the reversed engineered firmware while connected to our Bluesocket wireless network at my College. Both ways it lets me connect no problem the first try, but then it drops after a random period of time (sometimes 2 minutes, sometimes 15 minutes), and afterwards it will not let me back on. Sometime rebooting will allow me back on, but that's about it. I think what is happening is that the Network Manager gets confused with so many APs of the same name. If anyone can offer assistance, or point me to the right documentation I would be very grateful.

---

### Post by beorn! on 2007-12-12
If this helps... I've Emailed the following to our sysadmin. Please note that our BlueSocket network is called PROWLnet.  Also please excuse my limited knowledge of networking... I am trying and always willing to learn.

My first IP today was...
 129.89.223.64

I was connected for approx. 1hour, then all my pages stopped loading...

at the time nm-applet and gnome-network-manager showed me as connected.

I ran ifconfig and iwconfig...

eth0      Link encap:Ethernet  HWaddr 00:03:25:35:C7:B6 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:706176 (689.6 KB)  TX bytes:16637 (16.2 KB)
          Interrupt:19 Base address:0x1800

eth1      Link encap:Ethernet  HWaddr 00:C0:A8:AA:0D:A0 
          inet6 addr: fe80::2c0:a8ff:feaa:da0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49953 errors:0 dropped:16586 overruns:0 frame:0
          TX packets:10293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14319102 ( 13.6 MB)  TX bytes:1841048 (1.7 MB)
          Interrupt:20 Base address:0x4000

eth1:avah Link encap:Ethernet  HWaddr 00:C0:A8:AA:0D:A0 
          inet addr: 169.254.7.99  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x4000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14120 (13.7 KB)  TX bytes:14120 (13.7 KB)

I tried using nm-applet to connect. The first green light in the applet lit (showing that it was able to send packets to the router) The second light never lit up.

Frustrated I went to smoke... Came back and I was magically back on PROWLnet with the same IP.

---

