---
title: "messed with X or GDM, now I am stuck"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-04-20
Hi everyone.
I wanted to know how to do manage all this X stuff, but now when I turn on the computer I am just stuck on my wallpaper without anything.
Does someone know how to fix it?

---

### Post by cavh on 2011-04-20
CTRL-ALT-F1, then log in as usual and then type ```
startx 
```at the prompt and see where that gets you.

---

### Post by Avidanborisov on 2011-04-20
> **cavh said:**
> CTRL-ALT-F1, then log in as usual and then type ```
startx 
```at the prompt and see where that gets you.

CTRL+ALT+F1 didn't work, but CTRL+ALT+F2.
I logged in to tty2 as my user and then switched to root by sudo -s but when I typed startx I got the login screen again with the wallpaper without and the login sound without anything else.
Then i also tried CTRL+ALT+F3 and this time I wrote service gdm restart. The same issue again.
Also I have noticed that if I just press the shutdown button on my computer, I get the shutdown dialog but without any borders and quickly refreshing. So, I think I got problem with the windows manager, in my system its compiz.

Any ideas? I would just like to somehow restore it to the default settings.

---

### Post by cavh on 2011-04-20
I'd suggest disabling Compiz when logged in at a tty, but to be honest have no idea what command you need to do that.

---

