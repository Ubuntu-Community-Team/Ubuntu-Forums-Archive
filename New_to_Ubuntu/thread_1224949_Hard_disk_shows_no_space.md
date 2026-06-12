---
title: "Hard disk shows no space"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by MelDJ on 2009-07-28
Recently, I installed ubuntu 8.04 to my 40Gb hard disk through wubi. Setup went like normal. I then updated ubuntu. After restarting the computer, i saw that there was only 2Gb of space left. I had allocated only 7Gb for ubuntu, i kept only 1Gb of music and nothing else. Everytime I logged into Ubuntu, the space just kept decreasing until 1 day it showed that the GDM could not write its log as there was no more space. I then formatted the disk and reinstalled Ubuntu the same way as before.  This time I did not update it and it works fine. Is there a proble mwith updating?? I am really confused:confused:

---

### Post by jenkinbr on 2009-07-28
Updateing will put a bunch of package files in a cache directory.

You can always run **sudo apt-get clean** in a terminal to clear them out and free the space.

---

### Post by MelDJ on 2009-07-28
thanks for replying. I did try sudo apt-get clean. I even deleted the orphaned and installed package in synaptic. but the problem persisted!:(

---

### Post by mapes12 on 2009-07-28
Not sure if this is the problem you have encountered but an excellent guide why HDD's fill up for no apparent reason:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by MelDJ on 2009-07-28
Great! thanks everyone for helping! :KS

---

### Post by drs305 on 2009-07-28
> **mapes12 said:**
> Not sure if this is the problem you have encountered but an excellent guide why HDD's fill up for no apparent reason:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

I actually wrote a follow-on guide. The one above covers undeleted trash, this one covers lost 'free space' in general.
[Disk Space Problems & Solutions]("http://ubuntuforums.org/showthread.php?t=1122670")

Trash is one of the problems. The other two common problems are large log files in /var/log and backups that end up on the system partition instead of on backup drives or partitions.

---

### Post by MelDJ on 2009-07-28
but why does this not happen if i don't update? and how can 30++ GB b used up?:confused:

---

### Post by drs305 on 2009-07-28
> **MelDJ said:**
> but why does this not happen if i don't update? and how can 30++ GB b used up?:confused:

Do you do backups? Have you deleted very large files? These things can take up disk space even if you don't download any new applications. 7GB is above the minimum size required but won't give you a lot of extra space so you will have to monitor your file (wubi) space.

It would be best for you to go through the guide I linked, but if you post the results of these commands we can perhaps find out where this space is being taken up:

```

df -h
sudo du -h --max-depth=1 / 
sudo find / -name '*' -size +500M 

```

If /media is very large, unmount all non-system partitions and run the commands again:
```

sudo umount -a  # Disregard "busy" messages, they are ok.

```

---

### Post by MelDJ on 2009-07-28
sorry but i have already reinstalled ubuntu....:(
thanks for your help anyway [drs305]("http://ubuntuforums.org/member.php?u=223945")

---

