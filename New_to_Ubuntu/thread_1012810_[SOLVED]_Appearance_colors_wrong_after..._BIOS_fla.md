---
title: "[SOLVED] Appearance colors wrong after... BIOS flash??"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by uncibex on 2008-12-16
I have an HP DV2000 laptop and recently had to flash a new BIOS while in Windows Vista.  However, when I restarted in Ubuntu, my theme changed and I haven't been able to get my human theme back or get any color changes to work.  I'm not really sure what's going on, or if it has anything to do with the BIOS at all... that was just the most recent change to my computer.

I've tried everything I can think of working through the appearance menu, but while I'm able to change the window borders and outside shapes, I'm still stuck with a light blue color, different icons, and a boxier look.  This might instead have something to do with the updates I made to Ubuntu before restarting as well, but these were just the routine update manager packages and a package for one of my classes called eclipse.

I'm kind of at a loss, despite the fact that this seems like a very basic fix.  Any ideas?

---

### Post by uncibex on 2008-12-16
I thought a screenshot might be helpful as well to better demonstrate my problems

---

### Post by philinux on 2008-12-16
This has nothing to do with the bios.
One thing to do is to go to your home folder press ctrl h to show hidden files. Locate .gnome and .gnome2 and delete them. Logout then login again.
This will recreate these folders with the default settings.

---

### Post by uncibex on 2008-12-16
Thanks so much, that fixed it!

Any idea why the settings might have been changed in the first place?

---

### Post by philinux on 2008-12-16
In such instances the major cause is the user. :lolflag:

Have fun. If you break it again you now know the fix.

---

