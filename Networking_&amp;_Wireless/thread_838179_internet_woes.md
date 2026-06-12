---
title: "internet woes"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by ub520 on 2008-06-23
my laptop will not connect to the internet at all.
I tried ifconfig and got these results

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:12:70:bf  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:260555 (254.4 KB)  TX bytes:1679 (1.6 KB)
          Interrupt:18 Base address:0xe800 

eth0:avahi Link encap:Ethernet  HWaddr 00:03:0d:12:70:bf  
          inet addr:169.254.5.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141512 (138.1 KB)  TX bytes:141512 (138.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:76:c9:f7:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-76-C9-F7-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

my card is an sis900 and my modem sbv5220 cable

---

### Post by superprash2003 on 2008-06-23
are you trying to connect wirelessly or wired?

---

### Post by ub520 on 2008-06-23
Both and both give me problems

---

### Post by ub520 on 2008-06-23
Bump: I need help still.

---

### Post by darkreaction on 2008-06-23
did u disconnect the wired connection while trying to connect wireless?

---

### Post by superprash2003 on 2008-06-23
right . .better try one thing at a time.. to better troubleshoot the problem

---

### Post by SpaceTeddy on 2008-06-24
OK, slowly please (i need time to understand)...

just to clarify your network connection status... do you use network manager ? if so, do the wifi network appear in it ? If that happens, it would be a good thing. Make sure you have no cable attached and then try to connect to the wifi. If this does not work, disable your wifi (with the little switch on your laptop) and try the wired. When you plug the cable in, do the little leds on the nic become active ? does the light on the switch/router/modem come on that says your computer is plugged in ?

If all this happens, and you still get no connection, could you please post the output of the following command to get an overview on how your system is currently configures its network cards at boot time.
> cat /etc/network/interfaces

Also, how are you connected to the internet ? do you have a router, do you plug into a modem directly ? do other operating systems work and just not ubuntu - or do all of them fail ?
Do you have to dial on when you use a different Computer/OS or does the connection appear automaticially ?

I know, these are a LOT of questions... i am just trying to ask as much as possible to get the best overview of the situation. The more information is provieded, the easier it gets to (hopefully) solve a problem.

Hope we can figure this out :)

---

### Post by ub520 on 2008-06-25
wifi doesn't work, it shows up but it doesn't work.
the Ethernet port for some reason doesn't have a nic light but the cable works on all other computers (which run xp or vista)

I have a an always running road runner cable modem. no router, and yes i do use network manager on othe vista computer (the only one connected to the net is has online a boot-up so no dial-up

i'll try that command thingy and report with the results.
oh I forgot i'm using mint ellysa but it has the same networking tools.

---

