---
title: "[SOLVED] Unable to mount the volume 'Vista'."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-16
I am unable to open Vista Drive nor XP Drive from Ubuntu. When I try to open Vista Drive I get this error:
[[IMG]http://img408.imageshack.us/img408/1330/vistaerrorao2.th.png[/IMG]](http://img408.imageshack.us/my.php?image=vistaerrorao2.png)

---

### Post by albinootje on 2008-12-16
> **looi76 said:**
> I am unable to open Vista Drive nor XP Drive from Ubuntu. When I try to open Vista Drive I get this error:
[[IMG]http://img408.imageshack.us/img408/1330/vistaerrorao2.th.png[/IMG]](http://img408.imageshack.us/my.php?image=vistaerrorao2.png)

The possible solutions (and explanation why this happened) are in the error-message (Cool, isn't it ?). 
Try it!

---

### Post by caljohnsmith on 2008-12-16
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
Then try mounting Vista again. Let me know if that works or if you get the same or different error.

---

