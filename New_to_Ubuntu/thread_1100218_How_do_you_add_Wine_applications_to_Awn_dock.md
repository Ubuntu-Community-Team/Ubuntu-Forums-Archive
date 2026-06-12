---
title: "How do you add Wine applications to Awn dock?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-19
I've tried dragging and dropping from the menu and nothing happens, and I have tried creating a launcher on the desktop and then dragging that and it doesn't work.

Any ideas?

---

### Post by mc4man on 2009-03-19
You add it thru your awn manager (r. click in dock. 'dock preferences'
Then click on 'launchers' -> add

For command you can try your normal path to wine prog exe but i think either of these 2 'formats' is preferable.

Ex.
PgcEdit which is in /home/doug/.wine/drive_c/Program Files/foo/
> 
wine "C:\\Program Files\\foo\\PgcEdit.exe"

> env WINEPREFIX="/home/doug/.wine" wine "C:\\Program Files\\foo\\PgcEdit.exe"

As far as an icon if one was installed you'll need to track it down. The most likely place (if not in the progs folder) is in home folder -> ./local/share/icons

Click on the icon in the launcher set up, wait till it opens and then to browse to either .wine or .local click on directory -> other


If it doesn't accept the icon's file format then convert to .png in gimp (48/48 should be good


Here's a related thread, plus alternate method for some progs (progs that are 'standalone' .exe's can usually be placed in the windows folder. Then you create a wine wrapper script for it with the name you wish to use as a command. For instance I could call PgcEdit.exe with simply pgcedit


[http://ubuntuforums.org/showthread.php?t=1071096](http://ubuntuforums.org/showthread.php?t=1071096)

---

### Post by humphreybc on 2009-03-19
:D Thankyou so much!

---

