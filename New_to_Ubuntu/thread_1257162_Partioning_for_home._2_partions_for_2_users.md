---
title: "Partioning for /home. 2 partions for 2 users?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by gpapagni on 2009-09-03
Hello, I just installed Ubuntu 9.04 last week and I am having a blast learning how to use it. Now I find out that /home should have it's own partition. My wife uses the computer also. Do I need 2 /home partitions, one for each of us? If so, how to do? Thanks. 
 
Geo

---

### Post by Grifulkin on 2009-09-03
No because all of your files are in
```
/home/<user>/
``` so if you have more than one user they would be as follows ```
/home/<user1>
/home/<user2>
```

---

### Post by gpapagni on 2009-09-03
Thanks, that makes it easier.

---

### Post by Grifulkin on 2009-09-03
> **gpapagni said:**
> Thanks, that makes it easier.

You are very welcome.

---

### Post by CatKiller on 2009-09-03
> **gpapagni said:**
> Now I find out that /home should have it's own partition.

*Should* is probably putting it a bit strongly. A number of users find it useful for ease of backup and when re-installing. It's not essential to do so by any means.

---

### Post by gpapagni on 2009-09-03
I am also dual booting with XP.  That should not create any problems with a /home partition, right?  Since I do not have much in my /home file as yet, I figure I should go ahead and do the /home partition.

---

### Post by CatKiller on 2009-09-03
> **gpapagni said:**
> I am also dual booting with XP.  That should not create any problems with a /home partition, right?

No problems at all. One thing to bear in mind is that you can only have four [Primary partitions]("http://en.wikipedia.org/wiki/Disk_partitioning#Primary"), but one of those can be an Extended partition. Any or all of your Linux filesystems can be in an Extended partition with no problem at all.

---

