---
title: "Load script with only certain DM?"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-01-26
I was wondering if there was any way to get a script to only start with a specific Desktop Manage? I have two scripts that will only work in Gnome, but I want to try LXDE. Any thoughts?

---

### Post by Brandon Williams on 2010-01-27
Do you mean that you are trying to prevent a configured Startup Applications (a.k.a. Autostart Application) from running outside of a Gnome environment? If so, [look here](http://ubuntuforums.org/showthread.php?t=1382965) for a general description of how it works. I expect that you would want 'OnlyShowIn=GNOME;' in the corresponding .desktop file.

---

### Post by slughappy1 on 2010-01-28
That is exactly what I want, but what if it doesn't have a .desktop file? I have two simple scripts. The first one changes the background randomly, and the second one changes the xsplash to my background.

---

### Post by Brandon Williams on 2010-01-29
How are those two scripts being launched currently? If it's via 'Startup Applications', then there will be .desktop files.

---

### Post by slughappy1 on 2010-01-29
As a matter a fact they are. I didn't know their would be a .desktop file. Where are they located?

---

### Post by Brandon Williams on 2010-01-29
The post that I linked to previously explains where to find the .desktop files and how to make them do what you're trying to do.

---

### Post by slughappy1 on 2010-01-31
Ok thanks. That helped a lot. I followed what it said and it worked perfectly. After logging into LXDE however PCMan File Manager is now the default file manager in Gnome. How can I make Nautilus the default in Gnome, and PCMan in LXDE?

---

