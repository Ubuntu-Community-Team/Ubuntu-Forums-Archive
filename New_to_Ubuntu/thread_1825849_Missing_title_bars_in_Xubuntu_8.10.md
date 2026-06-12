---
title: "Missing title bars in Xubuntu 8.10"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by kampion998 on 2011-08-15
I just lost the titlebar, I can not move windows, and i can not use drop-down combo boxes.  I tried control-alt-backspace, xfwm4, xfwm4-panel, xfwm4 & , plus startx. etc.  this is the latest version of xubuntu.  I need this fixed as my income depends on my computer working!

HELP!

---

### Post by overdrank on 2011-08-15
Hi and welcome, I have moved your post to it's own thread. No need to revive a 2 year old thread. 
8.10 has reached End of Life on support.

 Are you still using 8.10?

---

### Post by Toz on 2011-08-15
Can't remember the specifics of xubuntu 8.10, but have you tried Alt+F2 then executing the following command:
```
xfwm4 --display=:0.0 --replace
```

This is the general fix for the missing titlebars problem.

---

### Post by newb85 on 2012-06-11
Thanks, Toz!  Fixed the problem for me in 11.10.

---

### Post by newb85 on 2012-06-11
Rats, I spoke too soon.  This worked, but only until the next time I logged in.

---

### Post by Toz on 2012-06-11
Try clearing out your cache (sometimes the saved sessions cache gets corrupted). You can do this by deleting the **~/.cache/sessions** folder.

If the problem still persists, then logout, Ctrl+F1 to go to the first tty, log in via text mode, and then delete the directory:
```
rm -rf ~/.cache/sessions
```
...then Ctrl+F7 to get back to the graphical screen.

---

