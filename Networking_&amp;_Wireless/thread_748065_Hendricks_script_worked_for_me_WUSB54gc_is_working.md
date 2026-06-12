---
title: "Hendricks script worked for me: WUSB54gc is working"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by dixonh2 on 2008-04-07
After 12 hours of research, rebooting, turning in a newly bought Linksys PCI wireless card to get a Linksys USB wireless, I ran Hendricks great script ( thank you , sir!!  :KS) and it almost connected. But I'm a first time  ever Linux user and in a moment I tweaked with the applet in the task bar at the top right of my new Gutsy installation and I was on the web! 

This was not a good introduction to the Linux world.:(

When I bought the earlier Linksys PCI card the tech at the retail tech shop fairly sneered at the idea of Linux. " I guess Linux is OK if you are a free software fanatic or have nothing but time on your hands to design your own drivers for practically everything.", he commented.

I cringed later when I had to exchange the Linksys PCI card ( because Linux.com said it was pretty hopeless but the WUSB54g was OK) There was the same tech with a smirk on his face waiting for me to cave in.

 A true Microsoft snob, that guy was.:lolflag:

For those interested, here's the terminal description of the WUSB54gc ( and note that it's the 54gc model which has so far ( only overnight ) been working just dandy thanks to Hendricks great script and hard work.

sudo lshw

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan2
       serial: 00:1a:70:a6:e3:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.48+Linksys, A Division of Cisc ip=192.168.1.125 link=yes multicast=yes wireless=IEEE 802.11g

Dixon H Harris, MCSE
Denver North Carolina

---

