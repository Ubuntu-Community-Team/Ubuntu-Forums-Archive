---
title: "flux box desktop stuck on nautilus"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-06-18
hi
maybe this shouldn`t be in the absolute beginner section but for this question I feel like an absolute beginner so...
my laptop was grinding to a halt even with xubuntu so I tried fluxbox
I tried to find my home folder and eventually found it by opening nautilus
trouble is now my ubuntu/ xubuntu desktop is stuck in fluxbox and I have lost the right click menu
i.e. I am basically stuck with my opera open and thats about it
how do I close nautilus in fluxbox?

---

### Post by Sealbhach on 2009-06-18
You could open up another screen, by using Ctrl+Alt+F1 or F2 . Log in there and then issue

killall nautilus

This should stop Nautilus. To get back to your other screen do Ctrl+Alt + F1 or keep trying all the F buttons till you find your original tty screen.

Also, try PCManFM instead of Nautilus as a file manager.


.

---

### Post by kukibird1 on 2009-06-18
> **Duke Togo said:**
> hi
maybe this shouldn`t be in the absolute beginner section but for this question I feel like an absolute beginner so...
my laptop was grinding to a halt even with xubuntu so I tried fluxbox
I tried to find my home folder and eventually found it by opening nautilus
trouble is now my ubuntu/ xubuntu desktop is stuck in fluxbox and I have lost the right click menu
i.e. I am basically stuck with my opera open and thats about it
how do I close nautilus in fluxbox?

Nautilus has the bad habit of bringing the xfce/gnome desktop with it if you don't use nautilus --no-desktop option in fluxbox.

If you run gconf-editor  and go to apps > nautilus > preferences and untick show_desktop  nautilus will not take over. You will have to click on the desktop folder in the file manager to access anything you had on the desktop.

---

