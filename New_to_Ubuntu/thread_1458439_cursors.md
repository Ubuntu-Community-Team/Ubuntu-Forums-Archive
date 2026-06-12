---
title: "cursors"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by mavenuparker on 2010-04-20
i messed up the icons in usr/share/icons folder.....
someone please tell me how to restore them back into original ones....
i was actually trying to install some new mouse themes ...so replaced cursor folder of one style with another

---

### Post by Temposs on 2010-04-20
In the future, when you want to install new themes and such, you should only mess with the ~/.icons folder(and all the other theme related folders like ~/.themes).

---

### Post by gmargo on 2010-04-20
The files in /usr/share/icons/ come from many different packages.  Do you know exactly what file or directory got trashed?  Then it should be possible to find all the affected packages to reinstall them.

For instance, if you know that the gnome/16x16/stock/ directory is bad, then you can find out what package(s) the files came from with "dpkg -S /usr/share/icons/gnome/16x16/stock".  That one comes from the "gnome-icon-theme" package, so you could reinstall that package with "aptitude -V -R reinstall gnome-icon-theme".

---

