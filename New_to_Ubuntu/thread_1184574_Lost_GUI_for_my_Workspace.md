---
title: "Lost GUI for my Workspace"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by nava2 on 2009-06-11
I have no taskbars or panels!  I cannot right click on the desktop etc, and all my icons are missing.

Only on my second workspace though! 

I also cannot switch back to my first. 

I have tried reinstalling gnome-panel, xfce etc which is not istalled on my computer I found.

So, anyone have any ideas? 

By the way, I CAN open windows, just I have to run out of a terminal.

Thanks, 
~N2

---

### Post by reeseslover531 on 2009-06-11
i know this is the standard response, but have you tried restarting your computer?

---

### Post by nava2 on 2009-06-11
> **reeseslover531 said:**
> i know this is the standard response, but have you tried restarting your computer?
Yeah, I have. :(

Its happened many times in a row.

Now, I'm just stuck in this non-panel mode some how.

As well, before, I used to have the bottom task bar, but that too is gone now.

---

### Post by reeseslover531 on 2009-06-11
if your run nautilus from the alt-f2 menu does anything come up?

---

### Post by pauna on 2009-06-11
> **nava2 said:**
> 
I have tried reinstalling gnome-panel, xfce etc which is not istalled on my computer I found.


I'm sorry if this sounds silly, but have you tried EXECUTING gnome-panel and/or gnome-wm from the command line?

Gnome-panel is responsible for the panel bars on top and bottom, and gnome-wm launches your selected window manager. They need to be run from your personal desktop session.

---

### Post by nava2 on 2009-06-11
> **pauna said:**
> I'm sorry if this sounds silly, but have you tried EXECUTING gnome-panel and/or gnome-wm from the command line?

Gnome-panel is responsible for the panel bars on top and bottom, and gnome-wm launches your selected window manager. They need to be run from your personal desktop session.

gnome-panel:
```
Cannot register the panel shell: there is already one running.
```gnome-wm:
All it did was just make a bunch of flashes and redid the bars it seems. Nothing significant changed except I have some more terminals on my current workspace.

> **reeseslover531 said:**
> if your run nautilus from the alt-f2 menu does anything come up?

Yes, the window appears.

---

### Post by Bölvaður on 2009-06-11
Try

```
killall gnome-panel
gnome-panel &
```



> **reeseslover531 said:**
> i know this is the standard response, but have you tried restarting your computer?
Standard response? it's like asking some one to turn their car on and off and check if the tire will plug it's own hole and put acceptable pressure into it.

At max you'd suggest restarting X.
Restarting the computer wouldn't do any good, probably only worse. Unless if the problem is that configs which got stored in ram but not on hdd.... oh wait that is almost impossible in linux (anything is possible and I can think of few ways but still... resarting is not the brigtest idea always).

---

### Post by nava2 on 2009-06-11
> **Bölvaður said:**
> Try

```
killall gnome-panel
gnome-panel &
```


Standard response? it's like asking some one to turn their car on and off and check if the tire will plug it's own hole and put acceptable pressure into it.

At max you'd suggest restarting X.
Restarting the computer wouldn't do any good, probably only worse. Unless if the problem is that configs which got stored in ram but not on hdd.... oh wait that is almost impossible in linux (anything is possible and I can think of few ways but still... resarting is not the brigtest idea always).

Such a simple thing just cured my ailment. 

Thank you.

---

