---
title: "saving xorg.conf"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by MungoDungo on 2009-08-12
I'm trying to reconfigure the resolution on my usb-drive ubuntu 9.04. In xorg.conf I've added:
> [FONT=Courier New]Section "Device"
    Identifier    "Configured Video Device"
[COLOR=Red]    Option        "PanelSize" "1200x600"[/COLOR]
EndSection[/FONT]
I opened the xorg file with:
> gksudo gedit /etc/X11/xorg.conf
But when I save it and restart the computer the old file is back again, messing up the resolution. I don't know how to solve this...

---

### Post by zerhacke on 2009-08-12
I've encountered this before.

In a terminal, type 

```
sudo displayconfig-gtk
```

and press enter.  This will bring up the GTK Xorg configuration application.  Usually (but not always) this makes the changes stick for me.

---

### Post by MungoDungo on 2009-08-12
Thank you for your answer zerhacke, however I tried: 
> gksudo displayconfig-gtk
and 
displayconfig-gtksudo 
but nothing happens... Is the GTK application something I have to download?

---

### Post by verbal.kint on 2009-08-12
I dont think there is a GUI for this config, its all through the command line.....I very easily could be wrong on this

---

### Post by CatKiller on 2009-08-12
> **MungoDungo said:**
> my usb-drive ubuntu 9.04.

Is it persistent (an actual proper install to a drive) or are you booting from an image (Live USB)? If you're running a Live USB session then you're only changing the version of xorg.conf that's in memory.

---

### Post by MungoDungo on 2009-08-13
Hi CatKiller, I use persistent and all my other changes is saved...

---

