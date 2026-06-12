---
title: "Wirless headach"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by tjd_98 on 2008-05-28
Hi I'm pretty new to linux and am having a major problem. My wireless just will not work on my Acer Aspire 3620. I replaced the built in mini pci card with an intelcard. All seems well untill i try and use the wireless to get a connection. I did some trouble shooting and found that my hardware switch just doesn't work. After many attempts to repaire/ replace the switch we found that all we need to do is change the value of the file rf_kill to 0 (currently set at 2). I have no problem getting root priviledge or opening the file but when I use the standart text editor it will not save any changes that i make. When I doe save next time i open it is back to old file. Then I did some more research and came across VIM using the terminal. When I change the value here and save the file I get a message allong the lines of sync with ... (rf_kill in another directory) failed. Please, what can I do to get wireless up and running?

---

### Post by tjd_98 on 2008-05-29
When I try to edit the file /sys/bus/pci/devices/0000:06:05.0/rf_kill I get the following message:


"/sys/devices/pci0000:00/0000:00:1e.0/0000:06:05.0/rf_kill" 
"/sys/devices/pci0000:00/0000:00:1e.0/0000:06:05.0/rf_kill" E667: Fsync failed
Press ENTER or type command to continue

---

