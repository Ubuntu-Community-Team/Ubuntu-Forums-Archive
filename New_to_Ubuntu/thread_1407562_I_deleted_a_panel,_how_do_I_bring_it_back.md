---
title: "I deleted a panel, how do I bring it back?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Evilhugbear on 2010-02-15
Hi, I wanted to try out the AWN dock, and I have decided I don't want it anymore. I just don't know how to make a panel that shows what windows are open, the one that is at the bottom of your monitor. Is it possible to bring it back?


Thanks

---

### Post by howefield on 2010-02-15
Right click the top panel, and select new panel.

Then right click the new panel and select add to panel, you'll want window list, show desktop, workspace switcher and deleted items applets.

---

### Post by duruttye on 2010-02-15
Click on the remaining panel, and New Panel, then place it where you want it to be, the right click on it, Add to panel and add whatever you like!

Have fun!

---

### Post by NightwishFan on 2010-02-15
Run this command in a terminal:
```
gconftool-2 --recursive-unset /apps/panel
```

If your panel disappears, press ALT+F2, and type:
```
killall gnome-panel && gnome-panel
```

---

### Post by Evilhugbear on 2010-02-15
Thanks I got it :D

---

### Post by jane_gjorce on 2010-02-15
Hello! 
I have a problem with my Ubuntu. I delete the bottom panel desktop and then read the forum how to back but now there is a problem when you can reduce the window does not appear on the bottom panel to do after they downplayed a window appears on the bottom panel. I tried with the option sudo debconf gnome-panel returns to normal, but after you log back panel does not appear. 
 What can I do to return to normal as it was before the uninstall panel 
PS I use Ubuntu 9:10

---

### Post by Ameades on 2010-02-15
I believe what you want is the window list.

Right click the bottom panel.
Click Add to Panel.
Add window list. (It's 3rd from the bottom)

---

### Post by jane_gjorce on 2010-02-15
**thanks[size="6"][/size]**

---

