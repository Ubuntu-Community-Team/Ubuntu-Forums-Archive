---
title: "Can I run apps from other Ubuntu partiotion"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Mortesins93 on 2010-08-25
Hello,
I have installed on my computer two different Xubuntus on two different partitions sda2 and sda5, I was wondering if I could run a program from for example partion sda5 using the Xubuntu from the partition sda2. If so how?
Thanks in advance

---

### Post by Mortesins93 on 2010-08-25
By the way, i misspelled partition on the thread, how can I correct the mistake or change the thread title?

---

### Post by ajgreeny on 2010-08-25
You probably can; you can certainly try.

As an example I have a partition on my machine, but on a separate hard drive, with a minimum install CD version of ubuntu plus LXDE desktop installed.  In my main ubuntu OS I can run at least some applications from the LXDE partition not on my main ubuntu with the full pathway to the executable as the command such as ```
/media/LXDE/usr/bin/leafpad
```It works as if it was instaled on the main OS.  The other partition must be mounted, of course, and I suspect there could be dependency problems for some apps, but for simple ones like leafpad, no problem.

---

### Post by Paqman on 2010-08-25
You can, but [it's a bit geeky]("https://help.ubuntu.com/community/BasicChroot") to set up.

---

### Post by Mortesins93 on 2010-08-26
Ok thanks a lot, I'll have a look at that and see if it's worth it.

---

