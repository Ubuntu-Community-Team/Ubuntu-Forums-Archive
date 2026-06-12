---
title: "Init missing"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by hero2011 on 2011-01-24
Need help from the forum,
i have been using Linux Mint9 for the last 6 months as the first user of linux OS.
all over sudden when i was using this new year the system stopped and rebooted.
the next thing is that the screen is blank and it indicates [INIT MISSING.] try bootrap.
i can't access my desktop.i had only one partition and my data was in home user.
how can i retrieve my desktop and my data?

---

### Post by [Snc] on 2011-01-24
> **hero2011 said:**
> Need help from the forum,
i have been using Linux Mint9 for the last 6 months as the first user of linux OS.
all over sudden when i was using this new year the system stopped and rebooted.
the next thing is that the screen is blank and it indicates [INIT MISSING.] try bootrap.
i can't access my desktop.i had only one partition and my data was in home user.
how can i retrieve my desktop and my data?

do you mean:

> Target filesystem doesn't have requested /sbin/init. No init found. Try passing init= bootarg.

this means that the root filesystem couldn't be mounted, so i would check whats wrong with a live CD and try to fix it there.

FYI: info from [http://askubuntu.com/questions/17647/days-old-but-wont-boot-missing-sbin-init-help](http://askubuntu.com/questions/17647/days-old-but-wont-boot-missing-sbin-init-help)

---

### Post by matt_symes on 2011-01-24
Hi

> i had only one partition and my data was in home user.
how can i retrieve my desktop and my data?

Boot up from a LiveCD, create a directory under mount or media and mount the partition on that directory. You can access your data that way.

You should back up regularly so this is a good time before trying to fix the problem.

Kind regards

---

### Post by hero2011 on 2011-01-24
Thanks All.
Exactly that is the message.i tried all means but didn't succeed because if i try to mount it refuses to that.
@Snc.you mean if i do like that i will get my data.i just put the hard disk down and just came for help from this forum.
i will try that method.

---

### Post by [Snc] on 2011-01-24
> **hero2011 said:**
> Thanks All.
Exactly that is the message.i tried all means but didn't succeed because if i try to mount it refuses to that.
@Snc.you mean if i do like that i will get my data.i just put the hard disk down and just came for help from this forum.
i will try that method.

My guess was just, that sbin/init/ is somehow malformed, with a live CD/USB you can easily check that without threatening your already installed OS.

That would be the first thing i would do, if its okay, then i would search and check through the log messages - run
```
gnome-system-log
```
and thats where any problems should be visible.

I hope this helped in any way, let us know!

---

