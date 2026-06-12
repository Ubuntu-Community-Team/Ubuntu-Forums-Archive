---
title: "Can we have home folder spread across 3 partitions"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by rohit raj on 2010-08-01
I was planning to dual boot windows xp with kubuntu 9.10. I was able to install kubuntu 9.10 and have been love with it since it then. But the problem is that windows xp failed to install properly. Net is not working and audio also does not works. So can i reinstall kubuntu to use those 2 useless partitions also as home folder

---

### Post by oldfred on 2010-08-02
Why not repartition? There is a LVPM that allows what you are asking and some like it but I do not use it. If you ever have problems in one partition, it breaks the entire thing.

I suggest separate /home and/or a separate /data. I moved all my data folders out of /home and now /home is only about 1GB with only the user settings in hidden files & folders. /data of course is much larger as it has all my data.

---

### Post by orethrius on 2010-08-02
> **oldfred said:**
> Why not repartition? There is a LVPM that allows what you are asking and some like it but I do not use it. If you ever have problems in one partition, it breaks the entire thing.

Seconded, for the same reasons.

> **oldfred said:**
> I suggest separate /home and/or a separate /data. I moved all my data folders out of /home and now /home is only about 1GB with only the user settings in hidden files & folders. /data of course is much larger as it has all my data.

That's actually not a bad idea.  Following that logic, I'm in the process of moving my files to a separate partition on a separate drive (okay, I'm paranoid, but at least that one dangerous command would only wipe out my per-user settings...) :)

---

