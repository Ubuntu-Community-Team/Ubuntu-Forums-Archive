---
title: "Wireless suddenly dissapears, and only manual config possible in nm-applet"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by olavjunior on 2007-08-23
My wireless randomly stoppes working. Like when I woke up this morning after the comp had been running all night, nm-applet said it was connected, but I couln't surf the internet. I then disabled network, to then reable it again. But then (here's the catch)** nm-applet only gives me the manual configuration option**. It doesn't give me any list of available networks. And if I go to admin -> network there's no wireless option. The network manager gives me two cabels, on eth0 and eth1 I think, and there's no way to configure the wireless. It's as it doesn't exists! 

Please help! Everytime this happens I have to** restart **to get it working again. Have tried ctrl alt backspace, killing nm-applet & network from system, all with no luck. 

This is really annoying, and has never happened to me until recently. Help is really appreciated

---

### Post by ACGarib on 2007-08-23
I have the same problem. I used to have an icon with 2 computer monitors that when I clicked it, it would give me the options of connecting to a wired network, enabling wireless, and which wireless network to connect to. Now that icon is gone. I added network manager to my top panel, and the icon is the same, but clicking on it brings up a different program.

I also have a problem with my battery monitor. When I unplug my laptop from AC power, a little icon the shape of a battery used to pop up in my top panel. Now that doesn't happen anymore. A little popup dialog box pops up in the upper left hand corner of my screen and says that the laptop is running on battery power, but the popup is pointing to nothing. (The same thing happens when I unplug my ethernet cable.)

---

### Post by ACGarib on 2007-08-23
Yay! I figured it out (at least on my laptop) For some reason, "notification area" in my top gnome panel was deleted. I just added that and I have network-manager and power-manager back! I then removed network-monitor, right clicked on network-manager, enabled wireless, then clicked on it again, chose manual configuration, and enabled wired network there, and everything's back to normal!

I hope this helps you.

---

### Post by r_l on 2007-08-23
> **olavjunior said:**
> My wireless randomly stoppes working. Like when I woke up this morning after the comp had been running all night, nm-applet said it was connected, but I couln't surf the internet. I then disabled network, to then reable it again. But then (here's the catch)** nm-applet only gives me the manual configuration option**. It doesn't give me any list of available networks. And if I go to admin -> network there's no wireless option. The network manager gives me two cabels, on eth0 and eth1 I think, and there's no way to configure the wireless. It's as it doesn't exists! 

Please help! Everytime this happens I have to** restart **to get it working again. Have tried ctrl alt backspace, killing nm-applet & network from system, all with no luck. 

This is really annoying, and has never happened to me until recently. Help is really appreciated

It happened to me, too.  I didn't know what happened.  Interestingly, for me it seems to be the WPA problem.  It doesn't happen anymore after I update to the gusty kernel (but still using feisty).  Before that, it happened from time to time and I had to boot to KDE (I have kde-desktop installed), and then somehow strangely Knetworkmanager "fixed" the problem.  Sometimes, it doesn't get fixed, but I would get into Knetworkmanager to reconfigure (mainly the DNS server, and the IP address) - then it reset itself and works itself out - then boot to Gnome and it kept working and seemed to be problem solved.  Go figure.   I am hoping that the wireless get more stable in Gusty.

---

### Post by olavjunior on 2007-08-24
OK, so mamby updating my kernel will help. I have wpa-encryption on.  This happens to me all the time, I loose my network, and I have to reboot. Wpa is really annoying! It sometimes also uses very long time to log in, and I have to give the password many times. It also seems that my keyring-manager isn't always working. 

ACGarib -this has nothing to do with my problem, sorry.

---

### Post by Harpoon on 2007-08-25
I've run into  a similar problem in Feisty.  It has been working fine until yesterday when suddenly the connection (to an open wap) began dropping and reconnecting for no apparent reason.  I also had the netspeed applet running, and that fell back to reporting eth1 is down (or similar) while a download in progress was happily continuing.  Thoroughly odd behacior, especially since I didn't install/change anything remotely connected to network settings.  I uninstalled netspeed, but it turns out not to be the culprit.  BTW, the wireless router is just outside my apartment door, so signal strength is not an issue.

I don't see any pattern to the behavior, so troubleshooting it is going to be a b**ch.

---

### Post by notoriousdbp on 2007-08-25
I hate to keep going on about it but I use wicd instead of network manager on my WPA encrypted wireless netwrok and I have never looked back.  Give it a try, there are loads of threads about it on the forum.

(Note: This is my **100th** Post! :D)

---

