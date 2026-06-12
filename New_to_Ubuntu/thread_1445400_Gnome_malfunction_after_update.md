---
title: "Gnome malfunction after update"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-04-02
Question:

After updates, my gnome panel no longer shows the running programms, and the sound volume manager and the gnome-network applet are gone from the top panel. And I can't add them again, because they are gone from the add-to-panel menu as well.

What to do now ?

---

### Post by wojox on 2010-04-02
Did you add Notification Area and Window List?

---

### Post by WitchCraft on 2010-04-02
> **wojox said:**
> Did you add Notification Area and Window List?

Not possible, I can only add mainmenu, menubar, logout, separator, shutdown, forcequite, drawer, connecttoserver, applicationlauncher, customapplicationlauncher and runApplication. That's all that appears in the add menu.

And I had to connect to the WLAN via the console...
ifconfig eth0 up
iwconfig essid "NetworkName"
dhcpcd eth0
Because the network manager is missing...

---

### Post by WitchCraft on 2010-04-02
I think I removed all those applets from the user config when there were bugs at login and it asked whether to keep or to remove...

I tried apt-get install --reinstall gnome-applets network-manager-gnome, but that doesn't help...

It seems like it doesn't restore the config entries.

---

### Post by lidex on 2010-04-03
Is this Lucid?

---

### Post by WitchCraft on 2010-04-03
> **lidex said:**
> Is this Lucid?

No, this is Squeeze (debian testing), after trying and failing to compile gnome3...
But it might also be the new kernel.

---

### Post by WitchCraft on 2010-04-04
bump.

---

