---
title: "Bringing back taskbar."
date: 2009-09-11
forum: New to Ubuntu
---

### Post by deepaksrm on 2009-09-11
Hi, I am a newbie and i was experimenting with cairo-dock. Since my eyes were hurting to see both taskbar and cairo-dock same time at the bottom, i closed the taskbar by 
Right click -> Close panel.

At a point of time i no more liked cairo-dock and removed it.

Now im not able to bring back the taskbar at the bottom.
How can i bring it back? 
Since i was using windows all this time, i am calling the panel as "Task Bar". I dont know if it is correct and sorry if im wrong.

---

### Post by scragar on 2009-09-11
Alt+F2 type:```
gnome-panel
```

---

### Post by deepaksrm on 2009-09-11
Thanks for the reply.
I get this error message when i typein gnome-panel in terminal.

> gnome-panel
Cannot register the panel shell: there is already one running.


---

### Post by scragar on 2009-09-11
Bah, stupid things.
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
gnome-panel &
```
Run those one after another.(In order they remove the current panel settings, which is the reason you have no panels appearing, then close off the current panel session, then start a new once).

---

### Post by deepaksrm on 2009-09-11
Thanks mate, it worked!

---

