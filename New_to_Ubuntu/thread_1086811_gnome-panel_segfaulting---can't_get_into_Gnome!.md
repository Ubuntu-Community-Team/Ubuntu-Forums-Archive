---
title: "gnome-panel segfaulting---can't get into Gnome!"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Angus77 on 2009-03-04
I get the Gnome login screen, but when I actually log in, I get the wallpaper and the mouse cursor doing the loading animation---and then it just hangs.

I moved to a virtual terminal and checked out dmesg, and it gave me this

```

...*[interminal lines like the following]*...
[   125.719354] gnome-panel[5926]: segfault at e45be6ff ip b74e7d88 sp bfc08efc error 5 in libc-2.8.90.so[b7471000+158000]
[   126.166926] gnome-panel[5927]: segfault at e45be6ff ip b7523d88 sp bfa445cc error 5 in libc-2.8.90.so[b74ad000+158000]
[   125.586417] gnome-panel[5928]: segfault at e45546ff ip b774dd88 sp bf89e42c error 5 in libc-2.8.90.so[b7407000+158000]
...[I][and on and on and on and on][I]...

```

I tried removing and reinstalling gnome-terminal, but it didn't change.

Google's not helping me.

I'm running 32-bit Intrepid on an EeePc 901 (Atom).  I use custom kernels from [array.org]("http://array.org"), but I still have the regular kernel around---booting up with it doesn't help.

---

### Post by cubeist on 2009-03-04
There must be an applet/plugin on the panel which is trying to access libc-2.8.90 and it is faulting out... So a couple solutions I can think of... try to remove the offending plugin/applet on the panel (trial and error),  or boot into a safe session and disable the gnome panel with a command like
```
gnome-session-remove gnome-panel
```
or, try removing the offending libc-2.8.90...

---

### Post by Angus77 on 2009-03-04
Apparently gnome-session-remove doesn't exist in Intrepid (there's a bug filed).

I tried installing a different version of libc6 (downgraded from 2.8~20080505-0ubuntu9 to 2.8~20080505-0ubuntu7), but I'm getting exactly the same problem.

GAH!  I've had Intrepid running smoothly since the day it was released.  What on Earth could cause something like this?!

---

### Post by Angus77 on 2009-03-04
I've given up!  I need to use my computer at work, so I just reinstalled Intrepid.

Frustrating!

---

### Post by cubeist on 2009-03-05
that really sucks, I wonder which applet caused it to junk out, it would be nice to know to file a bug report.

If it is any consolation, gnome-panel has caused serious problems for me in the past...never had to reinstall though.

Anyway, a great alternative is to use gnome-do with docky...
[[COLOR="Red"]http://do.davebsd.com/[/COLOR]]("http://do.davebsd.com/")

---

### Post by Angus77 on 2009-03-05
Thanks!  It looks nifty.  I'm gonna download it and give it a shot.

---

