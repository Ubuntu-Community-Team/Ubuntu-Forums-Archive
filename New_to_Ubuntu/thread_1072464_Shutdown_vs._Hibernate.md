---
title: "Shutdown vs. Hibernate"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by kiruch on 2009-02-17
i'm a former Windows user and from my experience, using Hibernate instead of Shutdown isn't a good idea - after "waking up" from Hibernate Windows XP would become slow and stupid.

i've tried hibernating my Xubuntu several times, and it worked just fine after that.

i start thinking that maybe i should always Hibernate, because waking the system takes much less time than booting it (at least in my case).

am i doing the right thing? :) or Hibernating is still worse than shutting down, and if it is, how exactly?

---

### Post by DGortze380 on 2009-02-17
> **kiruch said:**
> i'm a former Windows user and from my experience, using Hibernate instead of Shutdown isn't a good idea - after "waking up" from Hibernate the computer becomes slow and stupid.

i've tried hibernating my Xubuntu several times, and it worked just fine after that.

i start thinking that maybe i should always Hibernate, because waking the system takes much less time than booting it (at least in my case).

am i doing the right thing? :) or Hibernating is still worse than shutting down, and if it is, how exactly?

[http://en.wikipedia.org/wiki/Hibernate_(OS_feature](http://en.wikipedia.org/wiki/Hibernate_(OS_feature))

There is no harm in hibernating.

---

### Post by az on 2009-02-17
Hibernating is just fine, although it<s not an alternative to shutting down sometimes.  For example, if you run two or more linux system that share the same swap space, the hibernation data (the contents of your ram before you hibernate) are written to the swap space.  The second linux system will either overwrite your hibernated data, or not be able to use the swap space.

The other thing is updates.  If the kernel, or the hardware abstraction layer get upgraded, you need to reboot to dump them out of your ram.  Hibernating won't do that.

Other than that, hibernating should not cause you any problems.

---

### Post by Zenze on 2009-02-17
I'm not expert, but I don't think Hibernating is "worse" than shutting down.

When you hibernate your computer writes all the data in memory to the hard drive, and then turns off. When you wake it up to reads the data that it wrote the the hard drive back into memory, so it picks up right where it left off.

However, when you shut down it saves what it basically quits all of its tasks and turns off. Then when you boot up you have nothing in your memory except for system stuff.

If you are just putting your computer away for a short time to carry it around I would use Suspend/Hibernate. If you are going to leave it off for a long time I would shut down. Shutting down will clear all your memory that may still be taken up from a memory leak in a program you were running before.

---

