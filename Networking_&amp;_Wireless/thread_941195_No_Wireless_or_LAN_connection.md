---
title: "No Wireless or LAN connection"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Beerzo on 2008-10-07
First of all hi all, i am new to the world of Linux/Ubuntu.

I ma having issues getting an internet connection through wireless and LAN. 

I checked other posts and seen that UDISWrapper should be used to install the correct driver but i am unable to even get that installed. I tried the help file contained within Ubuntu but still no joy. 

Can anyone help?

Regards

Beerzo

---

### Post by coubury on 2008-10-07
What wireless card have you got?

---

### Post by Beerzo on 2008-10-08
sudo lshw -C network (i found this in the inbuilt help) gives me the below. Does that let you know?


 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8f:e7:5a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:72:cb:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Beerzo on 2008-10-09
Anyone? :-({|=:sad:

---

### Post by superprash2003 on 2008-10-09
post output of iwconfig

---

### Post by Ayuthia on 2008-10-09
Can you try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```
I just want to see if the wireless being disabled is causing any problems.  It should not be the problem, but it wouldn't hurt to check.

As for your wireless card, please try the following guide:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Go to Option 2 where it will explain how to get the files you need to get your wireless working.

---

### Post by Beerzo on 2008-10-09
superprash2003 - 

this is the output of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Ayuthia
The code you enter has managed to get my LAN working perfect i cant thank you enough KUDOS!!!

I will try the wireless thing as well. Not sure i have Ndiswrapper installed though.

---

### Post by TheSmokingGNU on 2008-10-09
sorry to jack this thread, but I need some help with my wireless as well. My main problem is that I a)Don't use ubuntu that often, and b) am running off of my neighbor's wireless, so I don't know the specs or the ip, among other things. I have a belkin wireless G desktop card, and a freshly installed ubuntu, I think it's the latest version. any ideas?
I am dual booting, so if I load into windows I have internet. It's cumbersome, but I can do this all if I take a while to do it.
thanks

---

### Post by TheSmokingGNU on 2008-10-09
oh, sorry. also, I am running an Intel Core 2 Duo E8400 processor. is that a 64 or a 32? or neither? I am confused...

---

### Post by Beerzo on 2008-10-10
WIRELESS NOW WORKING!!!!

When the LAN started working it prompted for some updates and driver notifications installed these and hey presto wireless now working. 

Cheers again

---

