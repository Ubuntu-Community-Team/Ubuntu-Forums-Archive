---
title: "I made a launcher to fix the Mouse cursor with compiz problem"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-10
I figured it out and I made a launcher to make it easier for others. I don't know how to make it installable so I just put instructions and everything you need to make a good looking launcher to fix the problem more easily until Compiz patches it.

---

### Post by Legendary_Bibo on 2010-06-10
Oh I messed something up. It has to be set to 'run in the terminal'. When I made it I had the temporary root privileges from doing something else. Otherwise it won't do squat.

---

### Post by kerry_s on 2010-06-10
run this command:
**gksudo -u gdm dbus-launch gnome-appearance-properties**

you can change all the defaults, it affects gdm to.

if the accessibility gets turned on, you can turn it back off in preferences-> keyboard

---

### Post by Legendary_Bibo on 2010-06-10
> **kerry_s said:**
> run this command:
**gksudo -u gdm dbus-launch gnome-appearance-properties**

you can change all the defaults, it affects gdm to.

if the accessibility gets turned on, you can turn it back off in preferences-> keyboard

Oh that works too I guess. I didn't try it but does it help fix the issue with the mouse cursor with compiz?

---

### Post by kerry_s on 2010-06-11
it allows you to set the default settings for the system, so everything you can do in preferences-> appearance
you can do there, it's the same program.

you can run it to see for yourself, just close it if you don't want to change anything.

here's what it does:

---

### Post by ben2talk on 2011-05-10
None of this stuff is working. I have Obsidian cursors set in appearance properties, checked in gconf-editor too, and it works great when I switch metacity --replace.

When I switch compiz --replace it's borked again.

---

