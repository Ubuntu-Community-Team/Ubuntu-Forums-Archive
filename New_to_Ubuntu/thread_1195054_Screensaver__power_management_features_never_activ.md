---
title: "Screensaver / power management features never activate"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Lexyboy on 2009-06-23
Recently I replaced gnome-screensaver with xscreensaver as per [this thread]("http://ubuntuforums.org/showthread.php?t=195557").  Now the screensaver never starts, nor does the screen blank as set with the Power Management prefs.

It seems that there's something preventing the system from noticing that it's idle, as if I enter```
$ xscreensaver-command -activate
```
then the screensaver runs fine.

Strangely, Pidgin seems to notice when I'm not there and changes my status, but I'm guessing it uses a different method to check.  I'm using Jaunty on a Dell laptop with touchpad if that helps.

---

