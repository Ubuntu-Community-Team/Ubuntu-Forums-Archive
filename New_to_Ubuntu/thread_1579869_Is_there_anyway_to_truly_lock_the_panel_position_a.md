---
title: "Is there anyway to truly lock the panel position and order?"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by kendoori on 2010-09-22
Am running 10.04 on a Thinkpad X61 laptop and often use with two screens. If I undock, or reboot, the order of the panels at the top of the screen will randomly change position, in spite of all being "locked." Is there a way to lock these in place and/or a script that I can easily run that puts them back in the right order and location? It's an utter waste of time to have to unlock, move, lock every time.

Curious as to whether this behavior crops up in 10.10

---

### Post by Elfy on 2010-09-22
There is a locked_down option in gconf-editor - have you tried that?

Alt +F2 then gconf-editor 

navigate to /apps/panel/global/locked_down and enable

Edit - no idea about 10.10 not bothered with it yet

---

### Post by JRBye on 2010-09-22
> **kendoori said:**
> Curious as to whether this behavior crops up in 10.10

I am using 10.10 and running a Thinkpad T61 and don't have that issue at all. I am still having the issue where the Resolution changes and the desktop icons are shifted when I dock/undock. I am working on a good way to fix that.

---

### Post by Gameboyman99 on 2010-09-22
Thx forestpiskie! I have problems exactly like that too, but never really gave it much of a thought
EDIT: P.S., I don't have to restart the panel for the changes

---

### Post by kendoori on 2010-09-22
@forestpiskie Your solution appears to work. I just tried switching back and forth between my laptop main screen and my large screen monitor and the panel appears locked properly.

Thanks for the tip

---

