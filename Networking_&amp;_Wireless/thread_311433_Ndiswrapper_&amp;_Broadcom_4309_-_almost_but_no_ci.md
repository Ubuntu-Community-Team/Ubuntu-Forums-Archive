---
title: "Ndiswrapper &amp; Broadcom 4309 - almost but no cigar"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by sanchrts on 2006-12-02
Dear all

Thanks to posts by trubblemaker and others I followed the blacklist bcm43xx / use ndiswrapper with Windows drivers route for my Dell Latitude X300 and its Broadcom 4309 wifi a/b/g card.

Via synaptics package manager I enabled universer and multiverse and installed Network Manager, network-manager-gnome Ndiswrapper-common and Ndiswrapper-utils-1.8

I completed the following steps:
sudo gedit /etc/modprobe.d/blacklist
* Add the line:  
blacklist bcm43xx
* After saving type at the terminal: 
sudo rmmod bcm43xx
* Get windows drivers onto desktop
* Install them in ndiswrapper:
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
* Check to see if hardware found
sudo ndiswrapper -l
* Setup ndiswrapper to load driver (and itself) at startup
sudo gedit /etc/modules
* Add a line which says:
ndiswrapper

My wireless now works including with WPA-protected networks but for some reason my Network Monitor appears to think that my wireless card (eth1) is not configured.

I think I had a similar issue in Dapper and it was to do with the name of the wireless interface...I have ensured that it is marked as eth1 (as this is the interface name that appears if I do the iwconfig command) but I am sure that Network Manager believes that my card is wlan0 for some reason.

I just cannot figure out how to tell Network Manager that my card is at eth1 and not wlan0 (if that is the cause of the problem).

Any help much appreciated!

Rafael

---

### Post by EriCr on 2007-11-28
Rafael,

My main man you are a [COLOR="Red"]**_[SIZE="4"]legend[/SIZE]_**[/COLOR]

I have been trying to get my wireless working for 3 months, 2 mins after reading your post I am typing this using my wireless connection. Did a reboot selected my wireless ap from the list banged in my wep key and BINGO***__*** I was online.

I have read dozens of posts, tried dozens of solutions but to no avail. Thank you, Thank you, Thank you. Again you are a [COLOR="Red"]**_[SIZE="4"]legend[/SIZE]_**[/COLOR]

:KS :lolflag:  :KS

---

