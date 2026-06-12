---
title: "Task bar changed in 9.10?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by echo314 on 2009-12-06
In previous versions, I'm used to having an icon for open programs in the upper left. For example, if I open up Pidgin, and then click the X in the upper right corner, the window will close, but I have not quit the program entirely. I can just access it from that upper right icon, to have it restored. Not so anymore. I have tried various extras in the panel, none seem to replicate this functionality.

---

### Post by dwasifar on 2009-12-06
Well, Pidgin's a special case.  If you close the window, it minimizes to a tray icon - a little text balloon with green circle at the upper right.  To close it completely, right-click that icon and choose Quit.

If you're saying that you don't see entries for ANY open window in the upper panel, the item you want to add to your panel is Window List.  Right click on an open area of the panel, choose Add To Panel, select Window List, and position it as you want on the panel.

---

### Post by issih on 2009-12-06
Under Tools->Preferences in Pidgin there should be something about system tray. I forget what its called exactly as I've been using empathy (slightly begrudgingly) since karmic, but toggling one of those should fix it for you I think, although it will depend on if you are somehow falling foul of legacy code from the previous version where I think pidgin's icon was integrated into the notification icon (the little envelope).

Have a look there anyway, and if not have a look at the notification icon, as the next most likely culprit.

---

