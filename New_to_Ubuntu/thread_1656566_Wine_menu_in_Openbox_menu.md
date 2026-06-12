---
title: "Wine menu in Openbox menu?"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2010-12-31
Is it possible to have a wine menu in the openbox menu with all the configure wine, wine programs etc etc?

---

### Post by Version Dependency on 2010-12-31
> **cyb3r_sn4k3 said:**
> Is it possible to have a wine menu in the openbox menu with all the configure wine, wine programs etc etc?

Yes.  You have to manually edit the menu, of course.   But here are the things you will probably want to add:

Browse C: Drive
```
xdg-open .wine/dosdevices/c:
```Configure Wine
```
winecfg
```Uninstall Programs
```
wine uninstaller
```And to point to a specific program that you've installed in Wine, it should look something like the following:
```
env WINEPREFIX="/home/USERNAME/.wine" wine "C:\Program Files\program\program.exe"
```In the above you will change USERNAME to your name, of course. 

Best of luck!

---

### Post by cyb3r_sn4k3 on 2010-12-31
K thnx I got the first "problems" solved:guitar:. But can I make a menu which automatically updates itself? I mean if I install a new software can it be automatically added?

---

### Post by Version Dependency on 2010-12-31
> **cyb3r_sn4k3 said:**
> K thnx I got the first "problems" solved:guitar:. But can I make a menu which automatically updates itself? I mean if I install a new software can it be automatically added?

No, you will have to add it manually.  It only takes a few seconds (I assume you have obmenu installed -- if not, install it).  All you need to know is the terminal command to launch the new program(s) you have installed.  If you don't know the command, you can look it up by opening alacarte (this is the program that manages the main menu in Gnome).

---

### Post by cyb3r_sn4k3 on 2011-01-01
Yeah I geuss its ok it would be cool thought to have something like that :)

---

