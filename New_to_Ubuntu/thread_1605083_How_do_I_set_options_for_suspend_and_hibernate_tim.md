---
title: "How do I set options for suspend and hibernate time limits for Lubuntu"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by nick987654321 on 2010-10-24
How do I set the options for suspend and hibernate time limits for Lubuntu?

I can find the screen saver settings, but the only options in there are for the monitor.

---

### Post by SuaSwe on 2010-10-24
System > Preferences > Power Management - that what you mean?

---

### Post by nick987654321 on 2010-10-24
> **SuaSwe said:**
> System > Preferences > Power Management - that what you mean?

There is no Power Management menu under Peferences in Lubuntu...

---

### Post by SuaSwe on 2010-10-24
Apologies, dind't spot the L! 

What window manager does Lubuntu use? Does it bring up anything from Alt+F2 > gnome-power-manager ? Do you have gconf-editor (also typed in under Alt+F2)?

---

### Post by nick987654321 on 2010-10-25
I'm not sure what window manager Lubuntu uses.  How can I find out?

The two Alt-F2 commands don't work.  gnome-power-manager doesn't bring up anything, and gconf-editor says "No such file or directory".

---

### Post by SuaSwe on 2010-10-25
I could be wrong as I've only ever used GNOME but I think you can find out by clicking System along the menu bar at the top (if you have it, that is!). With GNOME it says "About GNOME" second from the bottom; what's it say on yours?

---

### Post by nick987654321 on 2010-10-29
There is no "System" memo.

Lubuntu has: Accessories, Games, Graphics, Internet, Office, Other, Sound & Video, System Tools, and Preferences.

Under all these menus there is nothing for power management.

---

### Post by SteveDee on 2010-10-30
Lubuntu is a very light member of the Ubuntu family so it does not include all Ubuntu functionality. However, you can add stuff via Synaptic Package Manager. This is a great program as it not only allows you to add/remove packages, but is also a source of information on available packages.

So I suggest you search Synaptic for "power manager" and install any likely options.

I would expect "gnome-power-manager" to work (once installed) and you may need to launch the interface from a terminal (if there is no menu entry):-
```

gnome-power-preferences

```
...to access the GUI.

Synaptic also maintains a History (File > History), so you can use this to uninstall any packages that you tried but don't need because they didn't work for you.

---

### Post by Peadogie on 2010-10-30
Lubuntu 10.10 already has Gnome Power Manager installed. For whatever reason the developers didn't make it "visible".

Navigate to /usr/share/applications, open the Power Management .desktop file in Leafpad, and edit the line OnlyShowIn=GNOME;XFCE; to OnlyShowIn=GNOME;XFCE;LXDE; Save your change and it will then show in the Preferences menu.

You'll need root privileges to do this.

---

### Post by nick987654321 on 2010-10-31
How do i get root privileges to edit that file?

---

### Post by SteveDee on 2010-10-31
> **nick987654321 said:**
> How do i get root privileges to edit that file?

 - Navigate to the folder: /usr/share/applications using the file manager.
 - From file manager, select Tools > Open Current Folder as Root.
 - Enter your password when prompted.
 - Right click on Power Management and Open with Leafpad.

You should now be able to edit the file and then Save it.

---

