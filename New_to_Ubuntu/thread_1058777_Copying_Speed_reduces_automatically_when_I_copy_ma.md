---
title: "Copying Speed reduces automatically when I copy many files"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-03
Hi
Thank you for reading my post.
I have a very un-normal problem. Imagine that I have a 8GB flash disk. If I copy one single Film (750MB) it copy the file as fast as 6.5MB/Second.
If I try to copy 5 of those files, the copying speed start at 6.5 and reduces constantly. even it reduce down to 1mb/second.

Sometimes it happens when I copy a big file between my partitions. (I have two SATA2 hard disksand I am sure that they are fast because they are fast in windows.)

System spec:

Ubuntu 8.10 (8.4 which updated automatically)
CPU: Intel 3Ghz HT
RAM: 2Gig
HDD: Maxtor and Samsung (320 and 250), both are SATA2 (32meg buffer)


Please let me know how I can hunt the possible problem.

---

### Post by legolas_w on 2009-02-03
Any comment?

Thanks.

---

### Post by HavocXphere on 2009-02-03
Some of the cheaper flash sticks have a combination of fast memory & slow memory in them. Not sure what the logic behind that is...

Copying a single file is not an accurate measure since you have on disk caching and delayed writes that distort everything.

btw...why the "**Imagine** that I have a 8GB flash disk". Do you have this hypothetical fash or not?

On a Hdd, fragmentation could also distort the result...on a flash not so much.

Not much you can do about it.

---

### Post by annda on 2009-02-03
this is unfortunately a common problem, and many bug reports have been filed, e.g. [https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)

there seems to be a **temporary** fix available:
[http://ubuntuforums.org/showthread.php?t=911052](http://ubuntuforums.org/showthread.php?t=911052)

i haven't tracked all the update details so i can't pinpoint exactly what the culprit is, but since ca. gutsy i get either decent or miserable transfer speeds after major upgrades.

check out the "pci=routeirq" solution from the above thread, it may work for you.

---

