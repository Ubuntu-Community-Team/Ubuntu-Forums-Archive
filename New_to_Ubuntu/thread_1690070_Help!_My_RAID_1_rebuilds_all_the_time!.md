---
title: "Help! My RAID 1 rebuilds all the time!"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by frotzed on 2011-02-17
I've got 10.10 installed on a RAID 1.  Everything seems to be working normally, but any time I make a change to anything (read: install a program, copy music, etc) disk management shows my RAID rebuilding.  Is this normal?  Shouldn't the new data be written to both drives in real time?

---

### Post by YesWeCan on 2011-02-17
That is not normal as you have described it. Once the initial synchronizing has finished, there should be no more until a disk is replaced.

A little more detail. What sort of RAID? There are hardware, fakeraid and software RAIDs.

Are you sure it has completed its initial sync? This can take hours.

How are you monitoring the sync progress?


This is a continuation of this thread, right?: [http://ubuntuforums.org/showthread.php?t=1688244](http://ubuntuforums.org/showthread.php?t=1688244)

---

### Post by frotzed on 2011-02-17
Yes it is a continuation.  Perhaps we should just close this one down and bring the conversation to one location.

---

### Post by YesWeCan on 2011-02-17
No problem. It's just better to keep things in one thread. Helps others to find answers more easily. I'll go back to the original thread.

---

