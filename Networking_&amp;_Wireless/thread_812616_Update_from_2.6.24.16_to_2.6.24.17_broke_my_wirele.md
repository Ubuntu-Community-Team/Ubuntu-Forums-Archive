---
title: "Update from 2.6.24.16 to 2.6.24.17 broke my wireless networking"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by cjbarrow on 2008-05-30
I am Running the latest Hardy installed the latest updates last week which updated the Kernel from 2.6.24.16 to 2.6.24.17. Since this update I am unable to connect to my wireless router. I can choose to boot from 2.6.24.16 rather than 2.6.24.17 and the connection works fine.

When booting with 2.6.24.17 the laptop attempts to connect to my network, the network is clearly viable and shows good signal strength. 

I have a braodcom wirleless card and use the ndiswrapper for my connection, I have also followed all the instructions from a number of post I have seen without any luck ([http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312)) 

The following command gives me the following

lspci | grep Broadcom\ Corporation

05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I use wpa security.

Any suggestions would be appreciated.

Chris.

---

### Post by max littlemore on 2008-05-30
I just added a comment that I had a similar problem, but then I notice the wireless switch on my notebook which hadn't been working for wlan has now started working.

I had it switched off. :redface:

Please continue....

---

