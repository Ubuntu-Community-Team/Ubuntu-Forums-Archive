---
title: "A couple weird problems just popped up"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Steve05TSX on 2008-12-25
For some reason, I can't even drag my mouse on the desktop ie: selecting all the folders/icons on the desktop

also, when changing the fonts, the applications, places, and system are not changing fonts like they usually do

another sign was when looking at a folder, typically the first item in the folder would be blinking very rapidly.

any ideas?  didn't even change anything during this time frame

---

### Post by Steve05TSX on 2008-12-25
well, it just fixed itself, but I'd still like to know what was going on if anyone knows

---

### Post by 73ckn797 on 2008-12-25
> **Steve05TSX said:**
> well, it just fixed itself, but I'd still like to know what was going on if anyone knows


I have not encountered that problem specifically. Did this happen after any changes or updates were performed? Similar weird situations have occurred but only noticed if I immediately jump to something else after making a change. I assume that things are happening in the background and I catch it before it has had a chance to "take".

There have even been several cases where I logged out and back in and no more weird behavior.

Sound like a sensible situation?

---

### Post by Kellemora on 2008-12-25
Hi Steve

Do you have WINE and/or Compiz or both running?

Occasionally we have a problem similar to what you are describing.

However, it only happens on the machine with Compiz and only with a program that was running in wine that closed itself for no apparent reason.

The same program on a machine without Compiz works fine 99% of the time.  But if it closes itself, we can't reopen it again, even though all the other programs in wine will open and run just fine.  We have to restart the Xwindow for that program to start working again.

Then, after using the next program, whether or not in wine, suddenly the mouse will act up and other Linux programs act weird, not doing what they normally do.
Again however, simply restarting the XWindow and everything begins working just fine again.

We may have narrowed our situation down to simply not enough memory and/or a swap file that is too small for the heavy graphics work we do.

TTUL
Gary

---

