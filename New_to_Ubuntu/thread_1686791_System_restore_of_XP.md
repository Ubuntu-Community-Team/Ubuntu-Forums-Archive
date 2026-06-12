---
title: "System restore of XP"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by grad_student on 2011-02-12
I want to do a system restore of my XP back before I installed Ubuntu. Since the disk is partitioned, will doing a system restore prior to installing ubuntu mess up ubuntu?

---

### Post by Bucky Ball on 2011-02-12
How could it if Ubuntu is not yet installed ??? ;)

---

### Post by Rubi1200 on 2011-02-12
Before you install Ubuntu, make sure you have backups and be sure to defragment and run chkdsk on the Windows file-system.

---

### Post by grad_student on 2011-02-12
Sorry guys I wasn't very clear. I have ubuntu installed and have been using it for almost a year. I dual boot into XP to run some pieces of software. As of late, XP has gone bonkers and I'd like to do a system restore on it. My question is will it affect ubuntu?

---

### Post by lisati on 2011-02-12
> **grad_student said:**
> Sorry guys I wasn't very clear. I have ubuntu installed and have been using it for almost a year. I dual boot into XP to run some pieces of software. As of late, XP has gone bonkers and I'd like to do a system restore on it. My question is will it affect ubuntu?

Chances are that there will be some effect, depending on how aggressively the restore process goes about its business. It could be anything from overwriting grub to wiping Ubuntu completely. As someone else has said, it won't hurt to make a backup of your important files.

---

### Post by Rubi1200 on 2011-02-13
As far as Ubuntu being affected, as Lisati points out, there is a chance.

Here is what I suggest:

1. make backups of important data

2. make sure you have an Ubuntu CD ready in the event that you need to do something like reinstall GRUB or do file-system checks from the LiveCD

3. choose your restore point in Windows carefully; I would imagine the further back you go the more likely it is that it might affect Ubuntu.

4. if you need specific help with a Windows problem, why not try a Windows forum and see if someone can help you before you do a system restore?

sevenforums is supposed to be really good.

---

### Post by Mark Phelps on 2011-02-14
Unless you set about a HUGE amount of space for System Restore, you're not going to have a Restore Point still there from over a year ago.  Most folks are lucky to be able to go back a month.

If what you mean is restoring to the original condition, something done using a recovery partition or restore CD, then that will most probably reformat the hard drive and remove Ubuntu.

---

