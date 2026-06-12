---
title: "Acer Aspire 4520-5974 Wireless"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by eduf.santos on 2008-06-21
Hello guys, it is my first post here and seeking for help to install my wireless card.

I bought this pc 3 weeks ago and i did a dual boot with win xp. First i installed the 64 bits version of ubuntu and it "didnt work" and then i decided to install the 32bits version and i had the same result :(

I installed it in both version using madwifi/ndiswrapper and at the end i arrived at the same point. Ubuntu recorganise my wireless card and yesterday i could scan the network and even try to connect to it, but today is it not working the scan anymore :(

I'll post my info here

```
eduardo@eduNote:~$ sudo lshw -C network
 *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:2b:c2:48
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       **product: AR242x 802.11abg Wireless PCI Express Adapter**
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:86:35:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

* 1) The strangest think here is that the wireless name is different from the name that windows shows me. When i run windows it tells me that my wifi card is Atheros 5007EG and the name shown above (in bold) is different.

```
eduardo@eduNote:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:68:2b:c2:48  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe2b:c248/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3061440 (2.9 MB)  TX bytes:347043 (338.9 KB)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11200 (10.9 KB)  TX bytes:11200 (10.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:86:35:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f4000000-f4010000 

[B]wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:86:35:ec  
          inet addr:169.254.7.150  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:f4000000-f4010000[/B]
```

* 2) I dont know what this wlan0:avahi do. This is the one interface who gets ip. When i tried with madwifi same think happend just the name of the interface was different (ath0 and atho:avahi). My first thought about it it could be from the bluetooth interface this ip. 
I also tried to disable it, but when i do it, wlan0 disappears from the ifconfig list too

Please can someone help me to solve this problem? I've read a lot of post and followed a lot of how tos and some didnt work and the one that "worked" brings me back to this situation. I'm totally lost here!

---

### Post by josmcc on 2008-06-21
Hi, The best combo for wireless running linux is using ndiswrapper and the windows driver.

For handling wireless connections, encryption, etc.. 
Check out [wicd at sourceforge]("http://wicd.sourceforge.net/").

It's by far the best wireless config utility I've used for linux. I actually uninstalled gnome and knetworkmanager and stick with wicd.
It handles wireless and wired connections.

As far as ndiswrapper is concerned I've sometimes had to install/reinstall the driver

make sure to sudo ndiswrapper -m to load module at startup

---

### Post by eduf.santos on 2008-06-21
Hi josmcc, i´m using ndiswrapper atm, and i puted all modelues to /etc/modules to start up at tne boot time. I really dont know what else i can do make my wifi work. I´ve followed all tutorials, how tos and everyone who works, brings me back to the situation discribed above.

---

### Post by josmcc on 2008-06-21
I started having problems with wifi recently, which led me to use wicd.

I kept losing connection,had to reboot, reinstall ndiswrapper, etc, to get it to work.

I uninstalled network-manager-gnome and knetworkmanager, which I think may have had something to do with it.

The problem with Wlan in linux displaying differently may be due to driver, I'm not really familiar with madwifi, but I think that is a generic driver for atheros chipsets.(that is probably why is displaying wrong) 

I would boot into windows, find which .inf and .sys you need for the wireless network card, and use those with ndiswrapper, then install wicd.

Also, make sure when you install the drivers using ndiswrapper, you are installing driver as root (sudo)

Hope this helps, and you eventually get it to work, I'm kind of new to linux also, but been messing with it on and off for a while and recently decided to stick with it as only OS on my laptop.


From above it looks like you're getting automatic Private Ip for the Wireless card, so it may just be a DHCP issue. Try installing wicd. That is what fixed my wirless issues.

---

### Post by rodneymillerpca on 2009-03-30
I had trouble also with my 4520. Follow this tut and problem solved in less then 15 minutes. [http://www.hp2133guide.com/forums/viewtopic.php?p=10230](http://www.hp2133guide.com/forums/viewtopic.php?p=10230)

---

