---
title: "Realtek rtl8185 issues..."
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by DarthSteedious on 2008-09-18
I've just recently put 64 bit Ubuntu on my Alienware Aurora m9700. Everything is working fine except my wireless card. It appears to recognize the card is there but doesn't function in anyway. I've looked everywhere and it seems like it is this particular card that has the issue but I can't seem to find anything that works. The card is a Realtek with a model number rtl8185. If anyone has any suggestions or knows a way that can get this wifi card working I would greatly appreciate it.

---

### Post by DarthSteedious on 2008-09-18
lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:03:25:3d:d7:9e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair


and here is what comes up for my ifconfig

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:3d:d7:9e  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe3d:d79e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:535483 (522.9 KB)  TX bytes:92548 (90.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113400 (110.7 KB)  TX bytes:113400 (110.7 KB)

Why no wlan0?

---

### Post by shadowber on 2008-09-22
I have the same exact problem. can someone help??

---

### Post by DarthSteedious on 2008-10-08
Alright, I finally (after upgrading to the latest beta of Intrepid) was able to get ndiswrapper to load the windows driver for my network card. Now my problem is that the network manager is showing the existence of a wireless connection but says the device is unmanaged. I'll post my lshw and ifconfig. If you have any solutions for me I'd greatly appreciate it.


 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:3d:d7:9e  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe3d:d79e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1752272 (1.7 MB)  TX bytes:320966 (320.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:189700 (189.7 KB)  TX bytes:189700 (189.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:db:b7:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:c0:a8:db:b7:23  
          inet addr:169.254.8.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-DB-B7-23-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:db:b7:23
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:03:25:3d:d7:9e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

---

### Post by Aarookie on 2008-11-07
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up
I'm on 32 bit computer, not sure if this will work in 64 bit environment, my bro's computer wouldn't accept 32 bit driver with this method, and his card doesn't have 64 bit windows' drivers

---

