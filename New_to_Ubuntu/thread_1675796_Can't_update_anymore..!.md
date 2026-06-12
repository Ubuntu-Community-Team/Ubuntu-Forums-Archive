---
title: "Can't update anymore..?!"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by kramer65 on 2011-01-26
Hello,


I've been using Ubuntu for a couple years now, and I love it. The thing I love the most is that it has the ability to update all programs including Ubuntu itself automatically without bothering me. Recentely however, it suddenly gave some kind of error saying that updating failed. I now tried to update manually, but I get the following error:

```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: _cache->open() failed, please report.
```

Does anybody have any idea about what I can do about this..?

---

### Post by realzippy on 2011-01-26
Synaptic or SoftwareCenter running while manually updating?

---

### Post by kellemes on 2011-01-26
If you know there is no process using apt at the moment.. the lockfile hasn't been removed for some reason..
You may try the following to delete the lockfile..

```
sudo rm /var/lib/dpkg/lock
```

Now try again..

---

### Post by kramer65 on 2011-01-26
I didn't have the software center or synaptic running so that wqasn't it. So I tried to remove the lockfile and that indeed worked like a charm. I thing all functions well again now.

Thanks a lot!

---

