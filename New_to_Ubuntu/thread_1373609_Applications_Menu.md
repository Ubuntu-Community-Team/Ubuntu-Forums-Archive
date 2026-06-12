---
title: "Applications Menu"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by ericstrom on 2010-01-05
Tried updating to the latest version of Gimp. The update seemed to go ok but now it no longer shows up under Applications/Graphics.

How do I get it back on the list ? I think it is still on my PC

Currently running Kozmic

---

### Post by gordintoronto on 2010-01-06
Preferences/Main Menu lets you control what appears in the menus.  You will need to know what program to run, perhaps gimp.  There is probably an entry for it, with "Show" unclicked, and the old program name under Properties.

From accessories/terminal you can enter the command gimp and see if it starts up.

---

### Post by SchizmWolf on 2010-01-06
> **gordintoronto said:**
> Preferences/Main Menu lets you control what appears in the menus.  You will need to know what program to run, perhaps gimp.  There is probably an entry for it, with "Show" unclicked, and the old program name under Properties.

From accessories/terminal you can enter the command gimp and see if it starts up.

I highly reccommend this advice. If that doesn't work for you, you can manually reenter it into your menu bar by opening the terminal and inputting either "keditmenu" (for KDE desktop environment) or "alacarte" (for gnome, etc.) From there you would "create new item" under the folder you want it in (probably graphics) and type in the name, a description, and in the command box: ```
gimp-2.6 %U
```
That *should* get it started and add the GIMP icon back into your menu. Good luck!

---

### Post by ericstrom on 2010-01-06
neither method worked

When I went through teminal, it added a gimp to the applications/graphics menu. But then when I tried to open gimp through the applications / graphics menu,  i got the following message

Failed to execute child process "gimp-2.6" (No such file or directory)

---

### Post by firefly2442 on 2010-01-06
How did you install Gimp?  From a package provided via the Ubuntu repositories?

---

### Post by ericstrom on 2010-01-07
Yes, I think so. I did it about 2 weeks ago so I forgot the details. I am willing to uninstall it and reinstall if that would solve the problem. But I would need a little advice on how to do that.

---

