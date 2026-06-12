---
title: "Can't switch desks 9.04"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by raequin on 2009-05-15
Greetings.  I have a pretty fresh install of Jaunty.  I switched the mouse buttons and changed the keyboard layout to Dvorak.  I swapped positions for CapsLock and Ctrl.  Also, the right alt key is no longer for 3rd level.

Anyway, I just mention that in case some of it is causing this problem.  Those are the only real changes I've made besides installing flash, java, emacs, and screenlets (which I since removed).  Oh yes, I installed the CompizConfig Settings Manager

I am unable to switch desks.  Clicking the icons in the bottom right of the screen has no effect; same for Ctrl+Alt+Arrow.  Nothing.

By adding additional desktops in CCSM I was able to get out of my current desk ... but it went into a desk with no panels and I had to Ctrl+Alt+Del and restart to get back to functionality.  I got to that funky desk or whatever by clicking a desk image on the bottom panel.

So, all I want is multiple desks.  Additional desktops might be nice; it's my understanding that they allow you to have different images on the background, whereas desks do not.

So, please help me get desks working in this install.  I find them very useful.  Thanks.

---

### Post by emacbri on 2009-05-15
Hi,

In the CCSM set the number of desktops to one and set the Horizontal Virtual Size to more than one. That should fix your problem. Good Luck!:)

---

### Post by raequin on 2009-05-15
Nope.  Thanks for the response.  I already had "horizontal virtual size" set to 4, "vertical virtual size" set to 1, and "number of desktops" to 1.

Number of desktops was briefly at four, but that acted crazy(ier).

So, I am still unable to switch desks.

---

### Post by zeroseven0183 on 2009-05-15
How about resetting the Visual Effects to either **Normal** or **Extra**?
Right-click on the desktop, select **Change Desktop Background** then go to Visual Effects.

That always works for me.

---

### Post by raequin on 2009-05-15
That did it.  I set the effects to "normal" and now I can switch desks.

Is it going to be that I have to choose between the sweet Compiz effects and using multiple desks?

---

### Post by zeroseven0183 on 2009-05-16
> Is it going to be that I have to choose between the sweet Compiz effects and using multiple desks?

Always? I think so. But I haven't found any trick to bypass/correct it.

---

### Post by networm1230 on 2009-05-16
If your computer CPU and GPU can handle compiz go with Compiz if not keep setting at default. having compiz will tax you computers hardware

---

### Post by raequin on 2009-05-16
Toggling the settings in CCSM I discovered that it is disabling "Desktop Wall" that keeps me from switching between desks.  This disabling is required to enable the desktop cube.

So I can use Compiz except for the cube, which is fine by me btw.

Thanks again.

---

