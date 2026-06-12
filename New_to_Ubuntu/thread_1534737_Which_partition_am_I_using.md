---
title: "Which partition am I using?"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Grock1722 on 2010-07-20
Hello all-

Apparently at some point in my ubuntu career I installed ubuntu on a second partition on my main hard drive.  

At this point, I appear to have three partitions and two swaps, one partition for windows, and two with ubuntu on them.  I want to delete the extra partition and its swap to re-utilize the space it's taking up.  

If it helps at all, I think I installed/made a new partition for ubuntu when I had an upgrade error.  

Anyway, the ubuntu disk utility shows these partitions, and says that I can edit/delete them... but I don't know which one of my ubuntu partitions is the one with my OS on it.  Is there a way to figure this out?

Thanks for all the help,
G

---

### Post by bodhi.zazen on 2010-07-20
Open a terminal and enter ```
mount
```

---

### Post by Linux000 on 2010-07-20
In terminal type "df"(no quotes) and there should be a line that ends with Mounted on... / the other end of that row(/dev/sd**)will be the partition the you are using on that OS. Hope it helps.

---

