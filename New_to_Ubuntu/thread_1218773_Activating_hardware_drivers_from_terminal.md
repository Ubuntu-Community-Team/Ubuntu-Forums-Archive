---
title: "Activating hardware drivers from terminal"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-07-21
I got Ubuntu 9.04 set up @ an old box I had.
The wireless network card seems to work okay when I load gnome, but if I boot without gnome it simply does not work.
I noticed that I have the "alternate Atheros "madwifi" driver" enabled.

Is there any way to get this driver working @ terminal?

Extra information:
~If I boot with X and then switch to terminal (sudo /etc/init.d/gdm stop @ tty1) the card stops working
~If I boot without X (booting changed via rcconf) the card does not work at all but I am still able to detect access points.

---

### Post by Tman5293 on 2009-07-21
Is there a reason why you need to boot without gnome???

---

### Post by nothingspecial on 2009-07-21
```
sudo modprobe ath_pci
```

edit /etc/modules and add ath_pci

I`m not in ubuntu right now but in jaunty I thimk there is a specific /etc/modprobe.d/blacklist config for the madwifi driver (ath_pci). You will need to comment it. And probably add ath5k to the general blacklist config.

---

### Post by Zack McCool on 2009-07-21
The problem you're having is not the modules, but rather that network manager doesn't run until you log in to the desktop.  The wireless config is not (by default) stored in /etc/network/interfaces, since having it stored there (with your specific security information) would basically disable any roaming capabilities.

It IS possible to add the information to your boot networking startup, but then you'll really only be able to use your laptop at home.  If that's OK with you, post the specifics here, and someone should be able to help you to construct the proper interfaces file.

You'll need the type of card, the type of security (none, WEP, WPA).  You don't need to post the actual security information, but the above will determine if you need to use wpa_supplicant, or if you can simply create a wlan0 entry in interfaces.

---

### Post by nothingspecial on 2009-07-21
In that case read [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by The Cog on 2009-07-21
Gnome wireless manager - the wireless widget you see in the syetem tray - doesn't start to work until someone is actually logged in to the GUI.

It is possible to configure the wireless from the command line, but it is probably easiest to uninstall gnome-network-manager and install wicd instead. They conflict so you can't have both installed.

With wicd, a daemon is started when the PC boots, so it will find and autoconnect to the nearest wifi even if you don't start a GUI at all. The configuration files are in /etc/wicd but not very well documented so the easiest way to configure it is to use the GUI (it appears in the system tray, same as gnome-network-manager).

---

### Post by ozzyprv on 2009-07-21
> **Tman5293 said:**
> Is there a reason why you need to boot without gnome???

Because I will eventually use this box as a server. No need to use the X after I set everything up.
I was testing the internet connection before going headless.

> **nothingspecial said:**
> In that case read [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=571188")

Thank you. It looks promising. I will give it a try when I get home.

> **The Cog said:**
> Gnome wireless manager - the wireless widget you see in the syetem tray - doesn't start to work until someone is actually logged in to the GUI.

It is possible to configure the wireless from the command line, but it is probably easiest to uninstall gnome-network-manager and install wicd instead. They conflict so you can't have both installed.

With wicd, a daemon is started when the PC boots, so it will find and autoconnect to the nearest wifi even if you don't start a GUI at all. The configuration files are in /etc/wicd but not very well documented so the easiest way to configure it is to use the GUI (it appears in the system tray, same as gnome-network-manager).

Thank you. I will use this route if Tman5293's suggestion does not work.

---

### Post by ozzyprv on 2009-07-22
> **ozzyprv said:**
> 

Thank you. I will use this route if Tman5293's suggestion does not work.

I had to do this, remove network-manager and install wicd. Nothing else worked.

---

