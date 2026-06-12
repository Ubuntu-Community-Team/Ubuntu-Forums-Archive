---
title: "Routine drive check"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by raynard on 2008-12-17
Every 30 times I boot up my laptop, it does a routine drive check, which seems normal.
The first few times it did this check, there were no non-contiguous files, but this number has been growing to 2,4% now.
Is this anything to worry about, because I thought ubuntu didn't need to be defraged?

---

### Post by rlunger on 2008-12-17
> **raynard said:**
> Every 30 times I boot up my laptop, it does a routine drive check, which seems normal.
The first few times it did this check, there were no non-contiguous files, but this number has been growing to 2,4% now.
Is this anything to worry about, because I thought ubuntu didn't need to be defraged?

Shouldn't be a problem.  This can happen if you don't have a lot of free space for larger files, or if you have files that are appended to but not totally rewritten (database files, log files, etc..).  I wouldn't worry about 2.4% and I certainly wouldn't worry about defragging unless you run into some performance issues.

---

### Post by raynard on 2008-12-17
I thought it was quite strange, because I've just got a new harddrive of 500 gb and only 200gb of it is written.

---

### Post by drs305 on 2008-12-17
Do you have it divided into many partitions instead of one large one? The fsck check inspects each partition individually. Even so, 4% is nothing to worry about.

30 mounts is the default fsck checking point. You can change the number of mounts or select number of days via tune2fs ( -i and -c options ) if you want the partitions checked more or less often.

---

### Post by raynard on 2008-12-17
> **drs305 said:**
> Do you have it divided into many partitions instead of one large one? The fsck check inspects each partition individually. Even so, 4% is nothing to worry about.

30 mounts is the default fsck checking point. You can change the number of mounts or select number of days via tune2fs ( -i and -c options ) if you want the partitions checked more or less often.

Yes, I've got 3 partitions: one for windows, one for ubuntu and one for the swap space.  I guess that will be the cause.

Anyway, thanks for your help, all of ya! :-)

---

