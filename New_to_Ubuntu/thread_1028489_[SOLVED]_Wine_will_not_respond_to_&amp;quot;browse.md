---
title: "[SOLVED] Wine will not respond to &amp;quot;browse C Drive&amp;quot;"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Jesan Fafon on 2009-01-02
Hi, I've got Wine Version 1.1.4 and I need to access it's virtual C:\ drive, but when I click on that particular shortcut in the applications\wine menu, my computer does nothing, and using various system monitors, can not find any indication that its doing anything.

It worked once upon a time, which leads me to believe that the shortcut may have been broken or lost.

Anyways, I was hoping someone would have a suggestion as to how to fix this or get it working again.

---

### Post by ajcham on 2009-01-02
Check the Main Menu editor in System » Preferences

The command for 'Browse C: Drive' should be:
```
xdg-open .wine/dosdevices/c:
```

---

### Post by jerome1232 on 2009-01-02
Well make sure the folder exist. Goto your home folder press ctrl+h to view hidden folders and find .wine.

On my computer that shortcut points to ~/.wine/dosdevices/c: so make sure that path exists.

Make sure the shortcut is correct, right click Applications, click edit menus, click on wine, no click on browse C: drive, click properties, make sure the command looks like this without the quotes.

"xdg-open .wine/dosdevices/c:"

---

### Post by Jesan Fafon on 2009-01-02
Thank you that's done it for me!

---

