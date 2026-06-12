---
title: "Hard disks"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Martin_sensei on 2010-06-09
Hello!

I am having a bit of trouble with my hard disk configuration as the devices are not appearing as expected.

I have 3 160GB hard disks:

Disk A, attached to SATA1 - Windows, Linux and Swap partitions
Disk B, attached to SATA2 - Data partition
Disk C, attached to SATA3 - Backup partition

When I look int he disk Utility I see:

/dev/sda1 - Backup

/dev/sdb1 (system reserved)
/dev/sdb2 (Windows)
/dev/sdb3 
/dev/sdb5 (Linux)
/dev/sbd6 (Swap)

/dev/sdc1 - Data

I read in the Linux docs that sda = SATA1, sdb = SATA2 ...
So, I was wondering if anyone could explain why these drives don't map as expected?

This messes up my mounted drives when I remove the backup drive, as the mappings all seem to change.

Any ideas?

Many thanks

Martin

---

### Post by lisati on 2010-06-09
Have a look [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). If you have any further questions, feel free to ask.

---

### Post by Martin_sensei on 2010-06-09
Hello again,

Yes, this is the sort of documentation I have read though (although I read the official Ubuntu wiki version),

So, the pages you reference also seem to state that sda is the first SATA device, so I still don't understand why the last drive I connected, attached to SATA3 is appearing as sda1...

---

### Post by louieb on 2010-06-09
Just a Guess - boot order plays a role in the sd@ designation.  Perhaps sata3 is 1st in the boot order -  that would make sata3 show up as sda1 - Check the BIOS setup.

---

### Post by Martin_sensei on 2010-06-09
> **louieb said:**
> Just a Guess - boot order plays a role in the sd@ designation.  Perhaps sata3 is 1st in the boot order -  that would make sata3 show up as sda1 - Check the BIOS setup.

Is that right? That may explain it then.  I did try moving the first boot device to be the last one, however than caused grub to fail, and rendered the machine unusable.

Is there not a way to dictate the sd@ designation rather that let it change.   It does mess me up when the backup drive is removed...

---

### Post by Mark Phelps on 2010-06-09
> **Martin_sensei said:**
> Is that right? That may explain it then.  I did try moving the first boot device to be the last one, however than caused grub to fail, and rendered the machine unusable.
You will note that with GRUB2, the config file it creates embeds the drive sequence in the boot stanzas.  So, if you move drives after you generate that file, you most likely won't be able to boot using GRUB until you regen that file.

> Is there not a way to dictate the sd@ designation rather that let it change...
Don't know about designating sda numbers -- believe that is done automatically.

---

### Post by srs5694 on 2010-06-09
The simplest workaround is probably to use UUIDs or disk labels instead of /dev/sd*xn* designations. You can do this in /etc/fstab, and I believe also in GRUB configuration files.

---

### Post by The Cog on 2010-06-09
I have read that the disk name allocation is done at boot time and is not guaranteed to happen in the same order every boot. So I would say that identifying drives by UUID (or LABEL) is the way to go. The installer should have used the UUID notation automatically, I thought.

---

### Post by louieb on 2010-06-09
Just a note about uuid and labels. Both can be used to identify a partition - even if the boot order changes. Ubuntu started using the uuid with v 6.10 - partly to get around problems when adding and removing hard drives.  Both work great when used in /etc/fstab  for mounting partitions.   (/etc/fstab is set up to use uuid  when Ubuntu is installed). 

The version of GRUB used by Ubuntu - has been modified to use the UUID to - I've seen far fewer GRUB problems reported in the forum since that change. But GRUB will have problems if the 1st drive in the boot order changes -       

> Is there not a way to dictate the sd@ designation rather that let it  change.

As far as I know - boot order is it.   UUID and labels apply to partitions only - not hard drives. 

It sounds like your backup (sata3) drive was 1st in the boot order when Ubuntu was installed.  -  GRUB code was put in the MBR of sata3 to load the GRUB program on sata1.

What you could do is change the boot order in BIOS so that sata1 is 1st in the boot order - then boot with the live CD and change  the MBR of sata1 to load GRUB. [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")  - 

By doing that you should be able to remove the backup and/or the data drive   and the PC would still boot normally.

---

### Post by oldfred on 2010-06-10
My drive order is the SATA port they are plugged into. Check port numbers on your motherboard.

I do note that since I boot sdc, that grub makes me chainboot to sda by using hd1 where sda is normally hd0, So for grub boot order redfines drive order, but no matter which drive/system I boot the sda, sdb, sdc is still the same.

---

### Post by bab1 on 2010-06-10
The /dev/s?? designation is determined by the order the partition is discovered (enumerated).  These can (and very often do) change the designation relative to the partition on the physical device.  There never is a need to ID the physical device as you only mount partitions.

UUID's are embedded information on the partition The UUID is created when the partition is formated with file system (mk2fs).  Think of the UUID as metadata.  To see the UUID's you can use the following command from the CLI```
sudo blkid -l
```

Partition labels can be created with the information supplied [**_here  _**]("http://www.cyberciti.biz/faq/linux-partition-howto-set-labels/").  These labels can be made or changed at any time after the file system is created.

Either way (UUID or Label), the partition should be referenced by a non-changing identifier.

---

### Post by srs5694 on 2010-06-10
> **louieb said:**
>   UUID and labels apply to partitions only - not hard drives.

AFAIK, this as yet has no practical implications in Linux, but the GUID Partition Table (GPT) partitioning system uses UUIDs (well, GUIDs, but they're basically the same thing) to identify disks, as well as partitions. It's conceivable that some future boot loader will enable selecting disks by GPT GUID, but AFAIK GRUB doesn't have such support today.

Also, in the more common Master Boot Record system, UUIDs apply to *filesystems,* not to *partitions.* For most practical purposes this distinction is unimportant, but there can be issues in some cases. For instance, if you do a low-level copy of a filesystem from one partition to another, the filesystems will both have the same UUID number, even if they're on different partitions (with different GUIDs, in the case of a GPT disk). This will likely result in confusion, since AFAIK Linux's ability to mount filesystems by UUID works on the filesystem UUID and ignores the partition's GUID (on GPT disks).

---

### Post by louieb on 2010-06-11
> **srs5694 said:**
>  in the more common Master Boot Record system, UUIDs apply to *filesystems,* not to *partitions.* 

Interesting - So a newly created partition on a hdd with an ms-dos partition table  would not have a UUID until it get formatted with some file-system. - Had not though about that.  I had noticed that when cloning a partition the UUID is duplicated too.

---

### Post by srs5694 on 2010-06-11
> **louieb said:**
> Interesting - So a newly created partition on a hdd with an ms-dos partition table  would not have a UUID until it get formatted with some file-system. - Had not though about that.  I had noticed that when cloning a partition the UUID is duplicated too.

Correct. In fact, many (mostly older) filesystems don't have UUIDs, although most do have some sort of ID code that can be used in its place with the "UUID=" label to mount or in /etc/fstab. A UUID is a 128-bit number that's written with a specific form, as described on the [Wikipedia page for UUID](http://en.wikipedia.org/wiki/Uuid) (see also the [Wikipedia page for GUID](http://en.wikipedia.org/wiki/Guid)).

---

