---
title: "desktop on/off button"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by ub9876 on 2010-11-11
anyone come up with a ready to go big icon  off,shut down button
for the desktop??   10.04

---

### Post by kerry_s on 2010-11-11
you can make that.
right click on the desktop & create a launcher.

name it what ever you want.
for the command: **/usr/lib/indicator-session/gtk-logout-helper -s**
click on the icon to select your icon

after thats done right click on the launcher an select resize.

you can make all 3 if you want.

you can also use "gnome-session-save", do "gnome-session-save --help" to see the commands.

---

### Post by ub9876 on 2010-11-11
i want shutdown, not log out.  I changed the logout to shutdown but didnt work...

---

### Post by qamelian on 2010-11-11
> **ub9876 said:**
> i want shutdown, not log out.  I changed the logout to shutdown but didnt work...
The command he gave you was for shutdown, not logout. The -s tells gtk-logout-helper to shutdown the computer.

---

### Post by kerry_s on 2010-11-11
don't think, just follow the directions.

---

