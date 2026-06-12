---
title: "Internet barely usable"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by portach king on 2008-05-27
Hi guys,
I'm having major trouble with my wireless at the moment. I'm using a Edimax Eg7318Ug USB dongle to connect online. I plugged it in and it worked fine, however suddenly as of this morning it's been acting strangely. It connects but whenever it starts to download anything my computer slows down to a chugging speed to the point hat I can't use it at all. This happens with websites that use flash etc and is is extremely unsettling. 
Can anyone help? The only thing I can think that has changed is a 59Mb system update I got yesterday, but I don't remember having any troubles after my initial reboot after that.
I'd hugely appreciate some insight. Thanks guys!

---

### Post by portach king on 2008-05-27
The problem seems to be that wheneven the computer starts to download anything it slows down the computer, not nessecarily the connection. The computer crawls and the fans spin very loudly. The USB dongle uses the ralink drivers (which comes inbuilt with Hardy, right?) so I'm not sure what the problem is. 
Again, as I said, I'd greatly appreciate any help, this is extremely fustrating. I feel like I'm always trying to fix wireless with Ubuntu.

---

### Post by mapes12 on 2008-05-27
Have you had a look here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59)

and here:

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by portach king on 2008-05-27
Thanks mapes12, but they don't seem entirely relevent to my problem. 
My card did work fine up until this morning.

---

### Post by mapes12 on 2008-05-27
If you follow the links they will take you progressively through issues such as driver misconfiguration where the card works OK at first but over time it breaks down. Particularly, if you have a ndiswrapper driver but the kernel has loaded a native driver as well.

What do you get from this

```
sudo lshw -C network
```

---

### Post by portach king on 2008-05-27
```
 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:76:7d:eb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:0e:2e:4b:19:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:19:4a:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

I'm not using my broadcom card though. I've given up on trying to get it to work (It's seems to be broken), and I'm using the Edimax Usb device to connect wirelessly. I'm not using ndiswrapper btw

---

### Post by mapes12 on 2008-05-27
From what I can see you have 2 wireless cards detected: wlan1 and wlan0

Neither of which are reporting any driver support? so not sure which one is working and what driver whichever is working is using.

Lets see which one is listening to DHCP

```
sudo dhclient
```

What's the output?

---

### Post by portach king on 2008-05-27
I just want to emphasise my problem here once again, as I'm not sure it's very clear.
The problem is not that it doesn't connct, or that i get a slow connection, but rather that when it does connect it slows down my system to the point that I cannot use the computer.
There must be a solution

---

### Post by portach king on 2008-05-27
Just noticed your post, mapes12. Sorry about th delay, an thank you so much for helping. 
Output:
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster1: unknown hardware address type 801
wmaster0: unknown hardware address type 801
wmaster1: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster1/
Sending on   LPF/wmaster1/
Listening on LPF/wlan0/00:14:a5:19:4a:56
Sending on   LPF/wlan0/00:14:a5:19:4a:56
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:0f:b0:76:7d:eb
Sending on   LPF/eth0/00:0f:b0:76:7d:eb
Listening on LPF/wlan1/00:0e:2e:4b:19:a3
Sending on   LPF/wlan1/00:0e:2e:4b:19:a3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.14 from 192.168.1.254
DHCPREQUEST of 192.168.1.14 on wlan1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.14 from 192.168.1.254
bound to 192.168.1.14 -- renewal in 1681 seconds.
```

---

### Post by mapes12 on 2008-05-27
> Listening on LPF/eth0/00:0f:b0:76:7d:eb
Sending on   LPF/eth0/00:0f:b0:76:7d:ebDo you have an ethernet cable plugged in your machine??
> DHCPREQUEST of 192.168.1.14 on wlan1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.14 from 192.168.1.254
bound to 192.168.1.14 -- renewal in 1681 seconds.It's the wlan1 interface which is pulling in the DHCP service.

So, if you have an ethernet cable connected then remove it. Then shutdown the none working interfaces

```
ifdown eth0
```
```
ifdown wlan0
```

Access the internet via Firefox. Any improvement?

---

### Post by portach king on 2008-05-27
I didn't have an ethernet cable connected when I posted the output earlier.
I tried what you suggested but to avail. Still the same problem. Mouse movements are jerky and computer slows down to a practical halt.

---

### Post by portach king on 2008-05-27
I'm quite genuinely surprised that my problem is so unique that I'm not able to find a solution. I'd like to thank Mapes12 for his help so far, and also extend the invitation to anyone else who has any suggestions. 
This problem is pretty much crippling for my laptop which otherwise runs perfectly out of the box.
Again, all help is greatly appreciated.

---

### Post by mapes12 on 2008-05-28
Just some questions:

1. What version of Ubuntu are you running?
2. Did you have a previous version installed and if so did the laptop work OK with it?
3. What make and model is it?

It's just a hunch but I think some of those updates you downloaded may have screwed up you Xserver.

---

### Post by portach king on 2008-05-28
1. I'm running Ubuntu Hardy Heron
2. I've been running Hardy since RC1 and had no trouble with it until yesterday.
3. My laptop is a HP pavilion zv6000.

As I said, my wireless was fine until yesterday, the day after I installed the 59mb update.
Situation has gone from bad to slightly worse since. Now it won't connect at all, network Manager seems to stall on *"Waiting for Network Key"*.
I haven't tried it with Wicd yet (as I've heard that it has problems with ralink cards).

---

### Post by portach king on 2008-05-28
I hate to do this but...
*bump*

I'm still having the same trouble

---

### Post by portach king on 2008-05-29
Im going to bump this again, as I still have not solved this problem

---

### Post by portach king on 2008-05-30
*bump*

This problem is really distressing. is there anywhere else I can go looking for help? Clearly an Ubuntu update has disabled my wireless. I need to fix it.

:(

---

### Post by portach king on 2008-05-30
I've  installed Wicd now. It connects to the network, but the connection is super-slow. :(
I'm close to pulling my hair out with Ubuntu wireless issues. I bought this USB dongle and ditched the broadcom chip in my laptop because it was appearantly linux native. And it worked fine, until Monday and that annoying update came through. I just wish I had an answer as to why it's suddenly not working after this update and if I can fix it.

---

### Post by portach king on 2008-06-02
I'm assuming that nobody has any ideas on how to fix my problem?
If that is the case, I'd even appreciate some advise on where else I could go online looking for help (ie. an irc channel, etc.)
Still though, if anybody has any ideas, as I said, I'd really, really appreciate it.

---

### Post by mapes12 on 2008-06-02
> As I said, my wireless was fine until yesterday, the day after I installed the 59mb update.

IOM something in those updates has crashed your system.

This happened to me when I downladed a mega load of updates and I lost my sound. The only way I could fix it was to reinstall from scratch.

Before I install updates any more I backup my entire system partition using [http://www.clonezilla.org/](http://www.clonezilla.org/) That way, if my system has a problem after the updates I can at least go bag to the Clonezilla version without having to reinstall everything inc added packages again. There's also a good guide here for backing up your system files:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by portach king on 2008-06-03
Cool. I'll do that today then.
Thanks Mapes. I'm going to set up Clonezilla ASAP too. Thank goodness I do currently run my system of two partitions.
One problem though, if I do reinstall should I deactivate all updates? How can I stop it from just happening again?

---

