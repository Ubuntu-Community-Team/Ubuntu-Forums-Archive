---
title: "How to edit a &quot;desktop configuration file&quot;?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Gias Kay on 2009-01-17
Ubuntu Intrepid

I tried:
```

gksudo gedit /usr/share/applications/Panel.desktop

```

But it displays nothing (literally a blank file, but it cannot be - it's 12.2 KB big).

Any idea how to get this work properly? Thanks.

---

### Post by cdtech on 2009-01-17
What are you trying to configure? The user configuration file is located within "~/.gconf/apps/panel". Be sure to do a backup of the config file if you plan on changing it.

---

### Post by mcduck on 2009-01-18
Sounds like you have mistyped the file's name/path. If you try to open a file that doesn't exist a new file is created with the filename you used when starting Gedit...

(I just checked and the file name for the panel's launcher file is /usr/share/applications/gnome-panel.desktop.)

Anyway, cdtech is right, the panel configuration is done with Gconf and editing the .desktop file is not likely to be any use for you.. If you wish to change panel settings start the gconf-editor and you'll find the panel's settings in /apps/panel/.

---

