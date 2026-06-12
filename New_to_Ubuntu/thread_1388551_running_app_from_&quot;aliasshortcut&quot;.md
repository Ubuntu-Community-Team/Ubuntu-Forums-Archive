---
title: "running app from &quot;alias/shortcut&quot;?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by NutmegCT on 2010-01-23
Good morning all.

I've installed DOSbox via the Ubuntu/SoftwareCenter.   DOSbox is now installed somewhere in the system area, which evidently was the default install area.

But I can only run it by going to that folder, and running from there. 

How can I create a shortcut or alias to put on my desktop, so I don't need to search.  DOSbox isn't listed in the Applications dropdown menu.

All the files are shown as locked.  If I rightclick any file in the DOSbox folder, the Make Link option is greyed out.  Trying to drag the files or folder only gives me an error "permission denied".

Any suggestions?

Thanks.
Tom

---

### Post by nothingspecial on 2010-01-23
Where is it?

You either need to put in your current $PATH

or add it yo your $PATH

---

### Post by bobtfish on 2010-01-23
Several ways I can think of.

1. Press alt+f2 to bring up the run application box. Tyoe "gksudo nautilus" and enter your password. Now you are going through your files as admin, so you should be able to use the right click menu to make link, then drag it to your desktop.

2. Another way is just to add it to your menu. I think the command to run dosbox is just "dosbox". Try typing that in the alt+f2 box and see if it runs. If not then the command is different and you need to find out what it is.
If it does work, you can create a menu entry to run that command. Right click Applications, go to Edit Menus. Select the subfolder you want in the left hand pane. Then click New Item on the right. Type "dosbox" in the command box, and whatever else in the name/comment boxes. Then Ok and Close, and it should be on the menu.

Chris

---

### Post by NutmegCT on 2010-01-23
Chris - I followed your directions, ran it from Alt-F2, then added it to the menu.  Success.

Thank you!
Tom

---

