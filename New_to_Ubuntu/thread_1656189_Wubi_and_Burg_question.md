---
title: "Wubi and Burg question"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by turtlecloud on 2010-12-30
First, how do I check that I am using Wubi? I installed ubuntu quite a while ago and forgot how I did it.

Second, how do I install burg with wubi? Is it possible?

---

### Post by wilee-nilee on 2010-12-30
NO, Burg is grub do not install it or take any grub-pc, or grub common updates in wubi.

You see a grub menu but grub within wubi is not the same as a regular install.

If you get a grub menu at startup you have a partitioned dual boot. 

If you get the windows boot from menu you have wubi.

---

### Post by Rubi1200 on 2010-12-30
Are you able to boot into Ubuntu?

Same for Windows?

A word of caution: do NOT try and install/use boot managers like burg; you will break the Wubi install!

You can check in Windows either under Add/Remove Programs or at the root of, presumably, the C drive.

For general information, issues, as well as solutions for Wubi installs:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

