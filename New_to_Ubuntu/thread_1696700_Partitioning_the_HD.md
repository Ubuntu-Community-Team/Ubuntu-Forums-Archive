---
title: "Partitioning the HD"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Alienspecimen on 2011-02-27
Dell Inspiron Mini Netbook

About half an year ago I installed Linux netbook edition on my sons Dell Inspiron Mini and configured it as a double boot system ie Windoz and Linux.  

I was not sure what I was doing and during the installation I created at least three Linux partitions and also attempted to split the available space equally between both operating systems.

My son attempted to consolidate the Linux partitions and also dedicate more space to Windoz, but in the process he erased the Linux OS and the computer did not start.  (more detail here: [http://ubuntuforums.org/showthread.php?t=1692755](http://ubuntuforums.org/showthread.php?t=1692755))

I am attempting to fix the problem by reinstalling Linux, but am stuck at the "Allocate Drive Space" screen.  Here is what I see:

                                 Size               Used
sda1 (fat16)             41MB             33MB
sda2 (ntfs)               34787MB       Unknown
sda5 (ntfs)               43293MB       3221MB
sda6 (Linux Swap)  1892MB         0MB
sda7 (ext4)              40647MB       6448MB
sda8 (ext4)              34778MB       8295MB
free space               4594MB

The only thing I want to do is split the 160GB disc into two equal partitions between both OS.  How do I do that?  

Thank you very much in advance

Best

Boris

---

### Post by Hedgehog1 on 2011-02-27
> **Alienspecimen said:**
>                                  Size               Used
sda1 (fat16)             41MB             33MB
sda2 (ntfs)               34787MB       Unknown
sda5 (ntfs)               43293MB       3221MB
[B][COLOR="Red"]sda6 (Linux Swap)  1892MB         0MB
sda7 (ext4)              40647MB       6448MB
sda8 (ext4)              34778MB       8295MB[/COLOR][/B]
free space               4594MB
Boris

Boris,

Unlike a simple application, an Operating System usually just wipes out the previous one on the disk.

Ubuntu allows you to add itself as a second OS, but you cannot keep re-adding it without creating some screwy paritions.

My I suggest you stop the re-installation, reboot the LiveCD and use Gparted to remove sda6, sda7 and sda8.

Then do a reinstall - this time 'manually' (inside the install) creating two partitions, the larger one for the '/' (ext4) and one for Swap (make swap space twice the size of the systems amount of, RAM)

:KS

---

### Post by Hedgehog1 on 2011-02-27
Boris,

Once the re-install of Ubuntu happens, grub (**GR**and **U**nified **B**ootlader) will be reinstalled, the the current version of windows will appear in the grub menu and boot again.

:KS

---

### Post by JC Cheloven on 2011-02-27
> **Alienspecimen said:**
> The only thing I want to do is split the 160GB disc into two equal partitions between both OS.  How do I do that?  

To answer your exact question: 
[INDENT]First you need to know where your XP is. It could be sda2 or sda5. For a try to find out, could you please post the output of ```
sudo fdisk -l
``` My guess is sda2 anyway. If so, that's not good news, as it seems to have been shutdown to a bad state (the sympthom is that the amount of used space is reported as unknown). Ubuntu will probably refuse to resize, or mount, or do any change in a filesystem in that state. But it still will recognize a win2 boot there if you install ubuntu. Well, hopefully. In a future boot on win2, it will repair his own filesystem, again hopefully.[/INDENT] 

[INDENT]Then, there's sda5. Most likely you have some data (3Gb) on it that you may want to save somewhere else before proceeding.

Then you should delete sda5, 6, 7 and 8 using gparted from live. Only dsa1 and 2 would remain. Then create and extended partition of ~ 80Gb at the end of the disk. Thus, about 45Gb of unused space will be next to sda2. Then create inside the extended partition two logical partitions, one ext4 of ~ 79Gb, and one swap of ~1Gb. Then install ubuntu choosing the 'advanced' option at the time of partitioning, and installing in the 79Gb partition, that will be sda5 in the new scheme. Then boot from the HD: grub should show entries for ubuntu and xp. When booting xp, it should manage to get things ok in sda2. Then you can use some windows tool to enlarge the xp partition to fill the 45Gb unused space you left before. Or you can boot from live ubuntu and use gparted again to do this (once the filesystem sda2 is in a good readable state)
NOTE: ALL THIS IS QUITE AN INVOLVED PROCESS, SOMEHOW PRONE TO ERRORS, BOTH ON YOUR SIDE AND FROM THE SEVERAL TOOLS USED.
[/INDENT] 

I could give an opinion -if asked- about how good is the partition scheme you intend for a typical use case, but I'll not further complicate the subject ;)

EDIT: Just saw Hedgehog posts. We mostly gave similar advice. Only, at some point you should collect the space of sda5 (or similar amount) to joint it to your xp partition, in order to get your intended scheme. What I said is a possibility to do it, among others.

---

### Post by Hedgehog1 on 2011-02-27
> **JC Cheloven said:**
> ...
EDIT: Just saw Hedgehog posts. We mostly gave similar advice. Only, at some point you should collect the space of sda5 (or similar amount) to joint it to your xp partition, in order to get your intended scheme. What I said is a possibility to do it, among others.

JC Cheloven,

Your scheme is the more complete, and would waste no disk space.

I was going for the ***'Please let Daddy survive what you did, Son'*** simpler option.

Boris (and Son): Either way works.  Think of this as Father/Son time. Please limit any yelling! :)

---

### Post by Alienspecimen on 2011-02-28
Thank you all for your answers.

I got a plan...

1.  Install Linux on one of the partitions, just to be able to boot up Windoz

2.  In Windoz, use a partitioning tool to convert the entire drive to NTFS so Windoz could utilize the entire space.

3.  Once done, reinstall Linux creating only two equal partitions, one for Windoz and another one for Linux

How does this sound?

I would appreciate if someone points me to a Windoz tool that will erase the partitions and format the rest of the drive.

Thanks 

Boris

---

### Post by JC Cheloven on 2011-02-28
Alienspecimen: there are some unnecessary and posssibly twisted details in that plan: It will make you install, delete, and then reinstall ubuntu. You don't need to.

I think the previously given advice would be better. Anyway, to answer your last question, the windows tool could be Partition Magic. 

By the way, if you are willing to follow your plan, perhaps you could consider that a similar (or little more) amount of work would be required to wipe your entire disk, make empty partitions just as you like (using gparted from live, creating one ntfs for win2, one ext4 for linux, and a third one for swap, for example), then installing windows in the ntfs one, and ubuntu in the ext4.

Best wishes, whatever you do ;)

---

### Post by Hedgehog1 on 2011-02-28
> **Alienspecimen said:**
> 
1.  Install Linux on one of the partitions, just to be able to boot up Windoz

2.  In Windoz, use a partitioning tool to convert the entire drive to NTFS so Windoz could utilize the entire space.

3.  Once done, reinstall Linux creating only two equal partitions, one for Windoz and another one for Linux
s 

Boris

Boris (and Son),

You will get bit by this plan because once you format the Linux partition, the computer will stop booting.

Instead, perhaps the better idea is to put back the 'boot directly into windows' MBR (**M**aster **B**oot **R**ecord).

Booting from the windows 7 emergency repair disk, do the following:

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/5151606.png?619[/IMG]

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/2756040.png?559[/IMG]

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/1433690.png?753[/IMG]

Then you can boot into windows and manage the partition from disk management:

[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/7688459.png?812[/IMG]

You can the opt to reinstall Ubuntu in whatever way makes sense.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-02-28
> **JC Cheloven said:**
> Alienspecimen: there are some unnecessary and posssibly twisted details in that plan: It will make you install, delete, and then reinstall ubuntu. You don't n

....

Best wishes, whatever you do ;)

My goodness you can post fast.  Yah beat me again!

:lolflag:

---

