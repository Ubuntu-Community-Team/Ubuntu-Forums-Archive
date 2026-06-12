---
title: "my newly installed programs arent in the menu"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by thomz92 on 2009-09-28
i recently installed supertux and wine, but they aren't appearing in the menu! i dont want to manually put launchers in there (and i dont even know how to with wine, because it's kind of a special menu). what gives?

---

### Post by ken22 on 2009-09-28
right-click menu -> edit menus -> tick the items you wish to be shown.

---

### Post by thomz92 on 2009-09-28
i already checked that...they aren't there

---

### Post by oboedad55 on 2009-09-28
> **thomz92 said:**
> i already checked that...they aren't there

Did you try a reboot?

---

### Post by thomz92 on 2009-09-28
yup...i even uninstalled and reinstalled the programs, and deleting the config files and any folders in my home folder that say .wine or .supertux or somethin like that

---

### Post by thomz92 on 2009-10-02
i think i uninstalled wine and it was still in the menu... so i deleted it from the menu. maybe thats the problem? but if i completely uninstalled it and deleted the config files and .wine file in my home folder, wouldn't everything be reset when i installed it again?

---

### Post by tahitiwibble on 2009-10-02
This might help you [http://ubuntuforums.org/showthread.php?t=616576](http://ubuntuforums.org/showthread.php?t=616576)

I had the same kind of problem which I haven't yet sorted out to my satisfaction. If you play around with "applications.menu" some strange things happen; I couldn't figure it out. Perhaps you can. Good luck.


I'm sorry not to be more helpful but I can never remember how I fixed things.

---

### Post by ad_267 on 2009-10-02
Once you've deleted an item from a menu there isn't an easy way to get it back (yes it's a bit silly). In the menu editor just click on Revert to get everything back to default.

---

### Post by tahitiwibble on 2009-10-02
**ad_267**, what **exactly** are you left with when you "revert"? 

Thanks

---

### Post by ad_267 on 2009-10-03
Clicking revert removes any customisation you have made to the menu layout. You end up with the same menu a new user just added to the system would get.

It will include any new programs you have installed, but will put everything back to its default groups and add any launchers that have been removed.

I think it's just the same as deleting everything in ~/.local/share/applications and ~/.config/menus, although I don't think it actually does delete them.

---

