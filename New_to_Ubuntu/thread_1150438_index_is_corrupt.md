---
title: "index is corrupt"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by esedizzle on 2009-05-06
I recently upgraded to ubuntu 9.04 and during the standard indexing it said the index is corrupt. What does this mean and what do I do?

---

### Post by meindian523 on 2009-05-06
That is a known bug and being worked on.Wait for an update to correct the problem.In the meantime,disable Tracker.

---

### Post by mprince on 2009-05-06
I think this is a bug.

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

---

### Post by meindian523 on 2009-05-06
Yes,it's a bug.Original bug no: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205)
**F**rom Jaunty release notes:
> 
**Tracker index corruption**

  In some cases it can happen that the index of the "tracker" desktop search engine becomes invalid. A dialog will be shown, offering you to "Reindex all contents". This button does not work, and the tracker service might start to use large amounts of CPU and disk resources. As a workaround, please press Alt+F2 and run tracker-processes -r. This will be fixed in a post-release update soon

---

