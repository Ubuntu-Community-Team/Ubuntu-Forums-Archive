---
title: "Network manager"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by sigma_z_1980 on 2011-01-18
hey this is probably a vey silly 1, but I've been trying to solve it for a while now and failed.

I've accidentally deleted the panel with all shortcuts. I've restored everything except the network manager, 'cause I can't find it anywhere, and this is damn inconvenient! I've run Network connections instead, but this is not the same thing for some reason. Also Ubuntu Center of Applications doesn't provide the link to its location for some reason (unlike other applicaitons).

I'm runnning Ubuntu 10.10, Gnome 2.30.2

---

### Post by khelben1979 on 2011-01-18
I think that if you start a [GNOME session]("http://en.wikipedia.org/wiki/Gnome_%28software%29") you should see the network manager in the Ubuntu menu.

Otherwise you have the option of replacing the default network manager with a software called [Wicd]("http://en.wikipedia.org/wiki/Wicd"). [Here's]("http://www.liberiangeek.net/2010/08/network-manager-trouble-replace-wicd-network-manager-ubuntu-10-04-lucid-lynx/") a short tutorial in how to do it.

---

### Post by mick222 on 2011-01-18
To reset panels to default open a terminal
```
gconftool --recursive-unset /apps/panel 
Then
rm -rf ~/.gconf/apps/panel
then enter
pkill gnome-panel
```
 you should be back to normal then.

---

### Post by pebo on 2011-01-18
Or you could try running```
nm-applet &
```in a terminal, then go to System -> Preferences -> Startup Applications and tick the nm-applet check box to have it autostart on boot

---

### Post by vivek.pandey on 2011-01-18
right click on panel..->add to panel->notification area

---

### Post by sigma_z_1980 on 2011-01-19
> **neo_aryan said:**
> right click on panel..->add to panel->notification area

thanks, this did the trick

---

