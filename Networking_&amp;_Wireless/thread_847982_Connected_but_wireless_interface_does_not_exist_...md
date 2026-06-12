---
title: "Connected but wireless interface does not exist ..."
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2008-07-03
Hi all.

Been looking around for a solution to this rather odd problem. After spending months on and off trying to get the Broadcom Bcmwl94311 wireless card up in my HP dv6000 AMD TurionX2/64 machine in Gutsy, while I have a break from uni I loaded Hardy 8.04. Wired connection has always worked no problem but once I loaded the updates after install of Hardy, I was asked a few questions by the system about my wireless card (I was about to start tackling ndiswrapper again!), a few things were downloaded (fw-cutter and b43 driver then installed automatically). Asked me to reboot and as it was shutting down, I noticed the blue light had come on! Yea!! Love you Hardy and congratulations to Ubuntu-eers everywhere. Goodnight vista once and for all!

So, all seems to be fine in wireless world except for an odd thing. When I open Network Tools, tells me all is well with wlan0, but when I try to configure tells me device does not exist. On further investigation, in Connection Properties, also tells me all is well. Below are results of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Slynn"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:84:AF:26   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=73/100  Signal level=-57 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:24:02:b9:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9900 (9.6 KB)  TX bytes:9900 (9.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:2b:0e:9f  
          inet addr:192.168.0.162  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe2b:e9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2001104 (1.9 MB)  TX bytes:217155 (212.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-2B-0E-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

As I say, all seems to be working well and I am online no problem, probably nothing, but not being able to configure through Network Tools is odd. My speed does also seem to fluctuate quite radically, but this could be my cable provider (they have been unusually unpredictable this last week).

Hoping someone may have an explanation, as simple or complex as that maybe. Happy to provide any further info ...

---

### Post by Bucky Ball on 2008-07-03
Silly me. Probably doesn't exist because it is virtual, yes??? ;p

---

