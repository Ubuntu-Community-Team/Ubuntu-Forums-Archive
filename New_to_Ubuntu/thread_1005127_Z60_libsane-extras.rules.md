---
title: "Z60_libsane-extras.rules"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by expatCM on 2008-12-07
After a system update my scanner stopped working.  As the computer boots there is an error message to the effect of

udev_rules could not read Z60_libsane-extras.rules.  No such file or directory.

If I look at the file with nautilus (/etc/udev/rules.d/) I can see that the file exists but the file properties say 
Type: link (broken) (inode/symlink)
If I try to view the content I am prompted to move the file to the trash.

So for some reason the file got trashed on an update.  I guess the easiest way to fix this is to reinstall something.  Any suggestions of what something to reinstall?

---

### Post by expatCM on 2008-12-08
Just in case anyone is wondering why I do not simply reinstall libsane-extras ......  I did .... but no change.

---

### Post by dardar on 2008-12-19
I also saw this message and think it was the result of a broken symlink that happened during a software upgrade. 

Go to /etc/udev/rules.d (cd /etc/udev/rules.d in a terminal window) and see what file is symlinked to z60_libsane-extras.rules (use ls -al).  If it isn't 50-libsane-extras.rules, remove the existing symlink (sudo rm z60_libsane-extras.rules) and then recreate the symlink to the correct file (sudo ln -s 50-libsane-extras.rules z60_libsane-extras.rules).  

That should fix the broken link.

---

