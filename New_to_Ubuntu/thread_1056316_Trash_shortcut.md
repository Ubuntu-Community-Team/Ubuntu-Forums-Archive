---
title: "Trash shortcut"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by RAiN2M on 2009-01-31
How do I put the trash icon on my desktop, I'm coming from windows xp, I'm used to having the recycle bin icon on my desktop, I know there's the bin in the corner of the screen although... I'd really prefer an icon. I've seen some people have it, please help, thanks.

---

### Post by cwsnyder on 2009-01-31
Try right clicking on the icon in the task bar and seeing if there is an option to detach the icon from the taskbar.  If not, try right clicking the open desktop and create the launcher for the trash can.

Detaching the icon worked on my GNOME desktop with Cairo-dock.

---

### Post by Elfy on 2009-01-31
Do Alt+F2 and then run gconf-editor

Navigate to apps/nautilus/desktop - enable trash_icon_visible

---

### Post by jbrown96 on 2009-01-31
Nevermind, Forestpixie had a much better solution

---

### Post by cdtech on 2009-01-31
First be sure you have the gnome configuration editor installed:
```
sudo apt-get install gconf-editor
```
Then just type in a terminal:
```
gconf-editor
```
Look under "apps > nautilus > desktop" and select to show trash_icon_visible.

After you have that selected your trash folder should show up on the desktop.

---

### Post by RAiN2M on 2009-01-31
Thanks. Solved.

---

### Post by cerberez on 2010-03-29
> **cdtech said:**
> First be sure you have the gnome configuration editor installed:
```
sudo apt-get install gconf-editor
```
Then just type in a terminal:
```
gconf-editor
```
Look under "apps > nautilus > desktop" and select to show trash_icon_visible.

After you have that selected your trash folder should show up on the desktop.

Interestingly, that does nothing for me. I close conf editor after checking that value, and nothing changes! I'm on UNR 9.1, if that matters.

thanks!

---

### Post by tommaguzzi on 2011-09-03
> **forestpiskie said:**
> Do Alt+F2 and then run gconf-editor

Navigate to apps/nautilus/desktop - enable trash_icon_visible

thank you pixie this works for me. i also got the computer icon up too!:KS

---

