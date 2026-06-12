---
title: "Out of Disk Space on Linux partition   ????"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2011-01-09
After resizing my original linux partition in preparation to create a separate /home folder-partition I have encountered an Out of Space problem.

Cannot do things like log onto my wife's account, select applications, save text files, etc.

GParted shows the original partition to have no unused memory. It is 59gig and shows 59gig in the used column. Funny thing is that it shows 44 gig in the unused column. Normally used and available columns equals total size. ????

I am in the process of finishing the /home folder move to it's own partition but I need to get around this memory issue. I can delete data files off the original Linux partition but no additional space is created. ????

HELP!!!!!!

Ed

---

### Post by mikewhatever on 2011-01-10
Checking that partition's file system might help. Use Gparted from the live cd to do that. If you have a backup of the files, deleting the problematic partition is also an option.

---

### Post by ozark_hillbilly on 2011-01-10
If I delete that partition do I start all over with the Live CD? I would rather avoid that if at all possible.

---

### Post by Daniel0108 on 2011-01-10
> **ozark_hillbilly said:**
> If I delete that partition do I start all over with the Live CD? I would rather avoid that if at all possible.

That's why mikewhatever told you to make a backup before deleting it...
If you try to resize your partition you could use your data too! I really recommend a backup :D Then try to repair your partition.
You could also backup the whole hard-drive, then format the partition to ext4 and copy all in again ;)

I hope this helped you,
Yours,
Daniel

---

