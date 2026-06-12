---
title: "WMP54GS in 8.04 not working ... losing hair!"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by jyanek on 2008-04-24
UPDATE 4/25/08 -- SOLVED by following this post:
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

UBUNTU boards are great :)

Original post:
* * * * *

I cannot get a connected wireless link after upgrade to 8.04

I am using a WMP54GS card, more specifically:
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

It worked flawlessly in 7.10.  I have upgraded to 8.04 and I cannot get it to work.  My networking icon can see the wireless networks in the entire neighborhood.  When I connect, the circular "arrow" or "comet" in the icon just spins and spins and I never get the green lights.

More info:
-- I have the Broadcom B43 wireless driver (restricted) enabled in the Hardware Drivers system menu.
-- I do notice that I get a message during boot that states:
"udev: renamed network interface wlan0 to eth2", although I do not know if that is significant or not, but you can see eth2 listed in my 'iwconfig' output below.
-- In the System/Wireless Network Drivers menu, there is an entry in the "currently installed windows drivers" window that says "WMP54GS Hardware Present:  Yes"

Here is iwconfig:
```
poodles@doc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

eth2      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:C4:31:67   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

output for lshw -C network

```
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0c:6e:79:96:fb
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Ethernet interface
       product: 3C920B-EMB Integrated Fast Ethernet Controller [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 40
       serial: 00:26:54:10:55:c6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:0f:66:6c:e3:3b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

I have searched the forums for several nights and tried most tricks, but I am having no luck.  I'm fairly new to ubuntu, so need some help getting me back on line.  Wife is tolerating the long cable to my router, but I would like to get back to wireless. 

I too hate M$.  I did not want to ask for individual help, but I have spent enough hours trying to rectify this that I know I'm in pretty deep.  Please help me find peace!

Best regards,
Jay

---

