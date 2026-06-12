---
title: "Is there a backup/sync solution"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Kedster on 2009-10-22
I wish to have a program sync my home folder with a backup home folder on a a windows computer on the same local network.

If possible I would like to have it be sceduled to sync every day or every week at like 1 am.

I would like it to be able to sync my whole "home" folder wich is on its own partition






Ps. on a side note does anyone know any tricks to get a physically damaged drive to work just to get like 2 small file (like 2 mb)

---

### Post by laffinet on 2009-10-22
Have a look at rsync, which should do just that.

Also check cron, to schedule backing up at certain times/days.

Lots of stuff on these forums about both topics, just a few below:

[Cron]("http://ubuntuforums.org/showthread.php?t=102626&highlight=rsync+backup")
[rsync 1]("http://ubuntuforums.org/showthread.php?t=639979&highlight=rsync+backup")
[rsync 2]("http://ubuntuforums.org/showthread.php?t=1289062&highlight=backup+rsync")
[rsync 3]("http://www.mikerubel.org/computers/rsync_snapshots/")

That should get you started.

---

### Post by Psyphre on 2009-10-22
I'd recommend Conduit, I find it so much easier to use than rsync.
I think you can even have it constantly monitor for changes.

---

### Post by aaronchall on 2009-10-22
> **Kedster said:**
>  Ps. on a side note does anyone know any tricks to get a physically damaged drive to work just to get like 2 small file (like 2 mb)

The freezer trick has been known to get a hard drive working long enough to get some data off of it, but otherwise, you may have to send it to a specialist who may charge hundreds to do it.  

[http://www.trap17.com/index.php/Hard-Drive-Freezer-Trick_t26193.html](http://www.trap17.com/index.php/Hard-Drive-Freezer-Trick_t26193.html)

Just search for "hard drive" and "freezer trick" for more info...

---

### Post by powel212 on 2009-10-22
I use back in time to backup all the documents on my office server. It could be configured to backup to a remote location and shared.

[http://backintime.le-web.org/](http://backintime.le-web.org/)

I also use Ubuntu One to backup my home folder. which is shared between my work and home Ubuntu systems. You may also be able to use it so sync between Linix and windows. I think it isn't available for windows yet but they may be working on that. I am just guessing on that last bit. 

Dropbox may also be a reasonable solution.

I hope that helps.

Powel

---

### Post by winotree on 2009-10-22
I'll have to say *rsync* and its GUI *grsync. * You might also consider *sbackup* also called Simple Backup Suite, all of which are in the repositories.  I use both [for different purposes and reasons].  ;)

---

