---
title: "network manager can't set static ip"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by paul555 on 2008-10-31
Hi all i just upgraded to ubuntu 8.10 from 8.04 in my laptop and everything is working fine(even my wireless card with a rtl8187b chipset) except that network manager doesn't save the static ip i setup for eth0.In fact every time i start my laptop the settings(ip netmask gateway and dns servers) for eth0 interface are resetting to dynamic dhcp even if every time i set it up manually.Is there a way to fix this?

---

### Post by sakis on 2008-10-31
> **paul555 said:**
> Hi all i just upgraded to ubuntu 8.10 from 8.04 in my laptop and everything is working fine(even my wireless card with a rtl8187b chipset) except that network manager doesn't save the static ip i setup for eth0.In fact every time i start my laptop the settings(ip netmask gateway and dns servers) for eth0 interface are resetting to dynamic dhcp even if every time i set it up manually.Is there a way to fix this?
Same problem here!

To solve it i install **wicd** [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) in the place of network manager and everything worked just like they should be :)

To install it in Ubuntu all you have to do is to enter the below line in the repositories...

```
deb http://apt.wicd.net intrepid extras
```

and install the package wicd, which automatically removes the network manager.

I found the settings much more easier to understand than the network manager and it keeps my static ip without the need to set it every time i reboot :)

EDIT:
Before you set up the wicd make sure to...

```
gksudo gedit /etc/network/interfaces
```

ignore the lines with # in front of them and leave only the below...

```
auto lo
iface lo inet loopback
```

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by stankopp on 2008-10-31
That's all peachy, but if you can not make an internet connection, this is all pretty moot.  The contents of the /etc/networ/interfaces file are just like what you have above and that seems like it sets up the auto <iface> connection which is exactly what I don't want.

---

### Post by teet on 2008-10-31
I've had this problem too since alpha 6 of intrepid.  I'm really surprised this issue hasn't been fixed...

I guess I might have to resort to installing WICD.  Don't get me wrong, I've used WICD in the past and found it to be pretty awesome.  The thing is, I shouldn't need to install 3rd party, unsupported software to set a freaking static IP!

-teet

---

### Post by vitorgatti on 2008-10-31
> **teet said:**
> The thing is, I shouldn't need to install 3rd party, unsupported software to set a freaking static IP!

-teet

HELL YEA!
Same problem here.
[http://ubuntuforums.org/showthread.php?t=965762](http://ubuntuforums.org/showthread.php?t=965762)

Incredible how some really simple bugs just appear in each new version.
I remember Ubuntu 7.04 or 7.10 had an issue that didn't show Ubuntu logo on boot, because it always set 1280x1024 to resolution, so 15' monitors would never be able to show that...
Really, really amazing how crazy and "idiot" bugs simply show up.

---

