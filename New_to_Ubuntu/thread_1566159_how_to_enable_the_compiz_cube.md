---
title: "how to enable the compiz cube?"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by superarthur on 2010-09-02
when i read reviews for linux distros, compiz cubes are always shown
how do i do that?

---

### Post by Linye on 2010-09-02
Install SimpleCompiz Config from Software Center 

Then go to Appearance > Effects tab > Preferences button

---

### Post by anewguy on 2010-09-02
And make sure you have more than 1 desktop (for a cube obviously 4, but it can be more).

---

### Post by Linye on 2010-09-02
> **anewguy said:**
> And make sure you have more than 1 desktop (for a cube obviously 4, but it can be more).


I use 3, so its a triangle for me :)

---

### Post by Tracy177 on 2010-09-02
> **superarthur said:**
> when i read reviews for linux distros, compiz cubes are always shown
how do i do that?


it isnt simple first at all can your system support compiz? there on compiz web is a tool to ceck if u can or not run compiz esp 3d 

if u can then install it from synaptic

---

### Post by superarthur on 2010-09-02
which options should I tick?

---

### Post by Elfy on 2010-09-02
desktop cube and rotate cube

- trying to answer for 5 minutes - the thread kept getting spammed :lol:

---

### Post by superarthur on 2010-09-02
thanks
how to do the reflection and other fancy stuffs?

---

### Post by Elfy on 2010-09-02
Do you have compiz config settings manager installed? That is the best place to fiddle about with compiz.

[http://wiki.compiz.org/CompizPlugins](http://wiki.compiz.org/CompizPlugins) might help

---

### Post by superarthur on 2010-09-02
I have compiz config settings manager, but can't find buttons for fancy stuffs like reflection

---

### Post by realzippy on 2010-09-02
Install nearly all plugins:

[http://forum.compiz.org/viewtopic.php?f=114&t=12012#p75601](http://forum.compiz.org/viewtopic.php?f=114&t=12012#p75601)

About reflection settings:
[http://wiki.compiz.org/Plugins/Reflex](http://wiki.compiz.org/Plugins/Reflex)

---

### Post by superarthur on 2010-09-02
it seems that the ubuntu logo on the top of the cube is missing for me
there is a path to /usr/share/gdm/themes/Human/ubuntu.png in compiz config settings, but there is no such file when i go to the folder

---

### Post by GaryTheCat on 2010-09-03
I've got all the plug-ins and think I've installed them correctly - what do I need to do to see my lovely cube?

---

### Post by realzippy on 2010-09-03
...enable desktop-cube and cube-rotation in CCSM. 
...enable 4 Desktops (CCSM/General/DesktopSize/slider to "4")

---

### Post by GaryTheCat on 2010-09-03
I've done that - I get what looks like cube effects when I change workspaces but can't see that floating cube image that gets posted so often on various fora.

---

### Post by realzippy on 2010-09-03
...press mousewheel (on desktop) and rotate it.

...enable rotating cube as screensaver?

---

### Post by GaryTheCat on 2010-09-03
I suspect it's to do with me using a laptop ... I was trying to see that typical 'cube hanging in the air' kind of image

---

### Post by realzippy on 2010-09-03
> **GaryTheCat said:**
> I suspect it's to do with me using a laptop ... I was trying to see that typical 'cube hanging in the air' kind of image

...that should not make any difference if graphics driver working.

If the cube rotates,everything is OK.
You can zoom out the cube (to see it "hanging" in the air)
in CCSM/rotateCube/zoom slider

---

### Post by migs73 on 2010-09-03
> **GaryTheCat said:**
> I suspect it's to do with me using a laptop ... I was trying to see that typical 'cube hanging in the air' kind of image

Ctrl/Alt & Left click/hold and the cube will appear in space. Then use your pointing device (mouse/trackpad, whatever) to turn it around.

---

### Post by Verbeck on 2010-09-03
Follow the instructions on
```
http://forum.compiz.org/viewtopic.php?f=114&t=12012#p75601
```after that there should be a new option called 'cube reflection and deformation' and other new stuff

edit: seems like it was already suggested... i only read the first page :|

---

### Post by GaryTheCat on 2010-09-03
Thanks - worked a treat :D

---

### Post by gudurukarthik on 2010-09-03
hey i dont see any effects tab in there ? can u be more specific please

---

### Post by migs73 on 2010-09-03
> **gudurukarthik said:**
> hey i dont see any effects tab in there ? can u be more specific please

To enable/disable the desktop effects, Right Click on your desktop, select 'Change Desktop Background' (this is the same as System--> Preferences--> Appearance) then select the Visual Effects tab.
Click on the effects setting you wish.

---

### Post by realzippy on 2010-09-03
> **GaryTheCat said:**
> Thanks - worked a treat :D

More fancy:

animate skydome now and specify a nice equirectangular backround image...

---

### Post by realzippy on 2010-09-03
> **migs73 said:**
> To enable/disable the desktop effects, Right Click on your desktop, select 'Change Desktop Background' (this is the same as System--> Preferences--> Appearance) then select the Visual Effects tab.
Click on the effects setting you wish.



....this might break your CCSM settings due to a bug.When setting
up effects in CCSM and compiz runs fine,never touch those settings
given by "right-click/aso"

---

### Post by migs73 on 2010-09-03
> **Linye said:**
> Install SimpleCompiz Config from Software Center 

Then go to Appearance > Effects tab > Preferences button

It was in reference to this I think? Don't know if the Simple Compiz has this problem?

---

