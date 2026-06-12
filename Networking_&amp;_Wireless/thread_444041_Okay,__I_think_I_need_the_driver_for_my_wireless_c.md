---
title: "Okay,  I think I need the driver for my wireless card"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by JMV290 on 2007-05-15
I just got Ubuntu installed(via Wubi) and I noticed my wireless card wasn't working



I'm assuming I need the drivers.


bcmwl5.sys is the driver for windows.  Do I just copy that to a folder in Ubuntu?


>  Network Card  
Model: Broadcom 54g MaxPerformance 802.11g - Packet Scheduler Miniport 
Driver: bcmwl5.sys
Wednesday, October 20, 2004
Supported 
 
That is what HP Help and Support Center says about my wireless card.


I tried typing "dmesg" into the terminal like some one told me.  Nothing about Broadcom came up. so I can't find the model number.

Does anyone know what to do?

---

### Post by bukwirm on 2007-05-15
It appears that many people have gotten that wireless card to work with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

