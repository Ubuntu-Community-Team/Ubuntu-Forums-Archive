---
title: "Lost 40GB of hard drive space??"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by 3rr0r on 2009-09-18
Hi there.  I triple boot Win Xp, Backtrack and Ubuntu.

Recently I was running out of space on my XP partition so I formatted my ubuntu partition, reinstalled on a smaller partition and increased the win xp partition.  Gparted shows my XP drive as being 40 GB bigger but when I boot into windows it doesn't show the change.  Where did the 40 GB go?

/dev/sda1 - win xp
/dev/sda2 - backtrack
/dev/sda3 - ubuntu
/dev/sda4 - swap

---

### Post by skatinjj on 2009-09-18
If you did not reinstall XP then you wouldn't be able to just increase the partition size unless you are using a dynamic disk configuration

Forgot to mention that dynamic disk is not supported on XP home (in case that is the edition you are using)

---

### Post by 3rr0r on 2009-09-18
Using XP Pro SP3.  So, how do I access the 40GB in windows?

---

### Post by skatinjj on 2009-09-18
in XP try running:

```
chkdsk /r
```

post output here please.

---

### Post by 3rr0r on 2009-10-05
I did... it did the full scan and the 40GB still not appearing.

---

### Post by halitech on 2009-10-05
Go into the control panel and open the Administrative tools and then Disk management. See if it can see the extra space in windows. I'm wondering if it didn't make a new partition thats not formatted so not showing up.

---

### Post by renkinjutsu on 2009-10-05
i think it was ```
chkdsk /f
```
the /f tells it to fix the filesystem.. but it'll output a message telling you it can't, asking you to schedule one at boot

say yes to that..

then reboot the computer

---

### Post by halitech on 2009-10-05
from [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

To repair errors, locate bad sectors, and recover readable information, at the command prompt, type chkdsk volume:/r, and then press ENTER.

To repair errors without scanning the volume for bad sectors, at the command prompt, type chkdsk volume:/f, and then press ENTER.


and no, you don't need to reboot to have it run. I just did it last night on a system I was working on and it did it without rebooting.

---

### Post by renkinjutsu on 2009-10-05
really?

i can't remember.. since the last time i did it was on XP a while ago.. Are you on vista? 7?

---

### Post by halitech on 2009-10-05
nope, I did it on an XP SP3 install.

---

### Post by renkinjutsu on 2009-10-05
then my memory must be failing me... maybe it was chkfs (exist?) or chkntfs (exist?) .. 

only thing i remember from windows is `chdir` and `defrag`

---

### Post by halitech on 2009-10-05
I'll double check, now that I think about it I may have run it on a drive other then c: and maybe that makes a difference.

---

