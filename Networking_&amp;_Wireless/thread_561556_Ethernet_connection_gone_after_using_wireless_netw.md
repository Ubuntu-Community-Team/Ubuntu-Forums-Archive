---
title: "Ethernet connection gone after using wireless networking EASY fix."
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by blu3ness on 2007-09-27
Hello guys, I tried to get my wifi to work on campus but instead I broke my LAN on linux too. The problem occured in the following manner:

I tried to use the the EASY way to configure wifi on the sticky post (I have previously instaslled ndiswrapper, got it half working, and gave up)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

It detected my driver BCOM34XX, and tried to install ndiswrapper, when the installer was inserting ndiswrapper into the kernel module, my laptop would freeze..This happened twice, and I was forced to hard-restart my laptop. The first time it happened, I thought it was caused by the update I was running simultaneously, but it happened again when I was only running the installer script, so I decided to do it manually
First I checked,
```
ndiswrapper -l
```
was giving me the correct message, then I did
```
sudo ndiswrapper -mi
sudo modprobe ndiswrapper
```

All was well, nothing seemed to have changed. I can see the wireless networks, but I can't connect to any of them, the post stated maybe using a different network manager might fix that, so I tried to install WCID network manager.

The installer had that option, so I ran it, and it started to remove my gnome-network-manager and nm-applet. Afterwards, I found I lost my internet connection completely.

I have two ethernet adapters when previously using 
```
ifconfig
```

But now, my eth0 device is completely gone, and only my wireless adapter is showing up.

I know reinstalling network-manger will probably fix it, but the problem is, I can't even connect to the internet at this point...

Any help?

---

### Post by noob12 on 2007-09-27
It is probably just down.  If you type **ifconfig -a** it will probably show up. 

Go into **System | Administration | Network **.  Select wired connection and hit Properties. Disable roaming mode.  In Configuration select Automatic Configuration (DHCP).  That's it.

Then **sudo /etc/init.d/networking restart**

---

### Post by blu3ness on 2007-09-27
Hi there,
ipconfig -a 

Does display eth0 on the list, but

```
sudo /etc/init.d/networking restart
``` only restarts my wifi network adapter and not the eth0 one.

I have tried Administration-> Networking and setting it to DHCP as well, but that didn't work either :(

---

### Post by blu3ness on 2007-09-27
Hi there, this problem have been solved

Turned out somehow the installer script or the the package manager changed the network interface at

/etc/network/interfaces

all I did was adding back the eth0 entry and did a 

sudo /etc/init.d/networking restart

Thanks for the help noob12!

---

### Post by noob12 on 2007-09-27
Great!  That should have been equivalent to doing it through the GUI.

---

### Post by enchance on 2007-10-27
So it worked? I gotta try this.

---

