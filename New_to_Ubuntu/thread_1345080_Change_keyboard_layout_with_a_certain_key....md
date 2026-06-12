---
title: "Change keyboard layout with a certain key...?"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by sdim on 2009-12-03
Hi,everyone.
I was wondering if I can change the keyboard layout by using the key above TAB,the one next to 1.In KDE I've already done so.I already know about CAPS LOCK and other keys.
Many thanks.

---

### Post by sdim on 2009-12-07
```
xmodmap -e "keycode 49 = ISO_Prev_Group asciitilde ISO_Prev_Group asciitilde"
```
Run this in the terminal,and that's it.
You can then save it inside /etc/X11/xinit/.Xmodmap or make it executable (after writing it in gedit) and place it in the Startup Applications,so as for it to run at every boot.
By using this command,you can still use the certain key with SHIFT so as to type the uppercase symbol.
Many thanks to imitheos from adslgr.com,who provided the solution.

---

