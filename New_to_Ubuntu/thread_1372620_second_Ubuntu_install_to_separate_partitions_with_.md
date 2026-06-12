---
title: "second Ubuntu install to separate partitions with GRUB2"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by wyatt roberts on 2010-01-04
I have 2 ubuntu installs, 9.10,- one on each of 2 hard drives.  I like the first one best because it's the most mature - I just started the second with a new hard drive.  I should mention that the system is identical but for two eSata drives, both of which boot nicely. I have multiple partitions on the second drive.  Here's what I want to do:

I have tarred the system and Home partitions from the original (mature) install (disk1).
I want to untar them to separate partitions on Disk 2 (the new, larger one)

I then want to have Grub 2 on the new disk 2give me the option of choosing the new install or the original (mature) install from disk 1 (untarred on disk 2)

My understanding is that I can either update-grub OR grub-mkconfig, with the latter given preference based on:

"grub-mkconfig - /usr/sbin/grub-mkconfig - a script for making a new  /boot/grub/grub.cfg file.

As far as I know this command is supposed to be used in preference to update-grub in Karmic Koala and later versions of Ubuntu. Earlier version of Ubuntu didn't seem to contain this script. This command is more versatile than update-grub because we can use the -o option to have the results printed to a any filename and file path we like. That's a useful feature.

This script also runs other scripts and programs such as grub-mkdevice.map and grub-probe and then generates a new grub.cfg file." 
from: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig")

That is my plan: copy the tarred system.tgz to a partition, copy the tarred home.tgz to a separate partition, untar them and then run: grub-mkconfig - /usr/sbin/grub-mkconfig

I'm trying a lot of things for the fist time with Ubuntu... I'm hoping someone who had done something similar can review this plan and confirm it ought to work...

Thanks,
Wyatt

---

### Post by ikt on 2010-01-05
> **wyatt roberts said:**
> I have 2 ubuntu installs, 9.10,- one on each of 2 hard drives.  I like the first one best because it's the most mature - I just started the second with a new hard drive.  I should mention that the system is identical but for two eSata drives, both of which boot nicely. I have multiple partitions on the second drive.  Here's what I want to do:

I have tarred the system and Home partitions from the original (mature) install (disk1).
I want to untar them to separate partitions on Disk 2 (the new, larger one)

I then want to have Grub 2 on the new disk 2give me the option of choosing the new install or the original (mature) install from disk 1 (untarred on disk 2)

My understanding is that I can either update-grub OR grub-mkconfig, with the latter given preference based on:

"grub-mkconfig - /usr/sbin/grub-mkconfig - a script for making a new  /boot/grub/grub.cfg file.

As far as I know this command is supposed to be used in preference to update-grub in Karmic Koala and later versions of Ubuntu. Earlier version of Ubuntu didn't seem to contain this script. This command is more versatile than update-grub because we can use the -o option to have the results printed to a any filename and file path we like. That's a useful feature.

This script also runs other scripts and programs such as grub-mkdevice.map and grub-probe and then generates a new grub.cfg file." 
from: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig")

That is my plan: copy the tarred system.tgz to a partition, copy the tarred home.tgz to a separate partition, untar them and then run: grub-mkconfig - /usr/sbin/grub-mkconfig

I'm trying a lot of things for the fist time with Ubuntu... I'm hoping someone who had done something similar can review this plan and confirm it ought to work...

Thanks,
Wyatt

Heya,

I think it sounds overly complicated for what you want to, why not go with the new install and just install all the programs your missing from the mature install and copy the data over?

Hope it all works out :)

---

### Post by theozzlives on 2010-01-05
Your settings and documents are only in your /home. All you have to do is copy everything in the "mature" /home to the other /home. You may have to install any software you've added, but that's easy.

When I do a fresh install, I leave my /home partition alone and just reinstall my packages.

---

### Post by wyatt roberts on 2010-01-05
> **ikt said:**
> Heya,

I think it sounds overly complicated for what you want to, why not go with the new install and just install all the programs your missing from the mature install and copy the data over?

Hope it all works out :)

You're probably right.  I may be excessively concerned about making a big blunder and losing things.  If I had a second install, short of losing the hard drive I could just copy home or system over from the still working one and be backup... although I seem to learn a lot from my mistakes...That was my ultimate plan... a disk clone on the same disk..., sort of like hot swaping installs by copying over the damaged one... If I had a backup system in place I had confidence in I'd feel better.  On windows I used Acronis, and it performed with never a hitch and I have multiple backups of xp and that confidence let me proceed with abandon, knowing I could come back to the same spot I was earlier. (And I have used that multiple times...note I did not mention a microsoft backup product - Acronis is Linux I think- they just don't have an economical linux product.) Once I have the same thing in place for Linux, I will relax.

Your approach is easier though.  I will probably do as you suggest while I am pursuing a backup system I feel confident in.  I though I had it with Mondoarchive because it worked on the first install, to at least  complete the backup, although I never got through the restore to check yet... I couldn't get it to backup the new system yet... I'm still working at it.  I appreciate your suggestion, since that is the system I like, I will do that while I work on the backup part.

Thanks,
Wyatt

---

### Post by wyatt roberts on 2010-01-05
> **theozzlives said:**
> Your settings and documents are only in your /home. All you have to do is copy everything in the "mature" /home to the other /home. You may have to install any software you've added, but that's easy.

When I do a fresh install, I leave my /home partition alone and just reinstall my packages.

The new disk is bigger so I need the earlier /home on the new disk.  Would you have a recommendation on how to put it there... Untar over the more recent install /home partition or live disk and cp recursively over the newer /home?

Thanks,
Wyatt

---

