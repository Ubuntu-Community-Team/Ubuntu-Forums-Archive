---
title: "windows only open in upper corner???"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by jmedoro on 2009-05-08
i must have done something wrong, probably trying to install compiz (its all i ever fool with, havent been successful once), b/c now i have a strange problem.

no matter what i am trying to run (i.e, firebox, add/remove programs, ANYTHING), the window will open as if its anchored to the upper left corner of the screen. this window will also run along the top of the screen and overlap the top taskbar, covering everything on it.

firefox opens like it will work, but when i try to type a website in, nothing happens.

what the hell is wrong?

---

### Post by Didius Falco on 2009-05-08
Try pressing F11 and see if that fixes it.

---

### Post by jmedoro on 2009-05-08
F11: no dice. it did something in firebox (i couldnt get the window large enough to really see), but didnt do anything if i had the Evolution window open, add/remove window, etc.

one more thing: sometimes i am able to grab the RIGHT side/corner of the screen and drag the screen larger, but other times (after restarting), i am not, i'm just stuck with however the window opened.

what the F.

---

### Post by Didius Falco on 2009-05-08
Try switching to metacity with this command and see if that helps:

```
metacity --replace
```

Or, if you have the Compiz-Fusion Icon installed, you can switch it from that.

---

### Post by jmedoro on 2009-05-08
> **Didius Falco said:**
> Try switching to metacity with this command and see if that helps:

```
metacity --replace
```

Or, if you have the Compiz-Fusion Icon installed, you can switch it from that.


close! 

i tried this and it worked, but ONLY IF I KEPT THE TERMINAL WINDOW OPEN, as soon as i close it, the windows go right back to being locked in the corner.

another thing i am noticing is that when the window is locked, there is no (in my case) black bar running across the top of the window, where the minimize/maximize icons are located. these appear when i type 'metacity --replace,' but disappear again when i close the terminal window.

in addition, take a look at my output, see if this means anything:

> $ metacity --replace
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x36001b1 (Ubuntu Sta); these messages lack timestamps and therefore suck.


---

