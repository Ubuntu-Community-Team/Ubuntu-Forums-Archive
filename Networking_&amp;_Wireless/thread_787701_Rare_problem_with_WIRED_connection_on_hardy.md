---
title: "Rare problem with WIRED connection on hardy"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by eternal243 on 2008-05-09
Hello everyone, I've been using gutsy for a long time now and haven't experienced any problems with it, so once I saw that Hardy Heron had been released I upgraded through the built-in updater.

Now I got a really weird problem and I can't find anything similar by searching the forum. I'll try to describe it.

I got two computers, my parents computer with winXP and mine with ubuntu, both connected through normal TP-cables to a D-Link router.

Before the update my internet worked flawlessly in ubuntu, but after the upgrade I just can't use the internet at all. On **_ANY_** of the two computers.

After some testing I figured that if my computer with ubuntu is powered on and connected to the router then the internet dies and can't be used on either mine or my parents computer. While if I unplug my computer from the router then I can use internet instantly on my parents computer. 

I've been thinking about this for a while but I just can't wrap my head around it. So if there is anyone who have experienced similar problems and got a solution, or anyone else who just want a challenge then I would be really grateful for some help.

And just to conclude the help request I'll add some info on my system that might be of help. My motherboard is an **Asus A8N32 SLI-Deluxe** and I'm using the **64bit version of ubuntu**. And finally my router is a **D-Link Dl 624+**.

Looking forward to some replies.

---

### Post by BallsOfSteel on 2008-05-09
If I were in your shoes, I'd just download a new .iso of Hardy Heron and reinstall.  I've never been a fan of 'updating' to a new operating system since the days of Windows 95.  Back up important files, reinstall and see if that fixes your problem.

Brandon

---

### Post by eternal243 on 2008-05-10
Yeah well, I will do that later if nothing else works but I would rather try to fix it without reinstalling first. Thanks for your reply anyway. =)

Btw, I have tried directly connecting my Ubuntu PC to the internet without passing through the router but it didn't work. Which means there is no problem with the router.

Any one else got any ideas?

---

### Post by zidboy on 2008-07-29
I update my computer and I had problems in the connection, in addition to the window where the connection set up, neither appeared, so it is clearly the fault of the update, things like that anyway always spend on upgrades.

I solved my problem with the command sudo / etc / init.d / networking restart

I hope you serve and you can navigate.

Bye

:guitar:

---

### Post by zidboy on 2008-07-29
I update my computer and I had problems in the connection, in addition to the window where the connection set up, neither appeared, so it is clearly the fault of the update, things like that anyway always spend on upgrades.

I solved my problem with the command: 

sudo/etc/init.d/networking restart

I hope you serve and you can navigate.

Bye

:guitar:

---

### Post by linux6994 on 2008-07-29
I would first look at the ip address of all three devices. Keep in mind that the router will have its own most likely dhcp ip address on the WAN side of the house. On the LAN side the ip address of the router will the dns and gw address that both the Ubuntu and XP will be pointing to. Sounds like when the Ubuntu is plugged in you are getting an address conflict, perhaps the Ubuntu and the router have the same ip address. 

Easy way to set them up is 

Router LAN ip 192.168.51.1 or 1.1 or what ever is default
XP set to 192.168.1.100 gw and dns to router IP
Ubuntu set to 192.168.1.110 gw and dns to router ip.

This way you know everyone's ip and can go from there. You should be able to ping from both PCs to the router and to each other.

---

