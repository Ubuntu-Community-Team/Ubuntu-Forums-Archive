---
title: "Cannot find wifi connection with Asus WL-138G v2"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by Fjatle on 2008-11-25
Hi there. 
I recently threw out my CWP-854 card because I couldn't get the drivers to work. 
So when I saw this Asus card on a webshop with "Works on Linux", I bought it right away..

My luck, same crap..

I am running Intrepid 
Linux Image: 2.6.27-7

I tried ndiswrapper with no luck. Ndiswrapper uses the driver: bcmwl5.

> 
**ndiswrapper -l**
bcmwl5: driver installed
       device (14E4:4318) present (alternate driver: ssb)



Here you have result from two other commands
> 
atle@atle desktop:~$ **sudo lshw  C network**
[sudo] password for atle: 
    
*-network               
[I]       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:11:3d:db
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt fd 
100bt 100bt fd 1000bt fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK NAPI 
duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair[/I]

*-network
[I]       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43 pci bridge latency=64 module=ssb
 [/I]  
*-network:0 DISABLED
       [I]description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:22:15:2d:93:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/I]

*-network:1 DISABLED
       [I]description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: c2:af:16:9c:00:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes 
multicast=yes[/I]



**atle@atle desktop:~$ iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not Associated   
          Tx Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.


I think this looks strange.
Iwconfig says it tries to use wlan1 ?

and lshw says wlan1 (logical name) is DISABLED, while the drivers are set to be some network connection wich dont have a logical name, and is not described as Wireless interface??

It doesn't make sense to me..


So here you have me. On my knees, screaming for help. I don't want to buy yet another pci card! ](*,)

---

### Post by divague on 2008-11-25
Try following this guide.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

hope it helps

---

