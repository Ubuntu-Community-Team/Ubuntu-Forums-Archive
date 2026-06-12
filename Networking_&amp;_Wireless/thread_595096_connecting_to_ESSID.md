---
title: "connecting to ESSID"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by jianthawiian on 2007-10-28
I'm using Ubuntu 7.04 "Feisty" and i've used NDISwrapper to install my wireless card.  All is well.. I think, i can see the SSID that my wireless router is broadcasting; i can even "connect" to it.  It tells me that i am connected and gives my my signal strength.  But when i go to access the web i get "Problem Loading Page" error  :( Don't know what the problem is... if anyone has any in-sight i'd appreciate it... hopefully it's a simple fix.

Thanks

---

### Post by kevdog on 2007-10-28
can you post the following when you are connected (or think you are)

ifconfig
route -n

---

### Post by jianthawiian on 2007-10-29
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:8A:FF:39             UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000 
eth0:avah Link encap:Ethernet  HWaddr 00:0B:CD:8A:FF:39  
          inet addr:169.254.8.93  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x4000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9876 (9.6 KiB)  TX bytes:9876 (9.6 KiB)
wlan0     Link encap:Ethernet  HWaddr 00:0F:66:3B:E6:AE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:241083 (235.4 KiB)  TX bytes:21799 (21.2 KiB)
          Interrupt:11 Memory:34000000-34000025  wlan0:ava Link encap:Ethernet  HWaddr 00:0F:66:3B:E6:AE  
          inet addr:169.254.8.139  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:34000000-34000025 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0      eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0      wlan0
0.0.0.0 	0.0.0.0         0.0.0.0             U     1000   0     0      eth0 


thanks for your help

---

### Post by Lylepalooza on 2007-10-29
Two quick things:
Do you use any security?
Also, if it is connecting, but not allowing you to do anything, it could be because the access point is setup to only allow certain MAC addresses.

---

### Post by jianthawiian on 2007-10-29
It is using security and i was getting prompted for the password then i was getting this far.  And the router is set to allow all.

But i tried a different wireless card went from a Linksys to a Compaq card and it works now. :) 

Thanks for your help!

---

