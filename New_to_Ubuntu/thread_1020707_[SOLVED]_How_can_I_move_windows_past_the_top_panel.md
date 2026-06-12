---
title: "[SOLVED] How can I move windows past the top panel?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by mvalviar on 2008-12-24
When I move windows around I can move it past the bottom panel but I can't move it past the top one. I'm using compiz. It's a little inconvenient.

---

### Post by jerome1232 on 2008-12-24
> **mvalviar said:**
> When I move windows around I can move it past the bottom panel but I can't move it past the top one. I'm using compiz. It's a little inconvenient.

Hold alt, then click and drag the window while holding alt.

You can change which key does this under System-Preferences-Windows

---

### Post by retskrad on 2008-12-24
Try to change the visual effects tp another level, like from normal to none or something. it worked for me.

---

### Post by Bucky Ball on 2008-12-24
What I did is right click on the taskbar/properties and ticked the 'autohide' box. You could also try a different desktop manager/environment.

---

### Post by stanz on 2008-12-24
Yea - compiz is nice...but there's to many unexpected results that
keep ya busy trying to figure out how to adjust things.

---

### Post by jerome1232 on 2008-12-24
> **stanz said:**
> Yea - compiz is nice...but there's to many unexpected results that
keep ya busy trying to figure out how to adjust things.

@stanz: Your avatar gives me the creeps lol.

---

### Post by mkvnmtr on 2008-12-24
Thanks Jerome I never knew that and it works good.

---

### Post by mvalviar on 2008-12-27
> **jerome1232 said:**
> Hold alt, then click and drag the window while holding alt.

You can change which key does this under System-Preferences-Windows

Those are the keys I use move move windows around and I doesn't let drag beyond the top panel. Even if I remove the top panel I can't move windows past the top of the screen.

---

### Post by jerome1232 on 2008-12-27
> **mvalviar said:**
> Those are the keys I use move move windows around and I doesn't let drag beyond the top panel. Even if I remove the top panel I can't move windows past the top of the screen.

You know what it was working the other day. I just tested it and I can't either now so I don't know what to tell you lol, I tested it before I posted and I remember dragging firefox to where it was above my top panel...

---

### Post by mvalviar on 2008-12-30
*bump*

does anyone got a fix on this??

---

### Post by fooman on 2008-12-30
works for me.

try this...open firefox,  if it is maximized...unmaximize it.

use the cursor to drag the corner of the window and make it a smaller size.  press and hold the alt key while grabbing somewhere in the middle or lower part of the window (not the toolbar) with your mouse and you should be able to drag firefox beyond the top panel.

now use the cursor again to drag the window to the maximized size again. 

should work ok after that (even after maximizing the window with the maximize button).

---

### Post by mister_pink on 2008-12-30
Paste into a terminal:

```

gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0

```

---

### Post by RookieUbuntuUser58 on 2008-12-30
^^^Thanks that worked for me.

---

### Post by mvalviar on 2009-01-04
> **mister_pink said:**
> Paste into a terminal:

```

gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0

```

Thanks this is the answer I was looking for.

---

