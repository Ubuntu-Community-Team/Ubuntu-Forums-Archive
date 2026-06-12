---
title: "wifi device now showing up in network-manager"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by cartucho on 2006-10-28
Hi i have an acer 5102, its a athero card.

i cant make the wireless work through command line, but im trying to put network-manager to work,

but it shows up only my wired interface, for some reason my wireless interface is not being showed up in network manager.

obs: i removed the "auto" entry for the interfaces as described in the how to.

The system is a edgy X86 64

follows some outputs:
cartucho@newton:~$ uname -a
Linux newton 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux


cartucho@newton:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:16:CF:29:92:B9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:15:FD:88  
          inet addr:192.168.8.4  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe15:fd88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6376538 (6.0 MiB)  TX bytes:546009 (533.2 KiB)
          Interrupt:233 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-29-92-B9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20166 errors:0 dropped:0 overruns:0 frame:98663
          TX packets:2273 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1617649 (1.5 MiB)  TX bytes:107246 (104.7 KiB)
          Interrupt:50 Memory:ffffc20000060000-ffffc20000070000

---

### Post by cartucho on 2006-10-28
im very sorry
for some reason it started working, sorry again.

thanks.

---

