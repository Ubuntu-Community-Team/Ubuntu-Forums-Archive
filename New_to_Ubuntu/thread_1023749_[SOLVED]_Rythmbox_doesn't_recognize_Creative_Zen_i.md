---
title: "[SOLVED] Rythmbox doesn't recognize Creative Zen in Intrepid"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jma79 on 2008-12-28
Previously I was using Gutsy and my Zen Microphoto was detected normally by Rythmbox. It was possible to move files, delete them, etc.
Recently I installed the Intrepid release and the Rythmbox doesn't detect the player anymore. It only is detected by the system if i put it in data storage mode.

I came across with a few ways to deal with this:

- using gnomad2

or solve a bug according to these links

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg236667.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg236667.html)
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/291810](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/291810)
[http://svn.gnome.org/viewvc/rhythmbox?view=revision&revision=5992](http://svn.gnome.org/viewvc/rhythmbox?view=revision&revision=5992)

Since I am new to this, i'm not quite sure of what to do.
What should i do to have rythmbox working as before?
Thx in advance

---

### Post by BDNiner on 2008-12-28
If you want to attempt to patch Rhythmbox then you can follow the instructions directions on the launchpad site. Otherwise it seems like the fix has already been proposed and an update should be avaliable soon that will correct the problem.

Otherwise you can use Gnomad2.

---

### Post by appi2012 on 2008-12-28
You could try syncing with the software mentioned in this post:
[http://ubuntuforums.org/showthread.php?t=216191](http://ubuntuforums.org/showthread.php?t=216191)

---

### Post by jma79 on 2008-12-28
After searching another thread i found out that the mtp device plugin in rythmbox was disabled. :oops:
Now it's all up and running.
Thx for your help.

---

