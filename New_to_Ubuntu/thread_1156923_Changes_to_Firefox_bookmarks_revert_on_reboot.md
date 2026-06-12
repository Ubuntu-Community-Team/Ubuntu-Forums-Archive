---
title: "Changes to Firefox bookmarks revert on reboot"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by VgnStirfry on 2009-05-12
Hi,

I upgraded to Ubuntu 9.04 (Jaunty) yesterday. w00t.   Now, my bookmarks in Firefox (3.0.10) can be edited, but when I reboot and open Firefox, I find that my changes have reverted.  anti-w00t.  I have not determined whether this occurs with any other aspects of my OS.  I do not know how to troubleshoot this. 

I would have taken this problem to forums.mozillazine.org, but since the problem seems to have started with the upgrade to Jaunty, I figured I would check here, first.  

An anticipatory "thank you"!

---

### Post by chrisod on 2009-05-12
It sounds like the main bookmarks file is corrupted. Click on *Bookmarks*, then *Organize Booksmarks* in Firefox. Then click on *import and backup* and restore from the backups presented there. Firefox automatically backs up your bookmarks.

---

### Post by VgnStirfry on 2009-05-12
**chrisod**: I am concerned that restoring a version that was saved before I upgraded may cause problems: I upgraded from 8.04 to 8.10 and from 8.10 to 9.04 in the same day.  Also, I would prefer not to lose any more; the version to which I would have to revert would result in a loss of those I saved before this issue occurred.  Thank you, though.

Any other ideas, chrisod, anyone?

---

### Post by chrisod on 2009-05-12
Firemarks bookmarks are just an html file - I can't think of anything about upgrading that would affect the bookmarks file. Usually when it gets corrupted it is caused by a Firefox crash. Anyway, just being HTML files you find them in your .mozilla folder and open then in Firefox to check before doing the restore.

---

