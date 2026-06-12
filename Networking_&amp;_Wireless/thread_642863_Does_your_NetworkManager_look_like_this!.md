---
title: "Does your NetworkManager look like this!?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by cisforcojo on 2007-12-17
I'm working on setting up WPA and came across this page. Does YOUR Network Manager look like this!?!?!? This looks awesome!

[http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html](http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html)

All I have is the nm-applet icon and if I left click I can choose "Manual Configuration" and right click yield "Enable Networking" and "About". If it looked like the Network Manager in that link, that'd be awesome.

I have an Intel PRO/Wireless 2200 BG network adapter using ipw2200. I currently have wireless working correctly but am trying to move to something more secure (I am only using WEP right now)

---

### Post by Edho on 2007-12-17
Leftclick on nm-applet....man config
>>password...

Select wireless...hit properties.

Can you switch to "roaming mode: ?

Then i get the nice applet with all information.

---

### Post by cisforcojo on 2007-12-17
Actually, it already was on 'roaming mode' (I've been messing around with /etc/network/interfaces though) but I usually type everything in manually (I guess that WOULD be the manual part of it. I'll try rebooting and see what I get.

---

### Post by Edho on 2007-12-17
My Network interfaces...

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0


Thats all.

---

### Post by cisforcojo on 2007-12-17
Nice buddy!! You solved my problem.

---

### Post by Edho on 2007-12-17
Explain.

---

### Post by cisforcojo on 2007-12-17
I needed to leave my wireless on 'roaming' in order for it to work. Still haven't gotten WPA to work though.

---

### Post by erfahren on 2007-12-17
I was/am still slightly confused about all this so someone can correct me if I'm wrong, but that isn't the actual Network Manager *per se*. The Network Manager itself is meant to save different network configurations. 

It's actually the nm-applet pictured there, which is part of the Network Manager package,
from: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
> 
Note: nm-applet is now part of the network-manager-gnome package which is recommended when you install the network-manager package but may not have been installed

- huh? :confused:

Anyway, I wanted to mention that I didn't have much luck setting up my wifi in Feisty using that. (I use WPA and static IP addresses on my PCs.)

I went by [this HowTo](http://ubuntuforums.org/showthread.php?t=202834), which basicaly sets up everything manually in /etc/network/interfaces . I also like it since I can just back up the file, restore it in a new installation, and be online.

---

