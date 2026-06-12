---
title: "Boot Issue:  Missing init"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Ebonhawke on 2011-05-03
Good morning,

Linux novice here - Last night, my computer crashed, and when I did a cold boot, I got the following message (think there was a line above the first one, but scrolled by too quick)

[I]mount: mounting /proc on /root/proc failed:  No such file or directory.

Target filesystem doesnt' have /sbin/init

No init found.  Try passing init=bootarg.
[/I]
Suggestions?

---

### Post by Ebonhawke on 2011-05-03
After it shows this message, it takes me to 'initramfs' prompt

---

### Post by Ebonhawke on 2011-05-03
OK - resolved the issue, found the help from

[http://ubuntuforums.org/showthread.php?t=1200023](http://ubuntuforums.org/showthread.php?t=1200023)

*sudo fsck - y /dev/sda1 - then reboot*

Google is your friend :)

---

