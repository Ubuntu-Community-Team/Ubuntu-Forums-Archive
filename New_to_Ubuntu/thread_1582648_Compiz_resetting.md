---
title: "Compiz resetting"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by corncob on 2010-09-26
I checked desktop cube and rotate cube, which disabled desktop wall, in the compiz setting manager.  Everything works fine -- I even get a hexagon when I increase the number of work spaces to six.  Thing is, it stopped working on two occasions.  When I went into the settings manager I found that the cube boxes had become unchecked and the desktop wall had become checked again.  Of course, on both occasions I was trying to impress people with what Linux can do.  Question is, is there something I unknowingly do that disables the cube?

---

### Post by corncob on 2010-10-06
I'm going to answer my own question in case somebody else is experiencing the same thing.  When I go to System > Preferences > Appearance > Visual Effects I see that nothing is checked.  When I check something, even the "Extra" button, the cube is disabled and desktop wall is re-enabled.  When I enable the cube the buttons in Visual Effects become unticked.  I guess I'll just leave it that way.  The cube seems to override it?  The other thing I'm using (wobbly windows) doesn't seem to be affected.

---

### Post by e79 on 2010-10-06
> **corncob said:**
> I'm going to answer my own question in case somebody else is experiencing the same thing.  When I go to System > Preferences > Appearance > Visual Effects I see that nothing is checked.  When I check something, even the "Extra" button, the cube is disabled and desktop wall is re-enabled.  When I enable the cube the buttons in Visual Effects become unticked.  I guess I'll just leave it that way.  The cube seems to override it?  The other thing I'm using (wobbly windows) doesn't seem to be affected.

From my personal experiences, every time I changed the 'Theme', the 'Visual Effect Extra' button is beeing unchecked; but everything is still works fine in compiz. When I check it, it rolls back Compiz to its original settings. Nothing I can explain here but it always do that. So now, when I want to change the Themes, I simply avoid checking/unchecking the Visual Effect Extra' button and Compiz does not reset.

Just my 0.02$

---

### Post by corncob on 2010-10-06
Thanks.  Just wanted to know what's going on.  I'll mark the thread as solved.

---

### Post by qamelian on 2010-10-06
The problem is that the effects settings in the Appearance applet contain a specific group of compiz settings. If you adjust the settings using compiz config settings manager, and then decide to change settings in the appearance applet, the appearance applet resets the effects back to whichever of the two presets you select. The moral of the story is that you should forget about adjusting effects in the Appearance applet if you fine tune effects in ccsm. On the other hand, if you really severely screw up your compiz settings, its nice to know you can quickly reset the mess back to something resembling normal from the Appearance applet! :)

---

### Post by e79 on 2010-10-06
> **qamelian said:**
> On the other hand, if you really severely screw up your compiz settings, its nice to know you can quickly reset the mess back to something resembling normal from the Appearance applet! :)

Definitely good to know, thanks for pointing it out !

---

