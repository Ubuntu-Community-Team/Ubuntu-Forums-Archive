---
title: "autostart sudo program"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by buzzmandt on 2009-08-26
I have a program I want to automatically start when the system starts.  I use kde btw.

its a program that requires sudo  to use.

in a terminal I would type sudo program_name

how do i autostart a sudo script in kde?

---

### Post by Liolikas on 2009-08-26
You have to autostart it in lower level, at boot (init scripts or sth like that).

---

### Post by buzzmandt on 2009-08-26
i think I need to add to init scripts, but which one and how?

---

### Post by Liolikas on 2009-08-26
Try to add command into /etc/rc.local (without sudo).

---

