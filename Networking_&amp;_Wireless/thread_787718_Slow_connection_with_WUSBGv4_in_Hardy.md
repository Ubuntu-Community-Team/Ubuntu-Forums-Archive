---
title: "Slow connection with WUSBGv4 in Hardy"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by devosion on 2008-05-09
When I used this linksys usb wifi connector in gutsy I would have it run through ndiswrapper with the drivers included in the software. Now that I have switched to hardy it seems to work out-of-the-box but the connection is terrible. I have re-installed ndiswrapper and the rt2500usb drivers but they dont seem to be picked up.

>   *-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:4c:16:72
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:39:0c:4d:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=******** multicast=yes wireless=IEEE 802.11g


When I perform a ndiswrapper -l it shows that the driver is loaded but it doesnt seem to make a difference. I know im missing something here but i'd appreciate some help in getting this fixed. Thanks!

---

### Post by superprash2003 on 2008-05-09
is it browsing speed or downloading speed? download a file and check the speed..

---

### Post by devosion on 2008-05-09
> **superprash2003 said:**
> is it browsing speed or downloading speed? download a file and check the speed..

It is both. Firefox is running slower than on my laptop, and I noticed that I was getting at most 10kb/s when dling updates through package manager.

---

### Post by devosion on 2008-05-09
bump

Please help.

Could at least someone tell me how I unload and reload modules? So that I can mess with unloading the default driver module and loading in ndiswrapper.

---

### Post by devosion on 2008-05-10
Bumping this again.

I've noticed that I cant get the ndiswrapper module to be associated with my linksys usb adaptor now. But as soon as I modprobe rt2500usb I obtain a wireless connection. Im not sure if I am the only one experiencing problems with Hardy acknowledging ndiswrapper for my linksys usb adaptor, but I never experienced this with Gutsy, or Fiesty for that matter. 

I attempted the 'quick-fix' of bumping my bit rate speed up with 

> 
sudo iwconfig wlan0 rate 54M


but that didnt help at all. I still have continued problems both browsing and downloading and I am not quite sure where to take this next. I'd really appreciate some assistance on this of some sort that either involves getting ndiswrapper associated with my linksys usb adaptor, or something else that will get my speed up from 8-16kb/s to something that better matches my bandwidth of 2mb/s on my dsl. At this rate i'll probably go back to Gutsy.

---

### Post by devosion on 2008-05-10
Managed to figure out the problem. Turns out this guide proved to be most helpful:

[http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")

It may not work for all wusb54gv4 users with hardy but it solved the slow connection issues.

---

