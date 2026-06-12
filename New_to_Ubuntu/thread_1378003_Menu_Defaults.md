---
title: "Menu Defaults"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by tomcatjosh on 2010-01-10
I accidentally deleted an inportant panel from my top menu bar. Is there any way to reset the menu bar at the top back to defaults? 

Thanks!

---

### Post by howefield on 2010-01-10
If it is just an application missing from the panel, you can right click on the panel and select add to panel, ect...  if you want to totally reset to default do the following.

Open a terminal (Applications > Accessories > Terminal) and type the following 3 commands.

```
gconftool-2 &#8212;&#8211;shutdown
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

---

### Post by warfacegod on 2010-01-10
What was on the panel that you want back. (FYI the "menubar" is called a panel.)

---

