---
title: "No wired internet after install"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by bclintbe on 2008-06-12
I'm helping a friend set up Ubuntu on his computer . I've been using Ubuntu for about two years but I've never experienced a problem like this, so I'm stumped. 

When we tried 8.04 from the live CD, everything worked great, including his internet (he has an HP desktop with a regular wired NIC, and wireless also built in). We were testing the internet using a wired connection, since we are unable to try the wireless because he doesn't have a wireless router. It does show some secured wireless networks that are nearby. So far so good. 

After installing 8.04 he has no more internet. It shows that it's trying to acquire an address, then shows that it's done, but when you show its connection info, all the numbers are zeroes and it's dead.

I can get it to work from the live CD every time, but never from the actual install to the hard drive. So far I've checked the following...

In both live CD and HD install, it's using the same driver, r8169.

When I run ifconfig from the live CD I get...

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:4e:26:5f 
          inet addr:10.120.2.104  Bcast:10.120.3.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:8cff:fe4e:265f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12762 errors:0 dropped:3669548760 overruns:0 frame:0
          TX packets:4106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5977695 (5.7 MB)  TX bytes:451264 (440.6 KB)
          Interrupt:218 Base address:0x4000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:584300 (570.6 KB)  TX bytes:584300 (570.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:82:ca:11 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-82-CA-11-00-00-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

But when I run it from the HD install I get...

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:4e:26:5f  
          inet6 addr: fe80::21e:8cff:fe4e:265f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967267 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:4e:26:5f  
          inet addr:169.254.4.148  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88488 (86.4 KB)  TX bytes:88488 (86.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:82:ca:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-82-CA-11-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Even I can see the differences in the HD install are changes in the eth0 and a second eth0 (followed by "avahi"), but is this the problem, and if so, how do I solve it. 

Last detail, if it's any help. When running from Live CD, during boot up, I can see the green light on the ethernet plug go off for a few seconds, then click back on... I'm assuming as it is detected as hardware. With the HD install, the green light is always on during boot up.

Any help would be greatly appreciated since I really want to help my friend get away from Vista, which has been killing him. Having no internet would be a big problem for him though.

---

### Post by superprash2003 on 2008-06-13
go to system->administration->network and go to eth0 properties and set it to DHCP instead of roaming mode.. you may want to reboot incase it still doesnt work..

---

