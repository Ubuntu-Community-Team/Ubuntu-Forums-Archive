---
title: "Panel will go invisible"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-09-27
ubuntu 10.04 netbook remix is just awful, i seem to find bug after bug, now the panel is going invisible when i click anything on it, i have used rm -r ~/.gconf/apps/panel to restart it but i hasn't made a difference. how could i go about fix this?

---

### Post by Bölvaður on 2010-09-27
You can always go to using another window manager.
So just fire up synaptic package manager and look for: kde desktop, ubuntu-desktop, awesome, fluxbox, openbox, icewm.. etc.. when you log in you should be able to change what desktop environment you use.

about killing the panel you can always find out what the name of the process is and then open the terminal and type something like (like here Im killing the gnome panel) ```
killall gnome-panel
```
but I guess you could also just type ```
xkill
``` and click on the panel.

this is obviously not a direct help, but I dont know what really is wrong.

---

### Post by Paqman on 2010-09-27
> **Bölvaður said:**
> You can always go to using another window manager.
So just fire up synaptic package manager and look for: kde desktop, ubuntu-desktop, awesome, fluxbox, openbox, icewm.. etc.. when you log in you should be able to change what desktop environment you use.


Incidentally, if' you're running the Netbook Edition then you've already got the standard Gnome desktop without having to install ubuntu-desktop. Just log out, hit your user name and choose "Gnome" from the sessions menu at the bottom.

---

