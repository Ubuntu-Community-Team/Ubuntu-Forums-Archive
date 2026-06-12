---
title: "putting a downloaded executable on the menu"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by tjefferson on 2009-06-17
Hi!
I recently downloaded a program in ".tar.bz2" format. I right-clicked its icon and selected "extract here." Now I have a new directory on my desktop that contains the executable file. If I open the directory and double-click the executable, I can open the application. However, I want to be able to access the application from the main menu. Preferably, the directory would also be moved off my desktop. In addition, I use Gnome-Do; how do I make the two compatible?

I realize I would not have this problem with a ".deb" file, right? I simply couldn't find one in this case. Thanks so much for any help!

---

### Post by Cheesemill on 2009-06-17
You  can move the directory to where-ever you wish, maybe create a Programs directory in your home folder and put it in there.

To add it to your menu just go to System > Preferences > Main Menu, click on the sub-menu you want it to appear on then click on 'New Item'.

Give it a name and just put the full path to the executable in the command field and you're good to go.

---

### Post by KOld Iron on 2009-06-17
> **tjefferson said:**
> 
...

I realize I would not have this problem with a ".deb" file, right? I simply couldn't find one in this case. Thanks so much for any help!

Not automatically, but if the person having created the DEB package has done the job properly a menu entry should be created using a "application-name.desktop" file, which is normally put in the "/home/$username/.local/share/applications" directory (and that is the same directory where your manually created entry will be stored as well)

---

