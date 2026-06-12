---
title: "My Trashcan Disappeared!"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by kramer65 on 2009-04-22
From one day to the other, the icon of my trashcan in the lower right corner has just vanished!

I restarted everything, but it doesn't help. Can anybody help me get it back?


[edit] btw. I've got ubuntu 8.04.1

---

### Post by Peter09 on 2009-04-22
in a terminal type
```
gconf-editor
```

select apps->nautilus->desktop 

and tick the trash can visible box.

---

### Post by kramer65 on 2009-04-22
Hi Peter,

Thanks for that. I can access it again... That's a whole relief..

But Can't I get it back to where it was on the panel thing on the right bottom corner?

---

### Post by Peter09 on 2009-04-22
Right click on the panel and add an applet, in the menu scroll down to the trash can applet.

---

### Post by clive littlewood on 2009-04-22
Hi

Right click on the bottom panel

Click add to panel

Search the list for Trash and click on add then close

Done      :P

Clive

---

### Post by kramer65 on 2009-04-22
Alright. I've got one again now! But it is left of the desktop switch things. Can I get it to the right of it so that it is absolutely in the right corner?

One question: how can it disappear like that when I didn't do anything. This happened before with the power button on the right top as well..!:confused:

---

### Post by Peter09 on 2009-04-22
Right click on the applet and select move.

---

### Post by nandemonai on 2009-04-22
You may need to 'unlock' existing panel applets to move it. If you find you can't move it past something like the desktop switcher then right click that, uncheck lock to panel then try again.

---

### Post by Lunx on 2009-04-22
> **nandemonai said:**
> You may need to 'unlock' existing panel applets to move it. If you find you can't move it past something like the desktop switcher then right click that, uncheck lock to panel then try again.

I prefer having only one panel on desktop, so it's the first thing I change when I do a fresh install. I find it easiest to just unlock everything and then move them around to my liking and when I'm happy I lock them all again.

On a slightly different topic, I played around with the latest version of OpenSUSE and KDE and for the life of me couldn't get the icons on the panel in the arrangement I wanted. I'd move them to where I wanted but the moment I released mouse button they'd return to original position. Total PITA and even if it was an error in the way I was doing it, I couldn't have been bothered trying to figure it out, so goodbye KDE. With Gnome I figured it all out in probablly the first ten minutes of ever booting a Linux distro, and this was simply by clicking my way around and figuring it out myself, far more intuitive IMHO.

---

