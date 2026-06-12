---
title: "Wine"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by atliia on 2008-12-06
I am using 8.10. I have just uninstalled WINE using the purge method, however I still have the programs that were installed while I was using wine displayed under the Applications menu. To the best of my knowledge I have also deleted the folders in the C drive in ~/.wine/..../ c: that contained the software. If anyone would like to offer any insight as to how I might be able to go about removing these items from the menu I would be grateful.

---

### Post by lovelyvik293 on 2008-12-06
HAi go to system->preferances->main menu.
And you can remove whatever you want.

---

### Post by atliia on 2008-12-06
If I do it that way then I will not be able to use any wine programs. My intent is to get rid of the programs that are uninstalled but still being displayed. I still wish to use wine in the future.

---

### Post by lovelyvik293 on 2008-12-06
You can remove the only removed wine apps from this menu editor.

---

### Post by jonathonward on 2009-01-19
I have the same problems too, I installed wine and then proceeded to install Wine doors.

Installed Adobe Flash & Dreamweaver 8.

As they werent launching correctly I tried to uninstall through wine doors and that didnt work. So I uninstalled Wine too thinking it might take with it the menu's . It hasnt :(

I understand you can remove the menu items using menu editor but I hate knowing the menu is still there under menu editor just hidden.
---------------
Try following this

nautilus ~/.local/share/applications/wine

Once I removed them from that directory, they disappeared.

--------------------------

---

