---
title: "hi how do i load the new firefox"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by blake7 on 2009-08-05
hi i have just down loaded and extrated firefox 3.5.2 to my desktop
will i lose any of my book marks and my large scapbook pages

thank you 
ps please keep it simple cheeeeeeeeeeeeersss

---

### Post by original_jamingrit on 2009-08-05
[COLOR="Red"]_Disregard this post_[/COLOR]
[COLOR="Gray"]
I can't tell you for sure, but in your home directory there is a hidden folder called .mozilla.  Your best bet is to copy and paste it, renaming it to something like .mozilla.backup.  If you don't want to un-hide the hidden folders, simply type in the command ```
cp -rf .mozilla .mozilla.backup
``` for the same results.

Then try running your new version of firefox.  If it wipes out your old stuff, then at least you have it backed up.  Chances are it will not erase your old stuff, but you can make a backup just to feel safe.[/COLOR]

---

### Post by original_jamingrit on 2009-08-05
I've just downloaded and installed firefox 3.5.2, and I can confirm that the new firefox will not lose your old bookmarks and history, but you can still back it up for posterity, or if you aren't sure you want to move to the new version yet.

To run the new version of firefox, close all open firefox windows, and in the folder you had extracted the new version of firefox to, run the "firefox" icon.

If you had just exploded the tar.bz2 file's contents all over your desktop, you can simply move them all into a folder and place that folder wherever you'd like.

Then also make sure to replace your old version's shortcut with a link to the new version in whatever folder you've placed it.

---

### Post by blake7 on 2009-08-05
thank you very much that was very cery simple

cant wait to cheak it all out

cheers mate and may the force be with you

---

### Post by philinux on 2009-08-05
No need to back up as firefox 3.5 uses a copy of your 3.0.12 profile to create its own. Then both browsers exist separately with the same bookmarks and addons etc. Afterwards if you add a bookmark in say 3.5 it does not get added to 3.0.12 and vice versa.

---

