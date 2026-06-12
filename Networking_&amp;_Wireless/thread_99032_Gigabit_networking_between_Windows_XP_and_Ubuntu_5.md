---
title: "Gigabit networking between Windows XP and Ubuntu 5.10"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by Mathboy on 2005-12-04
**OVERVIEW:**
I'm trying to connect my Windows XP computer to my Ubuntu server via Gigabit networking. 
Things appear to be working, but the speed of the connection copying a file from Windows to Ubuntu is terrible (~1Mb/s, both through samba and through scp). Going the other way (copying from Ubuntu to Windows) is fine - about 30Mb/s.
I know this may be a Windows issue, but thought the kind-hearted Ubuntu community might be willing to shed some light anyway :) 

**HARDWARE:**
The Ubuntu machine has a realtek 8169s based card in it, and the windows machine is using the on-the-motherboard Nvidia nic. They're connected directly through cat6-crossover (no switch). Ethtool and ifconfig output is copied below.

**THINGS TRIED:**
- Knoppix on the windows box: this works well, with ~15Mb/s knoppix->ubuntu through scp. So I guess it's not a hardware problem.
- Different cables: 5 have been tried, some cat 6, some cat 5e, all work identically
- Different NIC in the windows machine: I've tried a Marvell Yukon and it behaves identically to the NVidia.
- Running through a 10/100 switch: The gigabit cards both report 100Mbps full duplex, and the throughput INCREASES from 1Mb/s (gigabit) to about 5Mb/s (100Mbps)!
- Updated drivers on windows box: Put on the latest - no difference.


**QUESTIONS:**
1) Does anybody have this configuration (Windows->Ubuntu file transfers over gigabit ethernet) working well?
2) Are there magic driver settings I should be using? (both have 1500 MTU).
3) Any hints on diagnostic methods for this kind of thing?


**UTILITY OUTPUT:**

Ethtool:
> 
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Link detected: yes



Ifconfig: 
(The number of dropped packets doesn't increase - it's probably from when I was messing with cables while trying to get it to work.)
> 
eth2      Link encap:Ethernet  HWaddr 00:08:54:3F:3C:38
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe3f:3c38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2770001 errors:0 dropped:73 overruns:0 frame:0
          TX packets:1216509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3629837264 (3.3 GiB)  TX bytes:1317305852 (1.2 GiB)
          Interrupt:18 Base address:0xc000


---

### Post by Mathboy on 2005-12-05
Update:

I've disabled NetBIOS over TCP/IP, and turned off the internet connection sharing service (there's a Microsoft knowledgebase article about  high speed netwroking in XP SP2 being munted by that service). Sadly it made no difference.

I also tried iperf, and surprisingly the results seem fine!

Gigabit:
557 Mbit/s  --   Ubuntu -> Windows 
406 Mbit/s  --   Windows -> Ubuntu

10/100:
94 Mbit/s  --  Ubuntu -> Windows
87 Mbit/s  --  Windows -> Ubuntu

**So why is iperf fast and both scp and samba so slow?!** :confused:

---

### Post by Mathboy on 2005-12-06
I have just reinstalled windows and put in a new network card (identical to that in the server - a realtek 8169s card). The problem remains the same. :( 

However, by changing the following in Ubuntu I am able to get it going only a little slower than 10/100 (it's scary that it has come to that being a good thing!):

With ifconfig:
- MTU 7000
- txqueuelen 10000

Editing files in /proc/sys/net/core:
- rmem_max and wmem_max 16777216 (16Mb)
- netdev_max_backlog 2500


I think the performance issue must be further setting or driver issues on the Ubuntu machine.... 
Any help would be *much* appreciated!

---

### Post by Mathboy on 2005-12-06
Finally got this working - looks like this issue was a jumbo frame size mismatch! 7000 is not a good size to be using in Ubuntu - it must match the size used by other adapters on the network.

I've started a new thread with the results of my experiments:
[http://ubuntuforums.org/showthread.php?t=101117]("http://ubuntuforums.org/showthread.php?t=101117")

---

