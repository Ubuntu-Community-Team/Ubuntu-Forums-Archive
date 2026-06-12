---
title: "resizing terminal"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by theRightNee on 2009-02-07
hey everyone,

using xubuntu's terminal emulator and i find it annoying that i cannot resize the default size of the terminal..every time it opens i need to spend an extra second changing to a more manageable size (my screen is only 1024x768) any ideas? thanks!

---

### Post by Locutus_of_Borg on 2009-02-07
```
echo XTerm*geometry:100:50 >> ~/.Xdefaults
```

modify to your size desires, restart xterm, should now be new size

---

### Post by theRightNee on 2009-02-08
hey thank you for the reply! but unfortunately, there was no change to the terminal's initial size.any other possiblities?

---

### Post by ugm6hr on 2009-02-08
I think there is a --geometry option that allows this (I don't use xfce on this computer - so can't check).

If so, you could just change the command for launching (e.g. desktop or panel shortcut) - I can't remember if it is possible to modify commands in xfce menu.

It is something like this:
[http://ubuntuforums.org/showpost.php?p=1532445&postcount=3](http://ubuntuforums.org/showpost.php?p=1532445&postcount=3)

Perhaps try:
```
xfce4-terminal --geometry 480x320
```

---

### Post by theRightNee on 2009-02-08
thanks for the tip! it works..but i can't make it permenant because i can't figure out how to modify the menu option, when i go to modify the menu through the settings manager, i can't modify the launcher for the terminal..

---

### Post by ugm6hr on 2009-02-09
I haven't used XFCE regularly for some time (I have it on a work computer, but don't interefere with that any more - just use it).

However, all automated menus are created the same in freedesktop systems.

This might help: [http://ubuntu-lxde.wikidot.com/menu](http://ubuntu-lxde.wikidot.com/menu)

If you give the output from:
```
ls /usr/share/applications
```

This will list the xfce4-terminal .desktop file (it is probably xfce4-terminal.desktop (look for something like that) - we'll call it that in the example below (replace as necessary).

Then:
```
cd /usr/share/applications
sudo cp *xfce4-terminal.desktop xfce4-terminal.desktop*.bkp
gksudo mousepad *xfce4-terminal.desktop*
```

Look for the **Exec=** line and change to:
```
Exec=xfce4-terminal --geometry 480x320
```

Save and close Terminal.

Reboot, and it should work.

Not sure if this is the recommended way to edit menus in XFCE - but it will work (and can be reversed easily by copying back the .bkp file.

---

