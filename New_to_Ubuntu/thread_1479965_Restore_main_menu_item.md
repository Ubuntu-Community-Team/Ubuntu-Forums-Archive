---
title: "Restore main menu item"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by pi24 on 2010-05-11
Hi! 

I've accidentally deleted Wine from the main menu (fool me :))
Wine is still up and running, though.
I've tried reinstalling it but no change.

I'd like to restore it in the main menu, and also it's content, is it possible?

Thanks in advance!
Cheers,
PI

---

### Post by howefield on 2010-05-11
Have you checked..

System > Preferences > Main Menu

to see that the relevant menu items are checked to appear on your application menu ?

---

### Post by pi24 on 2010-05-11
Yeah, that's where I've deleted them successfully! :D

So that there are no "Wine" appearing, nothing to check, since deleted.

---

### Post by howefield on 2010-05-11
Hmm, have you rebooted since reinstalling ?

Not sure if it is still the same, but wine used to need a reboot (or at least a log out/back in) to get the icons on the menu.

Failing that, you might need to manually create them using the Main Menu option.

---

### Post by pi24 on 2010-05-11
Yes, I did reboot it, but nothing.

Also, I've thought about reproducing the menu, but I don't know where it's content located.
I've investigated ./wine/drive_c/Program Files, etc. but I haven't seen the wine-config.

However, it's a bit strange for me that reinstalling did not solve the problem...

---

### Post by howefield on 2010-05-11
> **pi24 said:**
> Also, I've thought about reproducing the menu, but I don't know where it's content located.
I've investigated ./wine/drive_c/Program Files, etc. but I haven't seen the wine-config.

I guess all you need is for someone to tell you what the properties of each Wine menu item is ?

---

### Post by pi24 on 2010-05-11
Great, thanks!
Could you please tell me one more: where can I find "Add-remove wine programs"?

---

### Post by howefield on 2010-05-11
> **pi24 said:**
> where can I find "Add-remove wine programs"?

I don't have that one my list, my (default) menu listing looks like

Programs > Accessories > Notepad
Browse C;Drive
Configure Wine
Uninstall Wine Software

The properties for Uninstall Wine software is as follows...

---

### Post by pi24 on 2010-05-11
Thank you very much! 

This is what I wanted! :D

Cheers,
PI

---

