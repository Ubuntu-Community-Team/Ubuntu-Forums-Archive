---
title: "Ralink rt2500 Feisty not working with Feisty/network-manager"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by theb4ron on 2007-09-06
I've gathered from reading around that there's an incompatibility with ralink rt2*00 cards in feisty's network-manager.

I'm really a linux newb. I've played and dabbled in it in the past, but I only have just-beyond-total-beginner's knowledge, and I'm having an incredibly hard time getting it to work with the solutions I've read.

I've done searches on these forums and what I've read 
Does anyone know a good place to start or have a solution that worked for them?

Thanks!

---

### Post by kevdog on 2007-09-06
You are right about the network manager / rt card conflict.  Here is what I would suggest:

1. Driver - I would reinstall your driver using the serial monkey rt2500 driver.  Do a search in the networking forum for rt73 serialmonkey written by deprius.  His instructions are for the rt73 driver, but it sounds like you are using the rt2500 drivers.  No problem, use some common sense, and in places in that thread substitute rt2500 where he uses rt73.  Its worked for many people before you, so I know you can do it!

2. If you need a graphical networking management utility, similar to network manager, you have 2 choices
a. rutilt
b. WICD

rutilt -- the sources can be found on the serial monkey homepage
wicd - another graphical gui.  I cant say that Ive personally tried this with the rt2500 series driver, but I think it works according to the creator.   I think you can install both, so you could try both out and make up your mind.

---

### Post by theb4ron on 2007-09-07
Thanks kevdog for the advice --  I followed diepruis's howto ([http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)) up to step 14, where it says I should find a wlan1 or wlan0 in my ifconfig -a.

This is my result:
```

aaron@aaron-laptop:/usr/src/rt2500-cvs-2007090713/Module$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:0D:2E:BD:82  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe2e:bd82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13708359 (13.0 MiB)  TX bytes:633899 (619.0 KiB)
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ra0       Link encap:Ethernet  HWaddr 00:13:D3:75:92:29  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1245200 (1.1 MiB)
          Interrupt:21 Base address:0xc000 

```

Is the ra0 the same as a wlan0 or wlan1? Should I really be seeing a wlan0 or wlan1?

---

### Post by theb4ron on 2007-09-07
Got it from there -- I'm up now, for about 3 minutes at a time...

It recieves and IP and I'm able to browse/im/etc. for that short period of time, then it stops working.

Do you know why the connection would be dropping out?

I can still do a *iwlist ra0 scan* and see my network and all the neighborhood networks so I'm pretty sure that everything remains right with the driver for the card.

If i run another *sudo dhclient ra0* i get this as a result: 
```
There is already a pid file /var/run/dhclient.pid with pid 6348
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:13:d3:75:92:29
Sending on   LPF/ra0/00:13:d3:75:92:29
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.1.107
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.872/0.872/0.872/0.000 ms
bound: renewal in 41808 seconds.

```

But I'm not actually connected to the internet. Help? :)

---

### Post by super61 on 2007-09-07
with Feisty i got a umm wmp54g linksys wireless pci card if this is what you got just use the manual not roam input everything and restart and it should work. if not move closer to the router     

 by the way does know how to check the chipset in linux? i forget to much :)

oo my card reads ro1 or ra1 its wired how that works

---

### Post by kevdog on 2007-09-08
please post lshw -C network

how are you bringing your network up?

---

### Post by super61 on 2007-09-08
> **kevdog said:**
> please post lshw -C network

how are you bringing your network up?

heres mine if you where talking to me 
 ```
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: f
       bus info: pci@00:0f.0
       logical name: ra1
       version: 00
       serial: 00:18:f8:2e:3f:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS ip=192.168.0.104 latency=64 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:c0008000-c000ffff irq:10

```

hay theb4ron the company changes chipsets every o year or 6 months i dont know why

---

### Post by kevdog on 2007-09-08
OK, I guess there was a whoops with the information you were telling me.  Again the title of the thread was rt2500, but the operating system is associating the rt61 driver with your card and not the rt2500.  This tells me in all likelyhood you have a ra chipset that uses the rt61 driver and not the rt2500 driver.  Which unfortunately means redo what you just did, instead use the rt61 rather than rt73 or rt2500.

---

### Post by theb4ron on 2007-09-08
kevdog, if you were talking to me...

```
aaron@aaron-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:2e:bd:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.107 latency=64 maxlatency=11 mingnt=52 multicast=yes
       resources: ioport:d800-d8ff iomemory:dfffc000-dfffcfff irq:21
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:13:d3:75:92:29
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:dfff8000-dfff9fff irq:21

```

i'm connecting to a wrt54gs which is functionally identical to a normal wrt54g, i think.

---

### Post by kevdog on 2007-09-08
Sorry mixed up the posters, you are fine, looks like everything is working for you

---

### Post by mastergunner on 2007-09-08
......

---

### Post by theb4ron on 2007-09-08
> **mastergunner said:**
> ......

Eh?

My driver issue seems resolved but I'm still trying to put my finger on exactly why i'm being dropped from my network after just a short period of connection. Should I start a new thread about that?

---

### Post by super61 on 2007-09-08
well i have a thery with linux. you need a PCI card and not a mini pci card for it to fully work probably. i think    

lol sorry kevdog for the mix up i didnt know if you where taking to me or what:lolflag:> Eh?

My driver issue seems resolved but I'm still trying to put my finger on exactly why i'm being dropped from my network after just a short period of connection. Should I start a new thread about that?

well if you sending packets with less the 60 kb then they are dropped by the router with no questions so that maybe it

---

