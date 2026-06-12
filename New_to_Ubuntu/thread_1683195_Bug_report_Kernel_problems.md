---
title: "Bug report: Kernel problems"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2011-02-07
Hi, 

I have had problems with all of the kernels in 10.10, save for 2.6.35-22. -23, -24, and -25 have all resulted in the same kind of random system freeze, albeit with an apparently differing frequency, requiring a forced system reboot. In most cases this has made the kernel unusable, so i have stayed on -22.

I am not sure if the problems i have had with the other kernels are the sorts of thing that i should report as a bug. Because it seems like its the same problem, and because its not being fixed with subsequent kernels, I think that i should. That said, i am not sure what sort of information to attach to a bug report on such a generic problem. 

So if someone could tell me if this is something i should report and what information to attach, that would be great.

---

### Post by NightwishFan on 2011-02-07
You can boot into the kernel that freezes, and if it fails, boot into one that works, and browse the logs in /var/log/ for information (remember to record the time of the freeze so it is easy to find in the log. A better way to look at logs is: System -> Administration -> Log File Viewer.

---

### Post by MorrisseyJ on 2011-02-07
Thanks for this. One question though.

As i don't really know what i am doing, is there any advice you can give me about which logs, in the left hand panel, i would do well to look at for information on a system freeze like the one i am describing?

Thanks.

---

### Post by MorrisseyJ on 2011-02-07
So just had a freeze on 2.6.35-23.

I have looked through the log files and can't anything in any of the tabs which even documents the time that the system froze.

If anyone has any advice that would be great.

---

### Post by NightwishFan on 2011-02-07
Try checking like "syslog.0" or etc, is the old one.

---

### Post by MorrisseyJ on 2011-02-08
I can't see anything in there at the time of the freeze. 

My system managed to run for about 3 minutes before freezing. All the log reports seem to be around the time i was booting up and logging in. So there is about a 2 minute lull in the logs, with no activity for 2 mins before the freeze. Nothing corresponds with the time of the freeze. 

I am not sure what to do with this.

---

### Post by MorrisseyJ on 2011-04-15
Never managed to identify what was going on in the logs or what was causing the system freezes. It does seem, however the problem has abated since i started running off the 2.6.35-28-generic-pae kernel. Did the updates this morning and haven't had a freeze all day.

If anyone knows what the conflict was and what the updates have sorted out it'd be great to know.

---

### Post by akakingess on 2011-04-15
You might want to check out Launchpad.net and do a search to see if others were having issues with those kernels in which case the solution should also be located there.

---

