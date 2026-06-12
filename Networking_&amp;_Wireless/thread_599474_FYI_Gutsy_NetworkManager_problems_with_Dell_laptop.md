---
title: "FYI: Gutsy NetworkManager problems with Dell laptops"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by T_W on 2007-11-01
If anyone is having a problem with NetworkManager not roaming from base station to base station on  Dell laptop (in particular a Dell D620), take a look at this:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444695]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444695")
> 
> Everytime network-manager tries to connect to a wireless network i get a log
> of:
> 
> NetworkManager: <info>  Error getting killswitch power:
> org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not
> supported
> 
> in syslog and nm just sits there and doen't connect.
> 
> My wireless card is an Intel 3945 on a Dell Latitude D620.
> 

This is most likely a bug in hal.
Please install libsmbios-bin and edit
/usr/lib/hal/scripts/linux/hal-system-killswitch-get-power-linux

and change the path /usr/bin/dellWirelessCtl to
/usr/sbin/dellWirelessCtl.


This change made a world of difference to NetworkManager stability for me.  

I was seeing the org.freedesktop.Hal.Device.KillSwitch.NotSupported error.

---

### Post by T_W on 2007-11-01
Note: May also have to do the following:

> sudo echo dcdbas >> /etc/modules

From [http://ubuntuforums.org/showthread.php?t=507598&highlight=dcdbas]("http://ubuntuforums.org/showthread.php?t=507598&highlight=dcdbas")

---

### Post by tschneiter on 2007-11-14
Trying it out now... I've had miserable luck with the wireless card under gutsy, and I am forced to restart because the system just sort of 'loses' it (and I dont know how to get it back any other way). Ill let you know if I have any luck.

Thanks!

---

### Post by Arenlor on 2007-12-13
I tried both parts of this, I have the infamous bcm43xx(11) and I can't get it to work whatsoever.

---

