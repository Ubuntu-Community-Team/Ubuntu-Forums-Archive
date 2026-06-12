---
title: "Two releases, only one works"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by elendilnl on 2009-11-30
I'm fairly new to Ubuntu, so explaining may take some time :)   A few days after I installed Ubuntu 9.10 I got an update message and after updating things went a bit strange.  I used WIBU to install Ubuntu, so during booting I can choose between Vista and Ubuntu. When I choose Ubuntu I could choose between 2.6.31-14-generic and the recovery entry. After the upgrade I can choose between 2.6.31-14 and 2.6.31-15. Whenever I choose the -15 generic I get the following message:  [Linux-bzImage, setup=0x3400, size=0x36fd0e0] [Initrd, addr=0x3782c00, size=0x7c3a0b] [       2.365895] Kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block(8,2)  I have to reset the computer in order to run the 2.6.31-14  version. What can/must I do to correct this?    Another problem I have is that, even without a program running (except System Monitor), all four cores of my processor run at 100%. How is that possible?  Thanks in advance,        -=[ Jurre ]=-

---

### Post by ukripper on 2009-11-30
Check this [https://bugs.launchpad.net/wubi/+bug/477169](https://bugs.launchpad.net/wubi/+bug/477169) bug report and read post **[SIZE="6"]#69[/SIZE]** to resolve your problem

---

