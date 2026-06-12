---
title: "Trouble backing up /home"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by tim1970 on 2009-10-05
I am attempting to back up my /home partition.  Since it is ext4 I am not able to use partimage, so I am using rsync.  I boot up with a live cd, then mount both my /home partition and my archive partition.  I run the following command: rsync -avS <source> <destination>

The problem is my /home partition shows about 200 mb worth of data, and my archive partition only shows about 55 mb of data once it is finished.

This is a new install of Ubuntu 9.04.  The only things I have done since install is add 3 users, and do some surfing.  No personal files.  So I can't figure out why my /home is showing 200mb.  I have tried to search for files that large, and can't find anything.

Any suggestions?  How much data should be in my /home after a clean install?

Tim

---

### Post by louieb on 2009-10-05
Where are you getting that number from?
Probably the 200+ mb used includes reserved disk space
what does ```
df -h
``` show

---

### Post by lavinog on 2009-10-06
try this:
```

du -xh --max-depth 1 /home
du -xh --max-depth 1 /archive

```
the -x means to stay on one filesystem.
without it, du will include the size of any drive mounted with gvfs or samba shares.

although rsync will also try and archive the same mounted drives, so when you use rsync to backup, you may want to use the -x switch too.

---

