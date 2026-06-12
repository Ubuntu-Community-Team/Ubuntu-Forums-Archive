---
title: "Resetting Desktop"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by m4nm4n on 2010-03-17
I've been wanting to add some features to my drab desktop.
I've had previous modifications, and stuff added to the panels.

But is there any way to 'reset' it to it's default?

---

### Post by tom.swartz07 on 2010-03-17
> **m4nm4n said:**
> I've been wanting to add some features to my drab desktop.
I've had previous modifications, and stuff added to the panels.

But is there any way to 'reset' it to it's default?

Only easy way is to either 1) try to remember what all you changed, and undo it

2) reinstall 



as far as the panel modifications ```
rm -r ~/.gconf/apps/panel
``` will remove any changes you made to the panel

---

### Post by errrata on 2010-03-18
Alternatively you can install compiz-fusion to add all your eye-candy and use commands compiz --replace AND metacity --replace to switch.

---

