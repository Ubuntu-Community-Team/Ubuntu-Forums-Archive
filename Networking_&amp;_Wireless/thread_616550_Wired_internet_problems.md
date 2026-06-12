---
title: "Wired internet problems"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Michaelmeee on 2007-11-18
I'm having some problems with getting a connection through my Ethernet port and I have absolutely no idea what's wrong with it.

Specs:
Pentium 4 3.0ghz
Geforce 5200FX
512MB Ram
ASUS P4S800 motherboard

I've tried the commands  ifdown eth0, ifup eth0 and dhclient eth0 but it doesn't really tell me anything useful, in a minute I'll boot up into Ubuntu again and post the results of both of those here. What's weird is that a few months ago on Ubuntu my wired connection worked fine, no hassle or anything, yet now nothing happens.

I have it set it up to look for DHCP automatically, but still nothing. I'm using a BTHOMEHUB from err... British Telecom of course. My wired connection works fine in Windows and on my Xbox 360 so I'm not sure what the problem is. Anyways, I'll post the results of ifconfig and dhclient eth0 in a few minutes.

Thanks!

EDIT : Oh, totally forgot, the problem is that when I try to access any website it doesn't work at all. I can't ping anything, I can't go to any websites, I can't even connect to my own modem. Can't believe I forgot to type that. Anyways, here's the results to the commands...

```
michael@:~$ **sudo ifdown eth0**
There is already a pid file /var/run/dhclient.eth0.pid with pid 4510
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:d8:5c:6c:4c
Sending on   LPF/eth0/00:11:d8:5c:6c:4c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

michael@:~$ **sudo ifup eth0**
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:d8:5c:6c:4c
Sending on   LPF/eth0/00:11:d8:5c:6c:4c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
SIOCADDRT: No such process
bound to 86.141.149.195 -- renewal in 35359 seconds.

michael@:~$ **sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:d8:5c:6c:4c
Sending on   LPF/eth0/00:11:d8:5c:6c:4c
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
SIOCADDRT: No such process
bound to 86.141.149.195 -- renewal in 37196 seconds.

eth0      Link encap:Ethernet  HWaddr 00:11:D8:5C:6C:4C  
          inet addr:86.141.149.195  Bcast:86.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3390 (3.3 KB)  TX bytes:8599 (8.3 KB)
          Interrupt:18 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by Blutack on 2007-11-18
Could you please try running
sudo route add default gw 192.168.1.254
?

---

### Post by Michaelmeee on 2007-11-18
```
michael@:~$ sudo route add default gw 192.168.1.254
SIOCADDRT: No such process

```

That doesn't sound good. If I take a while to reply it's because I have to change from Ubuntu to Windows to send this. Would use the laptop but it's currently in use at the moment.

---

### Post by Blutack on 2007-11-18
Uh-oh, looks related to this
[http://ubuntuforums.org/showthread.php?p=3652430](http://ubuntuforums.org/showthread.php?p=3652430)
On the plus side, it should work with feisty.  Do you use network manager?
could you post any juicy bits from
/var/log/daemon.log

---

### Post by Michaelmeee on 2007-11-18
I tried using the Network Manager to see if I could get it working through that, I could try adding that I.P to the gateway list through that too.

Oh, and I forgot to say I'm using 7.10. So, I'd have to download Feisty and install that instead? I'll see what the daemon.log says, but I think I'll most probably try 7.04 first, got nothing to lose have I?

---

### Post by Blutack on 2007-11-18
Don't bother installing it, if you have a feisty live cd lying around try that and see if it works.  If the live cd doesn't work an install probably won't either.  Still, its a rubbish solution :(
If feisty works and there is no obvious fix forthcoming you could try downgrading certain related packages to feisty level - I think dhcpd is most likely a culprit but figuring out the packages required would be tricky.  See if feisty works first.

---

### Post by Michaelmeee on 2007-11-18
Yeah I'll just be using a Live CD. I'll try it tomorrow and keep you posted on what happens, if it does work I'll get rid of 7.10 and if it doesn't I'll just wait until a fix becomes available, if it does. Is a bit of a shame that this had to happen though, I was actually looking to fully switch to Ubuntu for a month to see if I could fully replace Windows. Thanks for the help! :)

---

### Post by Rev60073 on 2007-11-18
Are you running roaming mode in your Network applet?

I noticed myself, when I set it up for manual configuration, and select DHCP, I cannot get a DHCP address from my router, bringing the interface down/up doesn't seem to trigger a DHCP request.

When I have it set up as roaming mode, things work fine.

---

### Post by Michaelmeee on 2007-11-18
I think I tried roaming mode once or twice, it didn't make a difference. I might boot up into it again later and give it a quick try though. :)

---

### Post by Michaelmeee on 2007-11-19
Sorry to double post, but I thought I'd give you an update. I tried the 7.04 live CD and it did the exact same thing, it still said "SIOCADDRT: No such process." which is a big disappointment. I hope it isn't a specific problem with my type of motherboard or something.

---

### Post by kevdog on 2007-11-19
What driver are you using??

Please post lshw -C network

---

### Post by Michaelmeee on 2007-11-20
Sorry for the long wait!

```
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:11:d8:5c:6c:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=86.141.149.195 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s


```

I also tried a Sabayon live disk to see if it would do it with that as well, and once again I had no internet which was strange. The only thing I can remember changing from when I used Ubuntu before and now was that I updated my BIOS. I would try to revert to what I used before but my floppy drive doesn't work, so I have no way of updating.

---

