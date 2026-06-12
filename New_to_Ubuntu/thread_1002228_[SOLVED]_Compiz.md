---
title: "[SOLVED] Compiz"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2008-12-04
Hello,

I am currently trying to enable the compiz cube and I am having some difficulty. I have played around with the settings to get the 3D effect, and yes I did activate the 3D option. But when I press <control><alt>down I get a banner. If I use <control><alt>left/right I get a cube, but it is not the same graphical effect and I cannot figure out how to make it smaller or how to navigate it with the mouse instead of arrow keys.

---

### Post by Michael.Godawski on 2008-12-05
So compiz is working....

Try to use your middle mouse button, if you have one. Click it on your desktop and move the mouse around. The Cube should be there...

---

### Post by Wrathchild9 on 2008-12-05
I know it's a silly question but where can I set up the compiz? I have Interpid.

---

### Post by philinux on 2008-12-05
In synaptic or

sudo apt-get install compizconfig-settings-manager

There is also simple-ccsm

---

### Post by Michael.Godawski on 2008-12-05
Wrathchild9, there are no silly questions...

Perhaps it works out of the box for you... go to system > preferences > appearance > visual effects and choose between normal or extra. Does it work?

edit: for more options install the package [philinux ]("http://ubuntuforums.org/member.php?u=353083")suggested[URL="http://ubuntuforums.org/member.php?u=353083"].
[/URL]

---

### Post by Wrathchild9 on 2008-12-05
Ok. Thank you guys. :) I knew there's something has to be installed but I didn't remember what it is.

---

### Post by benjamin.s.vaccaro on 2008-12-05
Okay, so I tried <control><alt>button1 and that did activate the cube, but not from an external view. Instead I was positioned in the middle of the cube. <control><alt>middle button does nothing.

---

### Post by Wrathchild9 on 2008-12-05
The cube works for me, but it's actually not a cube, much more a flat rotating square :D

---

### Post by Sarmacid on 2008-12-05
To fully configure compiz, including keybinds, you have to download the ccsm. Look for it in the add/remove menu.

---

### Post by Wrathchild9 on 2008-12-05
> **Sarmacid said:**
> To fully configure compiz, including keybinds, you have to download the ccsm. Look for it in the add/remove menu.

It's done. This is not the problem.

---

### Post by oldos2er on 2008-12-05
> **Wrathchild9 said:**
> The cube works for me, but it's actually not a cube, much more a flat rotating square :D

 You have to enable four workspaces.

---

### Post by benjamin.s.vaccaro on 2008-12-05
Just to remind everyone of the original issue behind this thread, I have these cube settings enabled.
**_CompizConfig Settings Manager:_**
**Desktop:**
Desktop Cube
Rotate Cube
**Effects**:
3D Windows
Cube Reflections

**Under Visual effects:** 
Extra

I also have four desktops.

These are the issues:
To activate the Desktop Cube I have it set to <control><alt>down
When I press those activation keys instead of getting a lovely 3D cube I get a 2D banner with all four desktops that I can cycle through. 
If I press <control><alt>right or left I get a cube animation the size of my screen. 
If I press <control><alt>button 1 I can control the cube with my mouse. However, I am positioned in side the cube and that is my camera view - within the cube. What I want is the 3D view with the camera angle outside of the cube.

---

### Post by satanic-yobbo on 2008-12-05
in ccsm in the cube settings there is a box that can be checked that says "inside" which refers to the view you see of the cube... uncheck that box and you will see the outside view of the cube ...this can be found in the behaviour tab in the desktop cube option..

---

### Post by razy60 on 2008-12-05
in compiz(ccsm): Desktop-rotate cube(highlite the icon)-under general settings you will see zoom, change the settings to 0.5 and then work left or right from there to make the cube larger or smaller.

Raz

---

### Post by benjamin.s.vaccaro on 2008-12-05
Wow, I feel like a complete moron for not noticing that. Thanks so much.

---

### Post by satanic-yobbo on 2008-12-05
no worries . glad i could help :) ...

---

