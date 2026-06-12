---
title: "how to restore default objects to top panel"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by kiriath-arba on 2009-07-28
Is there a bash command to do this?

In particular, I just want to restore the current user name to the top right hand corner after accidentally removing it.   I can right-click on a blank section of panel and select "Add to Panel..." but user name is not one of the objects in the list.   Thanks.

---

### Post by wojox on 2009-07-28
Scroll down and click 

User Switcher

---

### Post by kiriath-arba on 2009-07-28
Thanks wojox, sorted.

---

### Post by Subiono Ahmad on 2009-12-29
Hi, need help plz...I accidentally removed my batery & network indicator on my panel. How to restore it :(:(:(????? I'd try it with "Add to panel" but i can't found it on the option below then i try using this command :


gconftool &#8211;recursive-unset /apps/panel
 then,type this to delete current one:
rm -rf ~/.gconf/apps/panel
Finally,reload panel:
pkill gnome-panel

but still doesn't work.

---

### Post by MelDJ on 2009-12-29
you should add the notification area

---

### Post by Subiono Ahmad on 2009-12-29
**4 MelDJ, thanx a lot the clue dude coz IT WORKS !!!! **=D>=D>=D>=D>

---

