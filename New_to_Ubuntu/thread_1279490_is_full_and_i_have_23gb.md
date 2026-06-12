---
title: "/ is full and i have 23gb"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Peacefulpieofdeath on 2009-09-30
Ok iv installed this version not to long ago, i dont have a million apps on my computer but / partition is full.

df -h
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23G   23G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  204K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  164K 1006M   1% /dev
tmpfs                1007M   76K 1006M   1% /dev/shm
lrm                  1007M  2.2M 1004M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda6              46G   10G   34G  23% /home
overflow              1.0M   12K 1012K   2% /tmp
/dev/sdb1             765G  193G  573G  26% /media/disk-1
/dev/sdb2             155G   40G  115G  26% /media/disk-2
Is there somthing i can do, thanks in advance.

---

### Post by aktiwers on 2009-09-30
```
sudo apt-get autoremove
```
```
sudo apt-get autclean
```

Or check out this post:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

You don't have big files on your Desktop or in your home folder?

---

### Post by Peacefulpieofdeath on 2009-09-30
This did nothing, and yes i did add the o in autoclean...

---

### Post by louieb on 2009-09-30
Chenk out - [How to recover lost disk space]("http://ubuntuforums.org/showthread.php?t=1122670")
and [Check your trash]("http://ubuntuforums.org/showthread.php?t=898573")

Are you using sbackup? It defaults to storing in the root folder IIRC.

---

### Post by wdzieczny on 2009-09-30
Check your log files. You might be overloaded with them.

---

### Post by blackened on 2009-10-01
Instead of guessing where all your space is being used, you should fire up Applications -> Accessories -> Disk Usage Analyzer and do a scan of /.

It will output a navigable hierarchical representation of the filesystem that you can use to figure out the issue.

---

### Post by Peacefulpieofdeath on 2009-10-01
I found the reason, thanks guys..

it was simple backup that was sending backups to /media/disk where i wanted it to be, but my external harddrive had moved to /media/disk-1.... so it was saving to root.

Thanks anyway.

---

### Post by LewRockwell on 2009-10-01
thank you for following up with your discovery and resolution!

.

---

