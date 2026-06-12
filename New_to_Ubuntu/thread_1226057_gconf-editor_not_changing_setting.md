---
title: "gconf-editor not changing setting"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by leemajors on 2009-07-29
Hi there,

I'm trying to update the number of workspaces I have from 2 to 3 or 4 using gconf-editor, but whenever I go in there and change the workspace number and close gconf-editor nothing happens, even after a restart.

going back into gconf-editor shows the setting has been changed, but still no increase in workspaces...

any ideas?

---

### Post by wojox on 2009-07-29
Right click on the work space switcher and choose prefrences.

---

### Post by drs305 on 2009-07-29
Also remember that if you are changing the metacity workspaces they will not be reflected if you are running compiz, which keeps track of the number of workspaces independently of metacity.

---

### Post by leemajors on 2009-07-30
i don't have the workspace switcher on the toolbar -- i use docky and removed the bar at the bottom.

i do know i could enable it, set the number of workspaces and disable it again, but i'd rather learn another way of doing it as well.

how do i know if i'm running compiz?

---

### Post by earthpigg on 2009-07-30
> **leemajors said:**
> 
how do i know if i'm running compiz?

system -> preferences -> appearance -> visual effects

none = metacity

anything else = compiz

---

### Post by leemajors on 2009-07-30
seems that it's set to normal == compiz.

thus; how then do i set number of workspaces without using the workspace switcher in compiz?

---

### Post by earthpigg on 2009-07-31
> **leemajors said:**
> seems that it's set to normal == compiz.

thus; how then do i set number of workspaces without using the workspace switcher in compiz?

right click on panel -> add to panel -> workspace switcher -> right click on workspace switcher -> change it :D

---

### Post by leemajors on 2009-08-11
lol. not quite sure if you understood or not -- i know i can enable the workspace switcher, change it, then disable the workspace switcher, but surely there's another way to get to the compiz workspace settings without having to go through that step? 

Lee

---

### Post by mcduck on 2009-08-11
> **leemajors said:**
> seems that it's set to normal == compiz.

thus; how then do i set number of workspaces without using the workspace switcher in compiz?

Install CompizConfig Settings Manager, and set the number of workspaces under General settings.

---

### Post by leemajors on 2009-08-11
installing the compiz settings manager did the trick.

thanks to all who helped with this -- especially drs305 who has been helping me off-post.

---

