---
title: "post motherboard replacement issues"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by dhirajkhanna on 2010-10-20
Hello,
Have a dual boot-Ubuntu and Win XP. Replaced motherboard. From GRUB, can boot up Ubuntu with no problems, however, no joy in booting XP. Help would be appreciated.

---

### Post by mick8985 on 2010-10-20
chances are you have your windows partition on a seperate hard drive is this correct?

---

### Post by jmszr on 2010-10-20
dhirajkhanna,

Here are a few links regarding your situation: [http://www.theeldergeek.com/replace_motherboard.htm](http://www.theeldergeek.com/replace_motherboard.htm) and:  [http://support.microsoft.com/kb/824125](http://support.microsoft.com/kb/824125). Also: [http://arstechnica.com/hardware/news/2007/09/how-to-install-a-new-motherboard-without-reinstalling-windows.ars](http://arstechnica.com/hardware/news/2007/09/how-to-install-a-new-motherboard-without-reinstalling-windows.ars) .

Hope that helps.

---

### Post by dhirajkhanna on 2010-10-21
@jmszr Thanks for the links. Problem is, I don't have my XP installation CD. Was pirated anyway!

@mick 8985 The hard disk is partitioned and one of the partitions' holds XP.


So does it imply that I am doomed?

---

### Post by Grenage on 2010-10-21
> **dhirajkhanna said:**
> @jmszr Thanks for the links. Problem is, I don't have my XP installation CD. **Was pirated anyway**!

@mick 8985 The hard disk is partitioned and one of the partitions' holds XP.


**So does it imply that I am doomed?**

Your immortal soul.... perhaps.

You should be able to get it working, by running a sudo grub-update.

---

### Post by KirbySmith on 2010-10-21
Win NT 5.1 (XP) is sufficiently similar to Win NT 5.0 (Win 2k) that its behavior with a new motherboard should be similar.  As I recall for Win 2k, an elaborate process is needed to get the OS to adapt to a new motherboard without performing a new install.  NT expects to boot up and find all the processor, memory, bus, bridge, etc. parameters to be the same as before.  

Linux, on the other hand, has the wonderful ability to boot up, check out its "surroundings," and adapt as required with little fuss.  I recently confirmed this with Ubuntu 9.10 copying from Desktop 1 below to Desktop 2.   The only exception I am aware of is that if the two setups use different video drivers, the old video driver has to be removed before performing the cloning.

kirby

---

### Post by mick8985 on 2010-10-22
No, you're in no way "doomed", but we don't have enough information to diagnose your problem.
Describing what happens during boot would be a start.

---

