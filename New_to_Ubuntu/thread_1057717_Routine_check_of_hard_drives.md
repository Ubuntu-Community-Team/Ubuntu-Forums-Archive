---
title: "Routine check of hard drives"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by bosun1000 on 2009-02-02
Can anybody please help?
I am running a dual boot system with Ubuntu Hardy Heron & my second choice Windows XP 
When Ubuntu boots up it goes straight to the "routine check of hard drives" If I let this complete the system crashes but if I press "Esc" and skip the check, Ubuntu loads and works as normal.
is there any code I could run to repair this boot fault?
Thanks
Bosun

---

### Post by Ben Page on 2009-02-02
This is not a boot fault, you probably turned off the computer "violently", or had a power failure etc. So now Ubuntu is checking disc, if there is a problem in filesystem and bad sectors. XP is doing similar thing when you do this (especially XP no SP). The disk check is scheduled so there is a way to cancel the scheduling, but that is a question for Ubuntu gurus. I can sugest to check your discs for errors in XP, if XP crashes when checking, you got a faulty disc or filesystem. If check passes, then Ubuntu should do the check for itself without chrashing.

---

### Post by Praxicoide on 2009-02-02
Have you tried to use the utilities under the failsafe session? Checking the hardrive with fdisk should at least give you some output to get a better idea of what's going on.

---

### Post by expatCM on 2009-02-02
You can manage this process to change the frequency or change when the check runs.  The easiest way of doing this is to use Autofsck and you will find details at this link
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

The program downloads as a .deb so it is really easy to install.

---

### Post by bosun1000 on 2009-02-02
Thanks I seem to have solved my problem I downloaded AutoFsck and installed it. This forced the issue as on restarting  Ubuntu went straight to the routine check and promptly crashed even when pressing Esc to skip the check so I was forced to start in recovery mode which said some sectors on my hard drive failed and said I had to run Fsck manually from root which I did I just kept following the on screen prompts saying yes to numerous fixes when this finished I rebooted and deep joy, all is well and hunky dory!
Thanks again for your help this enables me to complete 6 months of Windows free computing!
Bosun  



> **expatCM said:**
> You can manage this process to change the frequency or change when the check runs.  The easiest way of doing this is to use Autofsck and you will find details at this link
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

The program downloads as a .deb so it is really easy to install.

---

