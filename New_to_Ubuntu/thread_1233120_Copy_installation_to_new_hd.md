---
title: "Copy installation to new hd"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by cthlhu1987 on 2009-08-06
Hi, this is an absolute beginner question:
I wanna buy a new, bigger hd. How do I copy the whole content of the old hd absolutely 1 : 1 to the new? And how to resize the partitions without (or at least, with a minimal) risk of data loss (I have an ext3-partition for Linux, NTFS for Windoze XP and a bigger FAT32 for Data)? Is there a program to do it more or less easy and without or with a minimal risk? thx in advance for the answers.

---

### Post by wizard10000 on 2009-08-06
> **cthlhu1987 said:**
> Hi, this is an absolute beginner question:
I wanna buy a new, bigger hd. How do I copy the whole content of the old hd absolutely 1 : 1 to the new? And how to resize the partitions without (or at least, with a minimal) risk of data loss (I have an ext3-partition for Linux, NTFS for Windoze XP and a bigger FAT32 for Data)? Is there a program to do it more or less easy and without or with a minimal risk? thx in advance for the answers.

The absolute easiest way?  Takes a little time but it works.

Install the new hard drive and assuming your old hard drive is sda and the new one is sdb, you'd open a terminal window and type this -

```
sudo dd if=/dev/sda of=/dev/sdb
```

which will make an identical copy of the hard drive.  You can then use gparted or something similar to resize partitions pretty much however you like.  Took me about 30 minutes for a 36gb drive and you can speed it up with command line switches so maybe someone else can help with that.

Another option is to burn a g4l live CD and do a raw copy with that - but all it is is a pretty GUI to the same terminal command.

But - make darn sure you have the source and target drives right.

Good luck -

---

### Post by TMAN 1 on 2009-08-06
> **cthlhu1987 said:**
> Hi, this is an absolute beginner question:
I wanna buy a new, bigger hd. How do I copy the whole content of the old hd absolutely 1 : 1 to the new? And how to resize the partitions without (or at least, with a minimal) risk of data loss (I have an ext3-partition for Linux, NTFS for Windoze XP and a bigger FAT32 for Data)? Is there a program to do it more or less easy and without or with a minimal risk? thx in advance for the answers.You could copy everything to an external HD and after you have the new HDD in,copy it all back to the new HDD.

---

### Post by mapes12 on 2009-08-06
> **wizard10000 said:**
> The absolute easiest way?  Takes a little time but it works.

Install the new hard drive and assuming your old hard drive is sda and the new one is sdb, you'd open a terminal window and type this -

```
sudo dd if=/dev/sda of=/dev/sdb
```

which will make an identical copy of the hard drive.  You can then use gparted or something similar to resize partitions pretty much however you like.  Took me about 30 minutes for a 36gb drive and you can speed it up with command line switches so maybe someone else can help with that.

Another option is to burn a g4l live CD and do a raw copy with that - but all it is is a pretty GUI to the same terminal command.

But - make darn sure you have the source and target drives right.

Good luck -So, on my system I have:
> mark@ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f247f24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        3206    25752163+  83  Linux
/dev/sda3            3207        9325    49150867+  83  Linux
/dev/sda4            9326        9729     3245130   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bfd1bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326   83  Linuxwhere sdb1 is used for backups.

Would I be correct to assume that to back "/" on sda2 the command would be: ```
sudo dd if=/dev/sda2/ of=/dev/sdb1
```:confused:

---

### Post by wizard10000 on 2009-08-06
> **mapes12 said:**
> So, on my system I have:
where sdb1 is used for backups.

Would I be correct to assume that to back "/" on sda2 the command would be: ```
sudo dd if=/dev/sda2/ of=/dev/sdb1
```:confused:

Yes, if / is on sda2  :)

But - it'll replace sdb1 with an exact copy of sda2 - including partition size.

If you want to make an exact copy of the entire drive you'd do 

```
sudo dd if=/dev/sda of=/dev/sdb
```

---

### Post by mapes12 on 2009-08-06
> **wizard10000 said:**
> Yes, if / is on sda2  :)

But - it'll replace sdb1 with an exact copy of sda2 - including partition size.

If you want to make an exact copy of the entire drive you'd do 

```
sudo dd if=/dev/sda of=/dev/sdb
```**Cool!** I've been messing around for ages with all kinds of disk imaging apps and rolling stuff up into tar balls and all I needed was this simple CL to backup one HDD to another. I'll have a play around with my test machine which I use to break things then see how to fix it again.

So, to restore I would need ```
sudo dd if=/dev/sdb of=/dev/sda

```i.e. just switching the drives in the command?

---

### Post by wizard10000 on 2009-08-07
> **mapes12 said:**
> **Cool!**So, to restore I would need ```
sudo dd if=/dev/sdb of=/dev/sda
```i.e. just switching the drives in the command?

Yup.

dd isn't a real good backup solution if that's what you're trying to accomplish.  I use rsync and just back up /home, /etc, /boot/grub and /var/cache/apt/archives to an external drive.  Runs as a cron job at 4am and hasn't failed me yet  :)

When I clean installed Jaunty on a new machine it took me less than an hour to install, reinstall all my apps and get everything reconfigured.

---

### Post by mapes12 on 2009-08-07
OK, I've given this copy to another HDD a go on my test system

In the machine I only had one 20GB HDD attached to the IDE1 channel. Got my hands on another bare drive and installed it but configured the cables as follows:

Original sda now connected to IDE2 (which is now reported in fdisk as sdb)
New HDD connected to IDE1 (which is now reported in fdisk as sda)

