---
title: "[SOLVED] Can't get 4965 wireless to work on asus fs3v"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by gzevspero on 2008-04-24
Hi,
I've recently switched from windows to linux and am running ubuntu 7.10 single-boot on my asus fs3v laptop. I've gotten pretty much everything setup properly, except the wireless card. Up until a few weeeks ago I was able to connect to wifi, but only to open networks - but not to any networks with wep or wpa. i tried following the instructions on forum posts to fix this: 

([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188),
[http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller),
others which I unfortunately don't remember)

but I seem to be worse off now than when I started... can anyone offer a newbie some help? Here's where I'm at now:

In network manager I see only the option for wired network - no wireless options, no SSID's detected. I was seeing SSID's before. 

If I go to network tools I see 3 wireless adapters: wmaster0 (shows as "unknown interface"), wlan0, which is configurable, and wlan0:avahi, which has an IPv4 address, but when I click to configure it I get the error "the interface does not exist".

Here is my output for lshw -C network:

  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1b:fc:48:4c:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A ip=192.168.123.172 latency=0 module=atl1 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:25:cf:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g



And this is my ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:1B:FC:48:4C:B9  
          inet addr:192.168.123.172  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe48:4cb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33858 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:76489952 (72.9 MB)  TX bytes:2800412 (2.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:25:CF:A1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:13:E8:25:CF:A1  
          inet addr:169.254.8.180  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-25-CF-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Why do I have three wireless interfaces? Do I need to use ndiswrapper with this driver, even though iwlwifi is native (as I understand...)? Any advice would be much appreciated... 

Thanks.

---

### Post by jpeach on 2008-05-15
So, you have solved the problem?  What got it working?  Also, when you move to 8.04 there is a new driver for that wireless card

---

### Post by gzevspero on 2008-05-15
While still running 7.10 I got it to work after installing wicd: [http://wicd.sourceforge.net](http://wicd.sourceforge.net). Used the iwlwifi 4965 drivers from the intel site.  
After upgrading to 8.04 though, network manager worked fine out of the box, WPA and all, and that's what I've been using without problems for a couple weeks now.

---

### Post by balagosa on 2008-05-15
> **gzevspero said:**
> While still running 7.10 I got it to work after installing wicd: [http://wicd.sourceforge.net](http://wicd.sourceforge.net). Used the iwlwifi 4965 drivers from the intel site.  
After upgrading to 8.04 though, network manager worked fine out of the box, WPA and all, and that's what I've been using without problems for a couple weeks now.

kudos to Asus fs3v user.

hmmm...gzev, does your lspci really list intel 4965 wireless?

---

