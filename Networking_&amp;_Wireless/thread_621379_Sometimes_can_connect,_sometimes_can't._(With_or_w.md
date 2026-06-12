---
title: "Sometimes can connect, sometimes can't. (With or without wires.)"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by TheMusicGuy on 2007-11-23
Hiyo,

I recently did a fresh reinstall / upgrade to Gutsy. (Did a complete reformatting of my HD; brand new filesystem and everythin

AND THEN EVERYTHING WENT NUTS.

...Well, internet-wise, anyway.

Okay, so I have a ipw3945abg for wireless, and it has always worked perfectly while using Kubuntu 7.04. However, upon upgrading/switching to Ubuntu 7.10 whether or not I can connect using it seems up to fate to decide. Sometimes it connects to any wireless network for which I have given the correct credentials (whether WEP or WPA Personal; haven't tried WPA Enterprise) during boot, and I have a good connection going by the time I log in.

Sometimes, however, I can't connect to save my life. I can usually see all networks in the area, but I can't connect to them using nm-applet or wifi-radar. Suspending my laptop usually makes me lose my connection, but sometimes it severely screws up my connection so that I get only a few KB/s but without losing the connection completely.

The only way I have been able to get around this problem is to reboot over and over until I can finally connect. This can take up to 4 tries to actually work. (Don't ask me why it works at all.)

Besides the wireless problems, I am having problems with my wired (ethernet) connection. Namely, I almost never can connect. Sometimes I can connect and can get a pretty good download speed. Sometimes I can connect with a very slow connection which completely stops working altogether after about 5 or 10 minutes.

Both of my devices (eth0 for Ethernet, eth1 for wireless) seem to be detected just fine by ifconfig and iwconfig. ifup and ifdown seem to be able to configure eth0 without any trouble, yet I can't seem to connect via ethernet after ifup.

The ethernet problems have always kind of been around (though never this bad before), but the wireless crud is new with 7.10.

---

### Post by c3apollyon on 2008-05-18
I have had this exact problem on and off since Fiesty or Gutsy.  I used to be able to correct it through command-line commands resetting dhclient and setting up the iwconfig line by line but now even that doesn't work.

If I try connecting to my home network it just continually pops up the password dialogue box while according to my router, nothing is even trying...

---

