---
title: "hard drive ??"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by jbalazs on 2009-11-10
I have a HP laptop with a Samsung HM250J1 hard drive, running ubuntu 9.10 but it's telling me that I have many bad sectors on my hard drive.
Is there a fix for this or I have to replace my hard drive ??

[IMG]http://i5.photobucket.com/albums/y176/foxhunter2/Screenshot-1.png[/IMG]

---

### Post by mr_steve on 2009-11-10
This could very well mean that your hard drive is on the verge of failing. Previous versions of Ubuntu didn't have the utility to discover that information.

There have been a few cases of false bad sector reports on Samsung drives, but I would strongly suggest that you start backing up your files *now*.

---

### Post by marcopolo1981 on 2009-11-10
I'm no epert at these types of things, but if I were you, I would definately start by un-ticking the 
"Don't warn me if the disk is failing"!!

Bad sectors can usually be repaired without to much hard work.(But not always)
It might be helpful if you let us know what file-system you are using. Ext2/3/4/reiser...

---

### Post by jbalazs on 2009-11-10
Using file type ext4

Thanks

---

### Post by alphaniner on 2009-11-10
Please post a screenshot where the failing attribute is shown in the 'Attributes' box.

---

### Post by Paqman on 2009-11-10
First and foremost: go to Sytem > Admin > Update Manager, update your sources and install any updates that are available.

The version of gnome-disk-utility that was in earlier versions of Karmic did have a bug that caused it to incorrectly report drives with a few reallocated sectors as failing. A handful of correctly reallocated sectors is fine. Lots of them, or unreallocated sectors is bad. AFAIK, the release version of Karmic shipped with this bug fixed, but without knowing when in the cycle you installed it's impossible to rule out a false-positive.

So install all the updates, then check to see if the disk utility is still flagging the drive as bad. If it is, *immediately* back up your data and start looking for a replacement drive.

---

### Post by jbalazs on 2009-11-10
[IMG]http://i5.photobucket.com/albums/y176/foxhunter2/Screenshot-1-1.png[/IMG]

---

### Post by alphaniner on 2009-11-10
That looks like a legitimate error and not a result of the bug.  I suggest backup immediately, and make preparations to replace.  You could also look into [Samsung's drive test tool]("http://www.samsung.com/global/business/hdd/support/utilities/Support_HUTIL.html") for a second opinion.

---

