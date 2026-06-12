---
title: "how to add a panel shortcut"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by sallam on 2010-09-24
Greetings
Yesterday, I dragged a text file from a partition other than ubuntu partition, and dropped it in the top ubuntu panel. It created a shortcut.
But when I restarted my laptop today, clicking that shortcut gave an error that of no such file!
I re-dragged the same file again to the panel, and it worked.
Is this something to do with mounting partitions?
How can I make a permanent shortcut that works after system restart please?

---

### Post by mikewhatever on 2010-09-24
Place the file inside the Ubuntu partition (your home folder) or make sure that the other partition is automounted.

---

### Post by l32007 on 2010-09-24
Above poster this is absolute beginner talk,
You'll probably have to copy it over, or use a shortcut to that drive, and put it in the start of C:/ drive (im assuming its windows)

---

### Post by sallam on 2010-09-24
I can copy it over, but then the old file will not be updated with whatever I add to the text file, in case I use windows7.
How do you automount a partition?
does automounting take extra cpu resources? I mean, will it affect the speed of my humble celeron/1gb-ram laptop?

---

### Post by mcduck on 2010-09-24
> **sallam said:**
> I can copy it over, but then the old file will not be updated with whatever I add to the text file, in case I use windows7.
How do you automount a partition?
does automounting take extra cpu resources? I mean, will it affect the speed of my humble celeron/1gb-ram laptop?

You'll need to configure the drive in /etc/fstab to get it automatically mounted on startup.

And no, it will not use any extra resources. :D It simply tells your computer to mount that drive when the system is booting, instead of mounting it at the time when you try to access it (which is what you are doing now). Actually the way you are doing it now probably requires more resources (at least in theory)...

---

### Post by sallam on 2010-09-24
> You'll need to configure the drive in /etc/fstab to get it automatically mounted on startup.
Could you please give me easy newbie steps for doing this?

---

### Post by mikewhatever on 2010-09-24
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

Here you are.

---

### Post by QLee on 2010-09-24
[QUOTE=sallam]Could you please give me easy newbie steps for doing this?[/QUOTE]
sallam, I see from your sig that you're using 10.10. I hope you are aware that it hasn't been released yet and may contain bugs. It's meant for more experienced users who can determine the difference between a bug and their own mistakes, and then fix the problem and/or submit a bug report to the developers. The un-released software shouldn't yet be used as a day-to-day system, except for experienced users. Most of the people who test do so on a test system, rather than the one they use for normal operation. You can choose to do whatever you wish, but I suggest that an inexperienced user wait until the release.

There is also a separate sub-forum for people who are testing 10.10 and they are familiar with the common problems encountered.

---

### Post by sallam on 2010-09-24
Thanks mikewhatever for the link.
QLee, thanks for the advice. I found the beta very stable, and so far had no problems with it. Its only a few days before 10.10 stable gets released anyway.
Many thanks.

---

