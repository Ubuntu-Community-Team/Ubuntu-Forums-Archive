---
title: "software manager error"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by around_the_block on 2010-09-24
Hi, I'm trying to install a couple things, but I keep getting the massage: Only one software management tool is allowed to run at the same time.
 please close the other application e.g. 'Update Manager', aptitude', or Synaptic' first. 
 I went to System>Administration>System Monitor, but didn't see any of those running, or on the list. There is a 'Update Notifier', however. Am I looking in the wrong place? I'm trying to install a deb package on version 9. I've done this before, but without the interruption. Thanks for any help.

---

### Post by andrewthomas on 2010-09-24
You have another package manager open.  Just log out and back in.

---

### Post by around_the_block on 2010-09-24
Thanks, but I went to upper right corner, log out>log in, and I get the same message.:confused:

---

### Post by andrewthomas on 2010-09-24
Go to system > preferences > startup applications

and uncheck the update notifier. Then restart

---

### Post by around_the_block on 2010-09-24
Thanks again, but same thing. Actually, I accidentally -removed- the update notifier. I'll deal with that later.

---

### Post by around_the_block on 2010-09-25
I guess everybody comes up their own side of the mountain...I Googled: 
one software management tool ubuntu
and found some pages of info. I did this:
terminal>sudo dpkg --configure -a
got a message about the usb modem I had been trying to install, and stuff about c and kernel, all over my head. Closed terminal. Opened it again, 
killall dpkg
got a no process killed message. Tried Inkscape install anyway, it worked. It's a 386 deb package.

---

