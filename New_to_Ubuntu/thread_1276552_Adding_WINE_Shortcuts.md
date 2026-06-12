---
title: "Adding WINE Shortcuts"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Swenghk on 2009-09-27
How do I add a .exe shortcut to the Applications > Games, menu?

---

### Post by MelDJ on 2009-09-27
copy the command that launches it from the wine menu. then make a new shortcut in the games menu with the command

---

### Post by bruno9779 on 2009-09-27
There are a number o ways to do this.

The easiest way is :

-right click on "applications" and choose "edit menus"
-move or copy the launcher of you choice from "wine" to where you need or want it

If it is not there, you will need to find the .exe and create a luncher, but let's not get there if not needed

---

### Post by Swenghk on 2009-09-27
How do i found the command that wineuses? It's not in the menu, you don't install it. You just click on it to play it

---

### Post by bruno9779 on 2009-09-27
you need to make a custom launcher.

So, in "edit menus" > "games" create a new launcher with something as follows

name: Utorrent

command:
```
wine /home/bruno/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe 
```

of course replace "/home/bruno/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe" with the path to your app

---

