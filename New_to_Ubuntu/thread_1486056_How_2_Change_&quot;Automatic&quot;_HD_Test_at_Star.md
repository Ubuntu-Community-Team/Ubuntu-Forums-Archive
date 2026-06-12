---
title: "How 2 Change &quot;Automatic&quot; HD Test at Startup?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by GregA on 2010-05-17
G'Day,

I believe in Ubuntu Hardy Heron, the hard-drive check utility would run after about 30 or 40 startups.   

Upon starting Lucid Lynx yesterday, I saw the text info message that my hard drive was being checked for errors.  The process takes a while (10-15 minutes), which is not a problem for a periodic test, however, I had the same situation today upon initial startup.  

In each case, no errors were reported and the system runs fine.

How do I update this hard-drive test service, so that it runs only upon the 50th startup of Lucid (and not sooner unless there is a problem).

Thanks for any tips.

Greg

---

### Post by philinux on 2010-05-17
There was an update to mountall that fixed some of that.

```
sudo tune2fs -l /dev/sdXX

sudo tune2fs -c 50 /dev/sdXX

```

First command list how many boots. Second one changes the number.

If you look at the man page for tune2fs there is an option for a time based interval e.g monthly.

If the file system needs it it will run one anyway.

---

### Post by GregA on 2010-05-18
Thanks - - I just ran the latest updates . . . there were over 70 changes.  Let's see if the issue still lingers, and, if so, I'll use the commands per your feedback, , , I appreciate it.

---

