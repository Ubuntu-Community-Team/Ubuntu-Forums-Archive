---
title: "SHUTDOWN button vanished on Gnome."
date: 2010-05-29
forum: New to Ubuntu
---

### Post by McRat on 2010-05-29
The upper right corner on my Gnome desktop no longer has the SHUTDOWN button.  The "USER" button is there twice instead.

I figured that CNTL-ALT-DEL will pull up the menu, but does anyone know why this happens?

I did the latest updates.  I'm 10.04 32-bit with Gnome 2.30.0.

Look up in corner on the attached pic.  "patrick" is the username.

---

### Post by McRat on 2010-05-29
Rebooting did not restore it, so I need a method to edit the bar icons?

---

### Post by bcbc on 2010-05-29
right click, add to panel, select Shut down

you end up with two, but it's a workaround. or from terminal ```
sudo shutdown -h now
```

-h = halt (shutdown)
-r = restart

---

### Post by McRat on 2010-05-29
Thanks!

Whew.  I finally got back to where I can use it.

The answer to "DELETE PANEL" is NO.  More more precisely HILL NO!!  :D

I'm trying to figure out how to add a PANEL now.  I deleted the top panel.  ADD PANEL reserves space on the borders, but it doesn't seem to create a new blank panel.

---

### Post by Kafubie on 2010-05-29
If you need to shut the computer down.
Just press the power button once.  You will be prompted if you want to suspend, shutdown, etc.

---

### Post by McRat on 2010-05-29
Thanks!

Yup, it APPEARS to only reserve space for the new PANEL, but what seems to be happening, is that it is being placed on the wrong side of the screen memory border.  If the bottom is row 1080, it puts it on row 1080-1130 instead of 1030-1080.

ie - When you create a new PANEL, it clears the space for it correctly, but puts it off the screen.  You see the area for it, but only one row of pixels for the panel itself.

But when you restart, it will put it in the correct location.

Maybe.

---

### Post by bcbc on 2010-05-29
There are some instructions somewhere on restoring the top panel, involving 'gconftool --recursive-unset' (but you'll have to search for it). It only restores it to it's default, and then you need to add back your customizations.

Regarding your original problem, here's the link to the bug. No solution yet it seems. [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448)

---

### Post by bcbc on 2010-05-29
Here it is:
[http://ubuntuforums.org/showpost.php?p=7570386&postcount=2](http://ubuntuforums.org/showpost.php?p=7570386&postcount=2)

---

### Post by McRat on 2010-05-29
OK, everything is back to where it came from.  Thanks!

---

### Post by dFlyer on 2010-05-29
If it happens again just use the command line and enter:

killall gnome-panel

This will stop and restart the gnome panel to fix the icons/applications on the upper and lower panels.

---

