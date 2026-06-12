---
title: "login issue"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by ryan! on 2010-07-09
I get to the login screen and enter my password. Then the screen goes black for a couple of seconds and goes back to the login screen. 

Update: I tried removing and reinstalling xserver-xorg but that didn't help

---

### Post by Muscovy on 2010-07-09
This happened to me a few months ago with the 10.04 Beta2. I never solved it, and just reinstalled that partition.

Perhaps logging into an XTerm session (it's an option at the bottom if you click your name) and running startx, then a graphical application like gedit or firefox. If it fails, try running the failed command like this:
> command that fails > ~/crash_log
And it will write whatever happens into the file crash_log.

---

### Post by ryan! on 2010-07-09
i'll just reinstall then

---

