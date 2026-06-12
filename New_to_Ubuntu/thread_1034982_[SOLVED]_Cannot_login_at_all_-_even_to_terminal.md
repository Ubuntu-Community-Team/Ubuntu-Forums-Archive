---
title: "[SOLVED] Cannot login at all - even to terminal"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by StoneMan353 on 2009-01-09
Hello All

I have a PC that has been running Ubuntu happily for years, (currently 8.10) that has just developed the most bizarre problem; I cannot log in. There are no error messages, it just kicks straight back to login prompt.

Computer boots up fine as always, displays gdm, I type my username/password, (also tried my wife's login) screen goes black for a second, then straight back to gdm.

Tried changing session to "Failsafe Terminal," thinking I had messed up xorg somehow, but same result.

Tried Ctrl>Alt>F2 but same behaviour, I type my login/password when prompted, and am immediately prompted for login: again.

If it helps the last things I remember doing before my reboot were making some changes to CUPS and applying an auto-update, which included some kernel headers. (hence the reboot)

This one's really got me stumped.
Any help would be greatly appreciated.

---

### Post by cmnorton on 2009-01-09
Boot with a recovery CD like the Ubuntu live CD or Knoppix, mount your hard-drive and look in your logs area /var/logs will be under a different path, because you want to see what went on recently after the upgrade.

---

### Post by Peter09 on 2009-01-09
This could be that your X server is configured incorrectly which would explain the black screen on attempting to log in. Have you tried recovery mode and xfix?

---

### Post by StoneMan353 on 2009-01-09
Thankyou for the replies.

I found a solution to my problem here:
[http://ubuntuforums.org/showthread.php?t=1030540](http://ubuntuforums.org/showthread.php?t=1030540)

Apparently a Samba-related problem.

---

