---
title: "Adding New hard drive with a controller"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by atuls on 2009-11-14
Hi all,

I'm new to the forum, and kind new to ubuntu. I've been using the system on and off for a while, but I consider myself new to ubuntu.

Well, I've built my server on 8.04 LTS. It's been up for about a month. Initially, I have two 80GB disks in Raid1 for system, and some storage. Recently, I'm trying to add 3 more new disks as Raid5 for network storage. I'm using an old mobo, so there are two SATA ports. The third disk is connected using a Rosewill RC-207 SATA to PCIE adapter. Here is my problem.

My system disk sda and sdb are reassigned to sdb and sdc due the the new disk, which becomes sda, connected to the controller. This happens whenever I reboot the system, but this won't happen if I hot plug the third disk after system boots. The change in disk letters causes some boot problem. Is there any solution to there without reinstalling system, or is it possible to fix "sdx" to certain drive?

I've tried to search, but I wasn't sure what to look for and there aren't many results.

Thank you in advance for helps

Chris

---

### Post by atuls on 2009-11-14
In addition, I can avoid the boot problem by temporarily remove the disk on controller when I reboot the computer, but it will take 2+ hrs to recover the raid5 array. Not very efficient.

Anybody have any suggestions?

Chris

---

