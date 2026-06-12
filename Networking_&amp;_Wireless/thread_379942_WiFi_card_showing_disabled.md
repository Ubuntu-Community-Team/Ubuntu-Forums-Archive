---
title: "WiFi card showing disabled"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by jf1991999 on 2007-03-09
I have installed the latest Ubuntu version to my Dell Latitude D505.  I have enabled the device in the System>Admin>Networking and entered my access points SSID and wep key.  The device shows as enabled in this screen.

I can't connect to the Internet.  I run lshw and the device and driver are listed as

*-network:0 DISABLED
   description: Wireless Interface
   Product: BCM4306 802.11b/g Wireless LAN Controller
   vendor: Broadcom Corporation
   physical id:3
   bu info: pci@01:03.0
   logical name: eth1
   version: 02
   serial: 00:90:4b:78:81:cc
   width: 32 bits
   clock: 33Mhz
   capabilities: bus_master cap_list ethernet physical wireless
   configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no muticast=yes wireless=IEE 802.11b/g
   resources: iomemory:fcffc000-fcffdfff irq:5

The troubleshooting guide says the issue is in turning the card on.  Which is apparently not necessarily easy.  

Any help would be greatly appreciated.

---

### Post by yigal.weinstein on 2007-03-09
what about ```
ifconfig -a
``` 

what type of devices do you have listed?

---

### Post by jf1991999 on 2007-03-09
ifconfig -a shows

eth0 Link encap:Ethernet HWaddr 00:0D:56:E1:C3:3E

eth1 Link encap:Ethernet HWaddr 00:90:4B:78:81:CC

lo      Link encap: Local Loopback

sit0   Link encap:IPv6-in-IPv4

There is other information under all 4 of these but it doesn't look as though it is very useful.

---

### Post by jf1991999 on 2007-03-09
I found a HowTo that is very helpful for my Wifi card at [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I followed that but as a newbie to things Linux I made some errors.  When I type ndiswrapper -l

I get 
Installed Drivers:
bcmw15 invalid driver!
bcmwl5  invalid driver!

I try to delete these drivers so I can reinstall with the ndiswrapper -e bcmw15 and again for the other spelling.  It appears that they should have been deleted however when I list the drivers they are still there.  Can anyone help me with this?

I copied the driver folder to the desktop and was a little confused by how to install the drivers using sudo ndiswrapper -i ~/home/jf1991999/Desktop/bcm/bcmwl5.inf

The font l and 1 confused me.  When I run this is says that bcml5 is already installed but with extension l is says it is invalid.  I do have the Broadcom 4306 card.

---

### Post by Tethtibis on 2007-06-27
it stays disabled, because the wireless is not installed correctly. the graphical frontend for ndis wrapper should help.

---

