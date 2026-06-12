---
title: "loosing wireless connection"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by andylinux on 2006-11-03
Hi,
I am using a TEW-421PC Trendnet wireless card in my laptop with Edgy.  I insalled the ndiswrapper-1.8 tools and was able to get it working.  My only problem is periodically I loose my connection and I have to run,

sudo ifdown wlan0
sudo ifup walan0 

to get my connection working again.  
I'm using a static IP address and am very close to the wireless access point.  I have used the wireless access point without problems with my work laptop and Windows XP. 

Is there a log file I can look into to try and figure out why I am loosing the connection?

Thanks for the help,
Andy.

---

### Post by whomever21 on 2006-11-06
The same thing keeps happening to me--same card, same distro, except that sometimes ifup/ifdown freezes the machine.

---

### Post by whomever21 on 2006-11-14
this is no solution, and it delays the boot process, but i added ```
ifdown wlan0
ifup wlan0
``` to /etc/rc.local

---

### Post by whomever21 on 2006-11-20
I'm not having this problem anymore. All I did was remove ndiswrapper from /etc/modules and reboot. Uninstalling the driver through ndiswrapper is definitely not the answer, but for reasons I don't understand, running the driver through ndiswrapper isn't either. go figure.

---

### Post by FrodoB on 2006-11-20
Andy;

You might have better luck if you upgraded to the latest ndiswrapper 1.28:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Whomever;

The startup for ndiswrapper should be in:

/etc/modprobe.d/ndiswrapper

did you have it trying to start twice maybe?

---

