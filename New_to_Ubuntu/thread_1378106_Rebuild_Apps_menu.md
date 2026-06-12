---
title: "Rebuild Apps menu"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by humphreybc on 2010-01-11
My applications menu is all screwed and has crap left over from applications I uninstalled ages ago.

I remember seeing somewhere that you could just delete a file in your home directory and then log out and back in and it would rebuild your Application menu for you.

What is this file?

---

### Post by ibninja on 2010-01-11
run
mv .gnome .gnome.bak
mv .gnome2 .gnome2.bak
mv .gconf .gconf.bak
mv .gconfd .gconfd.bak
mv .metacity .metacity.bak
in terminal, then either restart gnome (ctrl alt F1, then ctrl alt F7 will do this, I believe), or restart your computer and it should be back to the initial configuration. If this isn't what you want, or it messes something up, delete the new .gnome .gnome2 etc files and mv the .bak files to their original titles, then restart.

---

### Post by humphreybc on 2010-01-11
Hmm I don't want to do that, I actually managed to just get the menu back to normal by deleting the applications folder under .local and logging out and back in.

But I reinstalled Wine and now can't get Wine to show up in the menu.

---

### Post by ibninja on 2010-01-11
[http://ubuntuforums.org/archive/index.php/t-619974.html](http://ubuntuforums.org/archive/index.php/t-619974.html)

---

