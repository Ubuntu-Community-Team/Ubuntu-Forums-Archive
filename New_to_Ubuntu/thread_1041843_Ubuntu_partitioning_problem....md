---
title: "Ubuntu partitioning problem..."
date: 2009-01-17
forum: New to Ubuntu
---

### Post by psychicpotato on 2009-01-17
Dear experts,

Sorry to bring up this problem again, I'm sure it's been raised up numerous times. My situation is a bit unique, and being paranoid about losing data of my hard drive, I decided to start a new thread on this.

Recently I've tried to upgrade my Ubuntu 7.10 to 8.04, but during the upgrade process it crashed (mistake on my part), and I haven't been able to boot up Ubuntu since.

My solution was to use the disk manager utility in Windows XP in my other partition to delete the entire Ubuntu installation. Of course by doing that I ran into the horrendous "GRUB error 17", but nothing a Super Grub Disk couldn't fix :)

I've now burnt myself a Ubuntu 8.10 LiveCD, and wish to reinstall it onto the partition which previously had Ubuntu 7.10. However, during the installation process the Ubuntu partition program does not allow me to install into the 'Free Space' partition where 7.10 previously was.

I was wondering how I could fix this...should I go ahead and install Ubuntu and fix it with gpartition later? Or is there something I could do with the XP disk manager?

Thank you very much for your patience and help.

---

### Post by 73ckn797 on 2009-01-17
> **psychicpotato said:**
> Dear experts,

Sorry to bring up this problem again, I'm sure it's been raised up numerous times. My situation is a bit unique, and being paranoid about losing data of my hard drive, I decided to start a new thread on this.

Recently I've tried to upgrade my Ubuntu 7.10 to 8.04, but during the upgrade process it crashed (mistake on my part), and I haven't been able to boot up Ubuntu since.

My solution was to use the disk manager utility in Windows XP in my other partition to delete the entire Ubuntu installation. Of course by doing that I ran into the horrendous "GRUB error 17", but nothing a Super Grub Disk couldn't fix :)

I've now burnt myself a Ubuntu 8.10 LiveCD, and wish to reinstall it onto the partition which previously had Ubuntu 7.10. However, during the installation process the Ubuntu partition program does not allow me to install into the 'Free Space' partition where 7.10 previously was.

I was wondering how I could fix this...should I go ahead and install Ubuntu and fix it with gpartition later? Or is there something I could do with the XP disk manager?

Thank you very much for your patience and help.

How, exactly, is it not allowing you to install to the free space?

I would boot from the Live CD and use Partition Editor to repartition and format the free space to "ext3", then install using manual partitioning and select that free space as the Ubuntu partition.

Have you tried that?

---

### Post by bumanie on 2009-01-17
You should be able to install where you want if you choose 'manual' at the partitioning stage and choose the 'space' to put 8.10 accordingly. 'Manual partitioning' during installation is pretty self-explanatory, but if you have problems, post again with specific questions and someone will help. If you choose the space you previoulsy had 7.10 on, click edit and you should be able to set up 8.10 in that space.

---

### Post by Hospadar on 2009-01-17
first off, for any partition changes i would use gparted from a livecd. It is the best way to be sure you are doing what you think you are doing

create the partitions the way you want them, the do the manual partitioning during the install, and mount your partitions the way you want, example mount points: / (for the root of your installation) /home (if you have a seperate home partition)

i would do any needed formatting in gparted, and uncheck all the formatting boxes in the installer just to be safe.

to start gparted, Alt-f2, gksu gparted

---

### Post by seagullplayer77 on 2009-01-17
> **73ckn797 said:**
> How, exactly, is it not allowing you to install to the free space?

I would boot from the Live CD and use Partition Editor to repartition and format the free space to "ext3", then install using manual partitioning and select that free space as the Ubuntu partition.

Have you tried that?

I would agree...If the free space doesn't have a file system, then it's no surprise that Ubuntu won't install. I would use the partitioner on the Ubuntu CD to format the free space as ext3, or reiser, or xfs, or whatever file system you'd prefer.

If it doesn't let you install after doing *that*, well, then you've got a problem :P.

---

### Post by 73ckn797 on 2009-01-17
> **bumanie said:**
> Windows is the best virus detector on the market!
Ubuntu attracts Human Beings - Windows attracts viruses and worms 			


As a side note: I love your signature about Linux/Windows.

---

