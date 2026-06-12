---
title: "Gnome Do error. Compositing? But how?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by abybaddi on 2009-03-09
Hey I just updated the Gnome Do to newest version for the sake to Docky. But the problem is that when I go to the appearance tab I get the message "Your display is not configured for theme and animation support. To use this features, you must enable compositing."

Now what the hell is compositing and how do I get the docky interface?
Please help. Know that I have AMD(Sempron) 2200+, 512 MB of RAM and particularly no Graphics card.

---

### Post by abrussak on 2009-03-09
You need to install Compiz via the Add/Remove Software app. I have an integrated graphics card and after messing with the plugins and turning off just about everything, it's very snappy. 

If you want an easier solution, right click on your desktop and go to Change Desktop Background, then Effects(I think) and then select Normal(The middle one)


I'm on my desktop, so this is from memory.

---

### Post by abybaddi on 2009-03-10
When I click on the "Normal Effects" it searches for drivers, then blinks and then Pops up "Desktop Effects could not be enabled."Now what?

---

### Post by adult swim on 2009-03-10
if you are using metacity, you can turn on compositing by hitting alt+f2 and entering in ```
gconf-editor
``` then browse to apps>metacity>general.  when you get there, check the box that says compositing_manager.

---

### Post by abybaddi on 2009-03-11
Thank you Man, it works !!!

:D

---

### Post by x3qt0r on 2010-11-08
the alt+f4 gconfig-editor technique Worked  :)

---

