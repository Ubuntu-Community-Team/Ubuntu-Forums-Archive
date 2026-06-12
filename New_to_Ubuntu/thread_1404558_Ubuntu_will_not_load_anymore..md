---
title: "Ubuntu will not load anymore."
date: 2010-02-11
forum: New to Ubuntu
---

### Post by mightyh on 2010-02-11
My Ubuntu 9.10 will not load anymore after installing the updates from the Update Manager. I get the message after restarting under the heading: [1.469482] Kernel panic- not syncing : VFS : Unable to mount root fs on unknown-block (8,2). I am very surprised that this will happen especially after installing the security updates from the Update Manager. Is there a way I can still save my Ubuntu?

---

### Post by Rex Bouwense on 2010-02-11
> **mightyh said:**
> My Ubuntu 9.10 will not load anymore after installing the updates from the Update Manager. I get the message after restarting under the heading: [1.469482] Kernel panic- not syncing : VFS : Unable to mount root fs on unknown-block (8,2). I am very surprised that this will happen especially after installing the security updates from the Update Manager. Is there a way I can still save my Ubuntu?

Try to boot from a previous kernel.

---

### Post by grizato on 2010-02-11
Recover you files with a live-cd

and reinstall.

---

### Post by Mustard on 2010-02-11
> **mightyh said:**
> My Ubuntu 9.10 will not load anymore after installing the updates from the Update Manager. I get the message after restarting under the heading: [1.469482] Kernel panic- not syncing : VFS : Unable to mount root fs on unknown-block (8,2). I am very surprised that this will happen especially after installing the security updates from the Update Manager. Is there a way I can still save my Ubuntu?

There is no straightforward answer to this question.  A lot of points need to be covered first....

1. Did the updates change grub?  Maybe grub can be repaired as it was mis-configured during the update?

2. Is your file-system accessible from a live CD?  If so, your file-system is most likely intact and you can save your data and settings before a clean install.

3. The suggestion made earlier about booting with an 'older kernel' might work.  It could be that the new kernel had created unforeseen issues on your hardware, whereas the older kernel (which still resides on your hard drive) may run perfectly well.

Often times if you are hit with these problems, it might just be easier to do a clean install, especially if you have your /home directory on a separate partition.  The advantages of a clean install is it saves you a lot of time and mucking around in getting the system up and working.  While it might be a nice learning experience to get it working through troubleshooting, sometimes learning is not the goal and its more a painful experience. :)

Probably the most important question is how long have you been using linux and how good are your command line skills?

If you havent been using linux for very long and your command line skills are non-existant, then a clean install is a very good option. Just get your data off the drive first!

---

### Post by mightyh on 2010-02-12
Thanks Mustard. I am still a newbie with Linux and my command skills are still a bit shaky. I will go for your suggestion for a clean install. I will lose some of my data but it will be a learning experience....:D

---