Booted into realtime Ubu. Called up Terminal and entered ```
sudo dd if=/dev/sdb of=/dev/sda
``` to copy over my original disk onto the new one. About an hour later and lots of HDD noise the job appeared complete. So, went into Terminal and sudo fdisk -l reports this:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ce1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2491    20008926    5  Extended
/dev/sda5               1         701     5630719+  83  Linux
/dev/sda6             702        2371    13414243+  83  Linux
/dev/sda7            2372        2491      963868+  82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20496740352 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ce1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2491    20008926    5  Extended
/dev/sdb5               1         701     5630719+  83  Linux
/dev/sdb6             702        2371    13414243+  83  Linux
/dev/sdb7            2372        2491      963868+  82  Linux swap / Solaris
mark@test-ubuntu:~$Looks to me like everyhing is going to plan including boot flag in sda copied over OK.

Then, rebooted and changed BIOS to boot from the new sda drive. But it doesn't. It hangs around a while then decides to boot from sdb i.e. the original drive. Do I need to reinstall GRUB into sdb to make this work please?

---

### Post by Paddy Landau on 2009-08-07
Post the contents of /etc/fstab.

---

### Post by wizard10000 on 2009-08-07
> **Paddy Landau said:**
> Post the contents of /etc/fstab.

I'm thinking two partitions with the same UID.

Or, two partitions in the same machine with the boot flag set.

The clone you made was a raw hardware sector copy of the first hard drive - it'd take mbr, boot flag, UID, deleted files, everything.  Some PCs don't handle a boot flag on more than one partition very well.

---

### Post by Paddy Landau on 2009-08-07
> **wizard10000 said:**
> I'm thinking two partitions with the same UID.
Good point.

Post the results of both of the following commands.
```
cat /etc/fstab
sudo blkid
```

---

### Post by mapes12 on 2009-08-07
> **wizard10000 said:**
> I'm thinking two partitions with the same UID.

Or, two partitions in the same machine with the boot flag set.

The clone you made was a raw hardware sector copy of the first hard drive - it'd take mbr, boot flag, UID, deleted files, everything.  Some PCs don't handle a boot flag on more than one partition very well.**YOU GOT IT!** I powered down then disconnected the IDE cable on sdb (the old drive). Plugged it all back in again. Rebooted and the new drive (sda) has booted faultlessly into Ubu. Perfect. Excellent copy of my old drive with loads more space for more trickery to come! Here's my fdisk -l to confirm all went well:> mark@test-ubuntu:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ce1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2491    20008926    5  Extended
/dev/sda5               1         701     5630719+  83  Linux
/dev/sda6             702        2371    13414243+  83  Linux
/dev/sda7            2372        2491      963868+  82  Linux swap / Solaris
mark@test-ubuntu:~$ :lol:

OK. So now I'll plug in sdb after another power down, boot from a live cd and format it for extra storage. Should be there then.............Great info. Thanks guys!

EDIT: Did the power down. Plugged back in sdb (formerly the origanl HDD) Booted with a GParted Live CD. Deleted all the previous partitions on sdb. Formatted the whole drive to ext3  with extended then logical (cos might need more partitions later) for storage. Restarted and took out the GParted Live CD. The machine booted again from the new sda (copied from sdb a few posts ago). Everything works perfect and here is my new fdisk -l with the extra space from the now formatted sdb (old sda):
> mark@test-ubuntu:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ce1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2491    20008926    5  Extended
/dev/sda5               1         701     5630719+  83  Linux
/dev/sda6             702        2371    13414243+  83  Linux
/dev/sda7            2372        2491      963868+  82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20496740352 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ce1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2491    20008926    5  Extended
/dev/sdb5               1        2491    20008894+  83  Linux
mark@test-ubuntu:~$ 

---

### Post by Paddy Landau on 2009-08-08
Glad you got it solved.

Please mark your first post's title with [Solved] for other people who searching for the same issue.

---

### Post by starcannon on 2009-08-08
I'd probably do a fresh clean install myself, then I'd just dump the contents of /home onto the new drive. /shrug but dd will do it as well.

---

### Post by colau on 2009-08-16
> **cthlhu1987 said:**
> Hi, this is an absolute beginner question:
I wanna buy a new, bigger hd. How do I copy the whole content of the old hd absolutely 1 : 1 to the new? And how to resize the partitions without (or at least, with a minimal) risk of data loss (I have an ext3-partition for Linux, NTFS for Windoze XP and a bigger FAT32 for Data)? Is there a program to do it more or less easy and without or with a minimal risk? thx in advance for the answers.
I think,this will do the job:
```

sudo dd if=/dev/sda of=/dev/sdb
man dd

```

---

### Post by Kees-vw on 2009-08-26
> **wizard10000 said:**
> Yup.

dd isn't a real good backup solution if that's what you're trying to accomplish.  I use rsync and just back up /home, /etc, /boot/grub and /var/cache/apt/archives to an external drive.  Runs as a cron job at 4am and hasn't failed me yet  :)

When I clean installed Jaunty on a new machine it took me less than an hour to install, reinstall all my apps and get everything reconfigured.

Hi

I am looking for a way to copy my Ubuntu installation from one PC to another and stumbled accross this thread. I am interested in more information wrt the rsync method you described above. The two PC's differ in hadrware and i think it would be best to just copy my settings and apps from the old to new PC. It sounds like that is what would happen if i copy the directories mentioned above to an external HDD and then back to my new PC.

Could you please explain the method you used while upgrading to Jaunty, I tink this might work for me as well.

Thanks in advance.

---

