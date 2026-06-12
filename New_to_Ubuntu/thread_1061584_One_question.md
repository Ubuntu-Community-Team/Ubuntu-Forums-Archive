---
title: "One question"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by POWMS on 2009-02-05
I've downloaded all the updates (the system tells me it is up-to-date) which includes the kernel 2.6.24-23. And my panels are gone. I'm leaving them tuned off for the moment as my system hangs when they are turned on. Anyway I digress.......
My Xubuntu is a Wubi install, so I've downloaded the lvpm.deb file for installation as I want to create a hardrive partition(s) for permanent installation.
However, as soon as the package installer appears on the desktop the system hangs again, catch 22.
I am stumped as to why the system keeps hanging when I try to do anything in the desktop.
Is there a check I can do in terminal to see an error log of what is going wrong in the desktop (aka Windows Event Viewer)?
Thanks.

---

### Post by lisati on 2009-02-05
Please stand by - searching for a previous thread on the panels on Xubuntu desktop

EDIT: other things are demanding my attention at the moment, but from memory (I'm on a vista machine at the moment) one possibl solution involves right-clicking on one of the desktop icons (can't remember which), choosing "open terminal here", and entering 
```
sudo xfce4-panel &
```
You might want to check out [http://ubuntuforums.org/showthread.php?t=1056013&highlight=panel]("http://ubuntuforums.org/showthread.php?t=1056013&highlight=panel")
Anyone else?

EDIT 2: I think I misunderstood the question.... Anyone else?

---

### Post by POWMS on 2009-02-08
Well, I ended up formatting the harddrive and installing Xubuntu Intrepid. This seems to have solved all my issues. I'm not sure if it was the right course of action, but I ran out of options.
I also made a point of installing it on a partitioned harddrive, not thru Wubi.
All is working well, and as I want it too.
I also reported the bug (see my bug report thread).

---

### Post by ptn107 on 2009-02-08
Don't use wubi if you can avoid it.

---

