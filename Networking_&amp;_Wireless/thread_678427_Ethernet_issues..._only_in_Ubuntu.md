---
title: "Ethernet issues... only in Ubuntu"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by halfmike on 2008-01-25
I'm about to give up on Ubuntu.

So I first installed Ubuntu about 5 months ago, as a dual boot with my XP, but the big problem with it was that every time I tried to download a file, such as a regular firefox download or upgrading ubuntu, the internet connection would time out. To download updates, I would have to start downloading them, after they were about 1/16th of the way done, the connection would time out, so it took me a munite to restart, and then I got 10 seconds worth of downloading before it times out, and then it times out so I had to do upgrading in 10 second intervals, downloading things took me hours. This also happened with just loading pages, but not as often.

So then I give up on linux, because my windows xp seems to always work fine after i've installed the correct driver from the dell driver CD, no problems whatsoever. However, I decided after petitioning school about installing Ubuntu on school computers and witnessing my friend's awesome laptop and his steady internet connection, I backed up all my data, formatted my HD and never looked back...

...Until now. I have 185 upgrades, and I get about 4 at a time before my internet goes down. This has made me so frustrated; it seems some others have the same problem but everyone tells them that it's their hardware, or the cables, ect. However, I **know** that this is Ubuntu's fault, but I want to fix it cause I love everything else about Ubuntu.

tl;dr:
Ethernet fine on windows
will not download anything on ubuntu 7.10 without timing out after about 10 seconds (including upgrades)
i am very frustrated, as I just formatted my HD and only wanted this to work

P.S: I think i've read every other article, but nothing seems to work
P.P.S: I'm pretty sure it's intel 10/100 pci, and a belkin router

---

### Post by halfmike on 2008-01-25
So I do not what to jinx it, but it it working now, I just updated the firmware, and it works.

:popcorn:

---

### Post by halfmike on 2008-01-25
Hmm... all that does it that it doesn't reset or upgrade the firmware but it buys me about 30 minutes of uninterrupted downloading :confused:.

---

### Post by Hightide on 2008-01-26
Hi Halfmike

I know its very frustrating  but have a look at this thread which highlighted a similar problem with no ethernet connection.

[http://ubuntuforums.org/showthread.php?t=673528](http://ubuntuforums.org/showthread.php?t=673528)

regards
:)

---

### Post by ugm6hr on 2008-01-26
> **halfmike said:**
> P.S: I think i've read every other article, but nothing seems to work
P.P.S: I'm pretty sure it's intel 10/100 pci, and a belkin router

If you want people to help, you need to give us some information to start with:

```
lspci
lshw -C network
ifconfig
route -n
```

Re: your Belkin router - do you use a static IP or fixed IP?

Do you have roaming enabled in the Network settings (System-> Administration-> Network)?

It is unusual to have ethernet problems that can't be fixed with Linux.  Intermittent internet problems are even more unusual - but it is entirely likely that Network Manager is doing something unusual that causes it to drop connections.

---

### Post by halfmike on 2008-01-26
> Do you have roaming enabled in the Network settings (System-> Administration-> Network)?
I've tried both ways,roaming and dhcp, they both act the same.

> Re: your Belkin router - do you use a static IP or fixed IP?
The IP from comcast is dynamic, i think it's fixed.

LSPCI
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
02:0c.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
03:08.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
03:09.0 USB Controller: NEC Corporation USB (rev 41)
03:09.1 USB Controller: NEC Corporation USB (rev 41)
03:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:c6:43:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.2.4 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:07:E9:C6:43:A5  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fec6:43a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9255050 (8.8 MB)  TX bytes:828110 (808.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by ugm6hr on 2008-01-26
Hmmm... I can't see anything that looks abnormal in all that. :confused:

---

### Post by halfmike on 2008-01-26
Hmm, well maybe its synaptic or update manager because that's what kicks me off the internet.

---

