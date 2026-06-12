---
title: "How to configure network setting? How to connect to internet? HELP ME!!!"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by ann pic on 2008-01-24
I am beginner and i just install my ubuntu 7.04. The problem is i cannot connect to internet. I already try on my own to configure the network setting but still, failed. i got two operating system in my cpu. When i swith to windows it will automatically connected to the internet, IP address is assigned automatically. But when i switch to Linux, no network is detected. Is that any network software that i need to install?

when i run the command ipconfig in the terminal, the output produced is only as below:

lo     Link encap: Local Loopback
       inet addr:127.0.0.1 Mask 255.0.0.0
       inet6 addr: : :1/128 Scope: Host
       up LoopBACK RUNNING MTU:16436 Metric:1
       Rx packets:122 errors:0 dropped:0 overruns:0 frame:0
       Tx packets:122 errors:0 dropped:0 overruns:0 carrier :0
       collisions:0  txqueuelen:0
       Rx bytes:9484 (9.2kiB)  Tx bytes:9484 (9.2Kib)

---

### Post by NullHead on 2008-01-24
Hello could you please post the output of ```
lspci
``` This will help us determine the exact hardware and how to make it work. :)

---

### Post by ann pic on 2008-01-24
the output of the command of lspci is as below:

ann@anndesktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02)
00:03.0 Communication controller: Intel Corporation Unknown device 29c4 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 294c (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.1 PCI bridge: Intel Corporation Unknown device 2942 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2912 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
06:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE1394a2000
Controller
(PHY/Link)
ann@anndesktop:~$

---

### Post by nmartine on 2008-01-24
What type of machine are you using?? Or did you build this one yourself.

---

### Post by NullHead on 2008-01-24
wow ... yes please tell what computer model and or parts are you using. It seems there is allot of hardware being undetected.

---

### Post by ann pic on 2008-01-24
I still find my resit of payment of my pc. But generally, the parts are: 
-using dual2cuo processor
-intel motherboard
-ddr2 memory 
-Intel(R) 82566DC-2 Gigabit Network

---

### Post by ann pic on 2008-01-31
-Team DDR2 
-Intel Core 2 duo
-TS8555 WG
-Intel DG33FB

---

