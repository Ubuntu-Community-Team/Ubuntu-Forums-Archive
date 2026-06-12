---
title: "Firefox crash"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by beachcomber_1 on 2008-12-21
After Firefox update, Firefox sometimes loads to screen then flashes black and shuts down. Has anyone experienced this ? Know of fix.

---

### Post by Maharshi on 2008-12-21
happens sometime ..but after works good..

---

### Post by skern03 on 2008-12-22
I am running firefox 3.0.5 on Unbuntu 8.04 (couldn't get 8.10 to install). It crashes frequently, even in the middle of posting to this forum! Fortunately, when I restart and choose Restore previous session, I don't lose that much if any text.

Still searching for a reason or a fix. I used to run an earlier version of Firefox (2), and may switch back to see if that helps.

> **beachcomber_1 said:**
> After Firefox update, Firefox sometimes loads to screen then flashes black and shuts down. Has anyone experienced this ? Know of fix.

---

### Post by skern03 on 2008-12-22
In this thread there's a link to a post that is supposed to fix the problem. I just applied it - basically, it's a reinstall of firefox - and am anxious to see if it works. (Thanks skeetre)

[http://ubuntuforums.org/showthread.php?t=1014747&highlight=firefox+crash](http://ubuntuforums.org/showthread.php?t=1014747&highlight=firefox+crash)

Here's what the fix is supposed to be. In a terminal, enter these three lines in succession:
sudo killall -9 -r firefox
sudo apt-get purge firefox firefox-3.0 ubufox
sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support



> **beachcomber_1 said:**
> After Firefox update, Firefox sometimes loads to screen then flashes black and shuts down. Has anyone experienced this ? Know of fix.

---

### Post by pjman on 2008-12-22
> **skern03 said:**
> In this thread there's a link to a post that is supposed to fix the problem. I just applied it - basically, it's a reinstall of firefox - and am anxious to see if it works. (Thanks skeetre)

[http://ubuntuforums.org/showthread.php?t=1014747&highlight=firefox+crash](http://ubuntuforums.org/showthread.php?t=1014747&highlight=firefox+crash)

Here's what the fix is supposed to be. In a terminal, enter these three lines in succession:
sudo killall -9 -r firefox
sudo apt-get purge firefox firefox-3.0 ubufox
sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support

This seems to have fixed the problem for me. Thanks!

---

