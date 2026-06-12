---
title: "[SOLVED] DNS Problems / Strangeness in Gutsy"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by badmedic on 2007-10-23
I am a total linux newb, so please bear with me... I could really use some help and will try to be as thorough as possible! :KS

I have been combing through posts of similar issues to mine, but have yet to find  solution that works.

I am having an issue with my wired networking in a new install of Gutsy. The machine in question is a built from a Shuttle SS21T barebones and has an SiS chipset. The lan is an SiS 190...

I set the system up to dual boot w Vista and had trouble with the Ubuntu install... it turned out it would hang with the network cable plugged in, so I unplugged and managed to get it installed.

I then found that I couldnt really get anything to update properly and I can't really use FireFox. I say "can't really" because for some reason, Google servers resolve fine! (Search, Gmail etc.) Any other site just hangs up.

I am pretty sure the issue is local to the machine and not my router because the laptop I am writing this on is also a new Gutsy install from the same CD and I have no problems.

So far I have tried:

[LIST]
[*]Hard coding DNS servers in Ubuntu... both through the gui and through prepend in dhclient.conf (openDNS IPs)

[*]Hard coding the DNS servers in my router... just in case (openDNS IPs)

[*]Disabling IPv6, both in the system and in Firefox.
[/LIST]

A bunch of technical info from the machine (along with the commands I got it all from) follows... Please help!

lspci -nn

00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 761/M761 Host [1039:0761] (rev 02)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:0004]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] [1039:0966] (rev 59)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter [1039:0190] (rev 01)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7950 GT] [10de:0295] (rev a1)


sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 01
       serial: 00:30:1b:42:9f:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.2.15 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s


sudo ethtool eth0

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000037 (55)
        Link detected: yes


ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:30:1B:42:9F:1E  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe42:9f1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:791 errors:83 dropped:0 overruns:0 frame:83
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532507 (520.0 KB)  TX bytes:96033 (93.7 KB)
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by badmedic on 2007-10-23
I should probably add... attempts at updating package sources fail (time out).

Also, I can ping either IPs or domain names and both work fine. No slowness there! Ping seems to be the only network function thats working well on the system.

Thanks again in advance for any help or ideas!

---

### Post by Ewzzy on 2007-10-23
I've been having the same problem.  I can connect under windows, but under gutsy I can't get anything.

---

### Post by badmedic on 2007-10-24
Yeah, it is frustrating. I am starting to debate an attempt at Feisty, not that I have much confidence an older version will work. It's that or just giving up and living in an MS world for now. :(

---

### Post by detroitrockcity on 2007-10-24
> **badmedic said:**
> Yeah, it is frustrating. I am starting to debate an attempt at Feisty, not that I have much confidence an older version will work. It's that or just giving up and living in an MS world for now. :(

Just so you know.. my DNS always works in all Microsoft products... UNTIL I boot the OS. :lolflag:

---

### Post by badmedic on 2007-10-24
Not sure how that helps... but thanks for replying.

Anyone out there with a working sis190 Lan? I could really use some help. :(

---

### Post by badmedic on 2007-10-24
Wow!!! I finally got it... all I needed was

sudo ifconfig eth0 mtu 1492

---

### Post by badmedic on 2007-10-26
p.s...
To make the change permanent, I added the following line to /etc/network/interfaces

pre-up /sbin/ifconfig eth0 mtu 1492

---

### Post by jetpeach on 2007-10-26
wow! thanks, i was having a problem where sites would redirect and BECOME google
for example, i'd click my bookmark to zoji.com and it would show the google.com homepage, it was so wierd. but i typed that command and now it seems fixed. what did that command do?!

---

### Post by magicvince on 2008-03-02
Thanxs, it works for me after 

recompiling my sis191 driver on an ACER M1610 with this how to:

[http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6]("http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6")

Nice

---

