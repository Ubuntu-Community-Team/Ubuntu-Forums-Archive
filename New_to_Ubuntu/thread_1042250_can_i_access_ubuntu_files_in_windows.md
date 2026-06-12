---
title: "can i access ubuntu files in windows?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-17
i was wondering i can access my windows files inside ubuntu but is it possible to do the same thing but in windows?

---

### Post by taurus on 2009-01-17
Didn't you already ask this question before?

So, you want to access Ubuntu partition while you are in windows; is that what you're asking?

---

### Post by fuser312 on 2009-01-17
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

although theese tools will provide you read only facility

hope it helps

---

### Post by mamamia88 on 2009-01-17
> **taurus said:**
> Didn't you already ask this question before?

So, you want to access Ubuntu partition while you are in windows; is that what you're asking?

no i didn't ask this before.  and i was hoping there was a way since ubuntu now takes up almost all my hd space and i have windows on a 20gb island and don't really have much space

---

### Post by mamamia88 on 2009-01-17
thanks man that linux internals program looks great

---

### Post by taurus on 2009-01-17
If you want to access Ubuntu partition(s) while you are running windows, you can use fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by earthpigg on 2009-01-17
> **mamamia88 said:**
> i was wondering i can access my windows files inside ubuntu but is it possible to do the same thing but in windows?

yes, you can see/modify windows filesystems in any recent version of ubuntu.

with the assistance of a 3rd party program, you can see ubuntu files in windows.

the best solution, imo, is to have a partition specifically for sharing... format it fat32.

---

### Post by greenwich on 2009-03-06
Can someone please help me with these tools mentioned above? My basic problem is this:

Installed ubuntu via Wubi on Windows Vista a few weeks ago.
Ubuntu is now corrupt (booting just takes me to the grub command line).
Before I reinstall ubuntu via Wubi, I want to back up my ubuntu files.

I installed all three tools above but can't get any of them to work.

explore2fs: the program is running but all I see is a blank window like Windows Explorer. How can I get to see some files in it??

LinuxReader: I click on a drive and it says it can't read it. That's all it does for all my drives.

fs-driver: I assigned a letter L to a drive during installation, so now I have C, E and L drives. Now what?? How do I see my ubuntu files?

Any clues for me, please?

---

### Post by greenwich on 2009-03-06
Forgot to say...I don't have an ubuntu live CD, but I have a Knoppix live CD from a couple of years ago and it still boots fine. Could I use that to get access to my ubuntu files?

---

### Post by stchman on 2009-03-06
The disk internals software very well.  I would not recommend read/write privileges as you could delete something that Ubuntu needs.

---

