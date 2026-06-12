---
title: "Cannot connect to internet / network in 6.10"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by zreon on 2007-06-24
Hey all! I installed ubuntu 6.10 about 7 hours ago with hopes of installing linux MCE and begin configuring everything. Well immediately after installing ubuntu I ran into a wall. It won't connect to my internet or network.

Here is my current setup

DFI Lanparty Ultra D
Amd 2500+
256mb ram
Nvidia Ti-4200
Linksys BEFSR41  router

2 built in NIC's on motherboard. Neither one will connect.

One of them has data link lights but they won't turn on.

I have tried using DHCP and static with no luck on either.

Also, I have read probably 20+ threads on here about the same problem, but still no luck.

Can anyone please help me with this? My experience with ubuntu isn't going very well so far :(

---

### Post by zreon on 2007-06-24
bump

---

### Post by Chappy7777 on 2007-06-24
I am having the same problem, except I am using a dialup external serial modem, so I can only share your pain. Also, this will give you a free bump. :)

I originally had 6.06LTS installed, and it autodetected my modem and away I went. Conneck was easy and fast.

Then I installed 6.10 (hoping for newer versions of programming), and I immediately had the problem of there being no autodetect. After messing around for awhile, and posting on here w/no answers, for some reason, I reinstalled 6.06, back on the net. I am still using 6.06, but the other day I loaded Feisty on another HD and had the same problem as I had w/6.10. I don't know why Ubuntu changed the modem/internet setup from the way it was in 6.06. 6.06 is the last version to have an autodetect box. 

Anyhow, good luck. If you were using dialup I'd suggest getting a copy of 6.06. But since you're not, well, maybe someone else will answer you more directly!

---

### Post by Chappy7777 on 2007-06-24
Quick thought here. Does your ISP support Linux? They don't all do so, or so I have read in the stickies. Is this your 1st try w/Linux? If it is, and you're only 7 hours into it, then just having it running and finding where to try and get the net connected is doing ok. It ain't that Linux or Ubuntu is hard, it's just that you likely have years of Windozing to overcome. Hang in and read these forums. Google your question over cyberspace. You'll get connected.
If you are a total newbie to Linux, get a copy of "Ubuntu for Non-Geeks" by Richard Grant. If you are a geek, get it anyhow. It comes w/a copy of 6.06 on the back cover. That was the best PC investment I ever made, I think.

---

### Post by linuxonbute on 2007-06-24
Are you sure you are using a straight cable and not a crossover cable.

See the last few posts in this thread
  [http://ubuntuforums.org/showthread.php?t=480051](http://ubuntuforums.org/showthread.php?t=480051)

---

### Post by zreon on 2007-06-24
This isn't my first linux experience. I have messed with it for quite a while in the past so I know its not my internet.

Also, I have tried both types of wires.

---

### Post by zreon on 2007-06-25
anyone?

---

### Post by Rui Pais on 2007-06-25
Hi, 
its late here i can't help much today, but...

In order to anyone can help you must give more information.
Whats the output of:
```
lspci |grep net
```
```
ifconfig
```
```
cat /etc/network/interfaces
```

---

### Post by zreon on 2007-06-25
ifconfig

```
david@Linux-Media-Center:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:82:79:9E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:01:29:82:75:DE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1087015 (1.0 MiB)  TX bytes:1087015 (1.0 MiB)

```


lspci

```
david@Linux-Media-Center:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

```

I'm not sure how to do the "|" in "lspci |grep net"

---

### Post by kevdog on 2007-06-25
lshw -C network

---

### Post by zreon on 2007-06-25
lshw -C network

```
david@Linux-Media-Center:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:01:29:82:79:9e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth multicast=yes
       resources: iomemory:e0086000-e0086fff ioport:b000-b007 irq:193
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@01:0c.0
       logical name: eth1
       version: 10
       serial: 00:01:29:82:75:de
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 multicast=yes
       resources: ioport:a400-a4ff iomemory:df001000-df0010ff irq:209

```

---

### Post by kevdog on 2007-06-25
Could you post:
/etc/modprobe.d/blacklist

---

### Post by zreon on 2007-06-26
It appears that both built in network cards are not functioning. I just installed windows and both of them say the network cable is unplugged, yet the cable works in the computer right next to it.

---

### Post by Rui Pais on 2007-06-26
it looks like an ipv6 incompatibility 

try:
```
gksudo gedit /etc/modprobe/blacklist
```

and add to the  file:
```
blacklist ipv6
```

reboot and check.
Note that restart network it's not enough you need to reboot to unload ipv6 module.

Good luck.

---

### Post by Chappy7777 on 2007-06-26
> **zreon said:**
> It appears that both built in network cards are not functioning. I just installed windows and both of them say the network cable is unplugged, yet the cable works in the computer right next to it.
 
Obvious question here, I'm trying to help so don't get miffed. I've made more obvious mistakes myself. We're all human.

Anyhow, have you checked the BIOS in this machine to see that your network is enabled? 

Just a thought, since as you say, it works on the other PC. Not all that likely that both network cards would croak at the same time.

---

