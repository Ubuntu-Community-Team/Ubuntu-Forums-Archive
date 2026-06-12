---
title: "nm-applet"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by wokxpress on 2007-11-07
Just installed Ubuntu 7.10 on lap top after trying it out on desktop

-Installed gutsy on lap top
-tried to install ndiswrapper and Broadcom windows driver from the install.py file in bcm,43xx-0.3.2-internet.tar.gz
-wireless still not working after reboot, so then i tried WCID from same install.py file
-after reboot- nm-applet missing from top panel
-tried plugging in hard line, still no internet connection
-seems like there's no network manager. can't download from packet manager, cuz cant connect to the net
-searched everywhere, still can't find answer - any suggestions?

chipset: 14e4:4318

---

### Post by wokxpress on 2007-11-08
also got this from terminal

wokxpress@Toby-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:e8:5f:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64

now i just got a hard line connection but wont let me install network manager from add/remove program lis

---

### Post by wokxpress on 2007-11-08
finally got the network manager back up now just need to get wireless working. 

*cross fingers*

---

### Post by Selcal on 2007-11-08
I had to take the NM-applet out and just use a terminal window like below.


(eth0 is my wireless adapter id, yours may vary)  

> sudo modprobe ndiswrapper
sudo iwconfig <-to see if wifi is on
sudo iwlist scanning <-to see if it picks up your network
sudo iwconfig eth0 essid yournetworkname
sudo iwconfig eth0 key whateveryourkeygoeshere
sudo dhclient eth0 



I used NDISWRAPPER GUI that I picked up from the [add/remove programs]  Using the ubuntu help for iwconfig details and some details from a search of NDISWRPPER in here you will find everything you need.

it worked for me, see how it works for you.  I continually use the last 3 command lines to connect to my wireless,  all i need to do now is write it up in python and i can have a single icon connect.

---

### Post by wokxpress on 2007-11-08
thanks so much for the help 

after 4+ hours i was finally able to get the wireless setup with this guide
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Cheers!!

---

