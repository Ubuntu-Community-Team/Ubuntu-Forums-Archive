---
title: "Cannot reach bottom of window.."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by danwosere2007 on 2010-01-09
Hi dudes/dudettes i have a bit of a problem. I'm using 9.10NBR and upon pressing preference button on various aps, the sub-window is bigger\longer than the screen and even with dragging the window to nthe top of the screen i cannot actually reach the o.k\apply button to make any changes. Hope this makes sense im sure theres an easy solution to my problem, unfortunately for me im not sure what it is yet. Cheers - Dan ;)

---

### Post by nerdy_kid on 2010-01-09
press <alt> then click any part of the window and you can drag it around.  had something like this happen to me a while ago...

---

### Post by Hello Kitty on 2010-01-09
Try holding down the ALT key on your keyboard while clicking and dragging anywhere on the window, this should allow you to move it further up than dragging by the title bar. :)

---

### Post by danwosere2007 on 2010-01-09
Awesome thanks guys\girls! :)

---

### Post by nothingspecial on 2010-01-09
Copy and paste this into your terminal

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

Now, if you hold down the Alt key while you drag the window (with the left mouse button) you will be able to drag the window above the top of the screen and reach the bottom of it, if you know what I mean.

---

### Post by nerdy_kid on 2010-01-09
no problem,  have fun!  (and dont forget to mark the thread a solved!)

---

### Post by quik_lives on 2010-01-11
This didn't work for me. I copied and pasted it, and I still can't grab the window anywhere but the top bar. It's a part of Open Office that is trying to recover a document I closed without saving, which  is frustrating.

---

### Post by daimaru on 2010-01-11
just use alt+middlemousebutton to resize the window

---

### Post by nothingspecial on 2010-01-12
I should have mentioned you need to be running compiz.

Right click on your desktop and set the effect to extra.

If that doesnt work press Alt F5 to resize the window.

---

