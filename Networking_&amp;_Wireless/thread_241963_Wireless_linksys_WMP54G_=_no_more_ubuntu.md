---
title: "Wireless linksys WMP54G = no more ubuntu"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by dragonlor20 on 2006-08-23
Ok, so we are 2/2 as far as fixing my problems with this forum go, so hopefully we can pull 3/3 and get my beautiful Ubuntu back :-(

Anyways, I just moved from Fresno, CA to Santa Barbara, CA (a nice long bumpy ride due to my old shocks). After I moved my computer, I inserted a LinkSys WMP54G Wireless PCI card... started up the computer... everything looked great to start with, I got to the bootup screen, all of my hardware checked-out... after i typed my username and password, it started to load, went to the splash-screen background, and then didn't go any further. I have a mouse but the little splash diologe never comes up and the computer refuses to go any further.

This also happens in a failsafe session of Gnome.

Please help... :-(

---

### Post by bionnaki on 2006-08-23
did you update before you last turned your computer off? see the stickies about this bug.

---

### Post by dragonlor20 on 2006-08-23
Update what exactly? The other sticky posts assume that Gnome boots up, which mine does not... I can get to the login, but not past the splash screen...

I have taken the card out and started the computer that way and it definitely boots up as per normal, so the problem is definitely the new wireless card. I can't get into ubuntu with the card inserted though, so the driver configuration and bug fixes and all of that are a bit difficult. What is causing it to freeze?

---

### Post by dragonlor20 on 2006-08-23
I got around the boot problem using this:

[http://www.ubuntuforums.org/showthread.php?t=223265](http://www.ubuntuforums.org/showthread.php?t=223265)

but while the connection seems to recognize the networks and be able to connect to them, I still don't have internet... :-(

---

### Post by niko7865 on 2006-08-28
Ya I solved all my boot problems, but it takes quite a few attempts to actually connect and get an IP address from the router. Thats if it doesn't freeze while connecting to the router, strange thing is that it works fine on the live CD. Would appreciate some help on the matter.

WMP54G v4.1 rt61 (useing the driver that came with ubuntu, not sure which it is)

---

### Post by bionnaki on 2006-08-29
[http://www.ubuntuforums.org/showthread.php?t=241565](http://www.ubuntuforums.org/showthread.php?t=241565)

---

### Post by dragonlor20 on 2006-08-29
> **niko7865 said:**
> Ya I solved all my boot problems, but it takes quite a few attempts to actually connect and get an IP address from the router. Thats if it doesn't freeze while connecting to the router, strange thing is that it works fine on the live CD. Would appreciate some help on the matter.

WMP54G v4.1 rt61 (useing the driver that came with ubuntu, not sure which it is)

Your dhclient should time out rather than freeze when trying to connect... I don't know why you would get a connection sometimes and not other times. How far from your router are you? I would include this stuff to get better replies:

/etc/network/interfaces


sudo iwlist scan
sudo iwconfig
sudo ifconfig
sudo dhclient

To keep from freezing your system back up on the reboot after playing with all this stuff, I would go ahead and do this:

```
cd /etc/network/
sudo cp interfaces /etc/network/interfaces.backup
```

The reason for this is that the networking utility under Dapper loves to change this file and this file is what will generally freeze you up when booting. If your system does freeze up, use ctrl+alt+backspace to get back to a command line and run this code

```
sudo cp /etc/network/interfaces.backup /etc/network/interfaces
```

If you can't get a command line that way then reboot, and use failsafe. Use the same code.

I would ask how new your installation is if it was working on the LiveCD and not now? The problem I ran into was that I had so much installed that I had no idea anymore what was breaking and what was working. A fresh install is the best way to work with the networking issue...

Hope that helps somewhat.

---

