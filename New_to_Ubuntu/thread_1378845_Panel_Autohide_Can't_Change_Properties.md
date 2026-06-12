---
title: "Panel Autohide Can't Change Properties"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Gomeriffic on 2010-01-11
I had my desktop set up PERFECTLY, but wanted to see how much better it would be. So, I went to my top panel's properties and clicked autohide, even though it was already 21 pixels. So, now I can kinda see the panel, but can't open the properties dialog. How could I access the properties and turn off the autohide? Configuration Editor was my first idea, but found it nowhere in the gnome portion.

---

### Post by ScottinSoCal on 2010-01-11
I'm interested to see the response to this. I autohid my bottom panel a week ago, and haven't seen it since. I have AWN installed, and I added the trash icon to my desktop, so I'm not missing anything, but it does seem like it should pop up when I move the mouse down there.

---

### Post by Gomeriffic on 2010-01-12
Found out what your possible problem is!! I was messing around on my computer, and was fine without my top bar. THEN, out of the blue, accidentally hit my top left corner (which touches the missing bar). To my surprise, the missing bar came out!!!! So, I recommend try the corners that touch the bar. The bar might come back from the grave!!!!

---

### Post by J V on 2010-01-12
if you want a more practical fix to this issue:

```
gconftool-2 --type bool --set /apps/panel/default_setup/toplevels/bottom_panel/auto_hide false
gconftool-2 --type bool --set /apps/panel/default_setup/toplevels/top_panel/auto_hide false
```

---

### Post by ScottinSoCal on 2010-01-16
Stumbled across it this morning, then came on the post about it and saw you already had. If I move my mouse to the bottom corner, it comes back up. I can edit, I can use it, I can do whatever I need to. So I left it autohidden.

---

### Post by S.P.Q.R on 2010-10-14
compiz setting confliction!

today i enabled "desktop wall" of compiz and guess what. my panel lost! (i was using it with autohide option enabled) then i disabled desktop wall and everything is normal again, i could show panel. so desktop wall makes a problem. i opened desktop wall settings. and i seen there is an option named "edge fliping" at the "bindings" tab. inside this option it setted to flip up when my pointer touchs at the top of the screen (and which conflicts with my panel autohide process) so i removed that flip up option from the desktop wall settings and it is fixed!

---

