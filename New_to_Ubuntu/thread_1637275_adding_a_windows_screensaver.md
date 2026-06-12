---
title: "adding a windows screensaver"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-04
i am trying to figure out how to add a windows screen saver to the screensaver folder. i can run it from the desktop fine in fact i even made a launcher and added it to my top panel. but when i tried to add it to the screensaver folder
/usr/share/applications/screensavers
then did this
made the owner root
and made it  -rw-r- r (like all the rest of the screensavers in folder were)
and open with wine
couldnt get it to show up as an option when i opened the application screensaver
tks

---

### Post by Frogs Hair on 2010-12-04
never mind

---

### Post by rburkartjo on 2010-12-06
i just bumped to see if anyone does know how to/tks

---

### Post by slidersv on 2011-01-08
> **rburkartjo said:**
> i just bumped to see if anyone does know how to/tks

Well, the most important thing is to get screen saver to work. Getting it to "appear" as a screensaver in a list is not really a problem.

The screensaver does not appear in the list, because items in the menu (individual screensavers) are not referenced by desktop files but  by their xml counterparts. They are located at:
```
/usr/share/xscreensaver/config
```

What I did was to select a screensaver I don't like, and edit it's ".desktop" file to include my windows screensaver.

The wine command works to launch the screensaver, but when I put the same line in my .desktop file, the screensaver is just a black screen :(

Here is the .desktop file I have sacrifised, so I don't have to create a .xml for the list:
```
[Desktop Entry]
Name=AntSpotlight
Exec=wine /home/atlas/.wine/drive_c/windows/zenith.scr /s
TryExec=wine /home/atlas/.wine/drive_c/windows/zenith.scr /s
Comment=Draws an ant (with a headlight) who walks on top of an image of your desktop or other image. Written by Blair Tennessy.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```

The following line works without the problem
```
wine /home/atlas/.wine/drive_c/windows/zenith.scr /s
```

But when it's as a screensaver then it doesn't work :(

---

