---
title: "Network Manager Applet disappeared from Gnome panel!"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by nalgarryn on 2010-10-10
[FONT="Palatino Linotype"]Hey guys,

I am not new to computers but am new to Linux. (more or less)

When I first started ubuntu I had the gnome "Network Manager Applet" in the panel. Now it's gone. It's still showing as installed in the software centre.

How do I get it back on the panel? When I right click and add item to panel it's not in the list!

Thanks in advance![/FONT]

---

### Post by andrewthomas on 2010-10-10
to reset your panel to the default
```
 
 
rm -r ~/.gconf/apps/panel

```
 
Then logout and back in to apply changes

---

### Post by Dyegov on 2010-10-10
Ah thanks! I screwed mien too no idea how, I'll reset it with this, thanks.

---

### Post by andrewthomas on 2010-10-10
Glad to be of help.

---

### Post by wojox on 2010-10-10
> **nalgarryn said:**
> [FONT="Palatino Linotype"]Hey guys,

I am not new to computers but am new to Linux. (more or less)

When I first started ubuntu I had the gnome "Network Manager Applet" in the panel. Now it's gone. It's still showing as installed in the software centre.

How do I get it back on the panel? When I right click and add item to panel it's not in the list!

Thanks in advance![/FONT]

When you add to panel it's the Notification Area.

---

### Post by nalgarryn on 2010-10-10
> **wojox said:**
> When you add to panel it's the Notification Area.

Thanks so much! Exactly what I was looking for!

---

