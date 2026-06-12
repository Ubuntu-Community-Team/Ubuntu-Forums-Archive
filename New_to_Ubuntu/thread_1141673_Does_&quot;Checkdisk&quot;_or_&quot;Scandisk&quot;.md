---
title: "Does &quot;Checkdisk&quot; or &quot;Scandisk&quot; exist in Ubuntu?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by drdave69 on 2009-04-28
I have almost fully switched both of my computers over to Ubuntu and am very happy with the experience. I have 1 drive that still has the ntfs on it. There seem to be errors on this drive. In windows I was able to run something called "Checkdisk" or "Scandisk" can't remember which, and it would check the disk for errors and automatically fix all errors & recover bad sectors of the disk. Is there an equivalent in Ubuntu? If so, can someone please tell me what it is called & how to use it.
Thank you in advance, Dave

---

### Post by SuperSonic4 on 2009-04-28
fsck would be the closest I can think of. However, it's not wise to run this command on a mounted filesystem so it's best to do it from a live cd or from recovery mode (I think). 

```
fsck /dev/sdXX
``` is the check I think (or you may use a mount point). **Please wait for confirmation on this.**

ext2/ext3/ext4 are all more stable than ntfs as a filesystem though so ubuntu does not need checking so much. fsck may be able to do ntfs but again, I'm not sure

```
man fsck
``` should tell you more

---

### Post by drdave69 on 2009-04-28
> **SuperSonic4 said:**
> fsck would be the closest I can think of. However, it's not wise to run this command on a mounted filesystem so it's best to do it from a live cd or from recovery mode (I think). 

```
fsck /dev/sdXX
``` is the check I think (or you may use a mount point). **Please wait for confirmation on this.**

ext2/ext3/ext4 are all more stable than ntfs as a filesystem though so ubuntu does not need checking so much. fsck may be able to do ntfs but again, I'm not sure

```
man fsck
``` should tell you more
Ok, waiting for confirmation.
I have movies on this (ntfs) drive, and I am trying to move said movies to another ext3 drive, so I can reformat the drive to ext3.

---

### Post by Saghaulor on 2009-04-28
Are you able to mount the parition? 

Keep in mind that I'm no expert, but.. .

If so, I wouldn't worry about the disk errors, just copy your files over and fritz the partition.


Before formating the ntfs partition, verify that your data has retained it's integrity, ie, the movies work, etc.

---

### Post by SuperSonic4 on 2009-04-28
If you're able to mount the drive I'd just move them over. If you're feeling lazy you can move the whole folder over

---

### Post by stchman on 2009-04-28
> **drdave69 said:**
> I have almost fully switched both of my computers over to Ubuntu and am very happy with the experience. I have 1 drive that still has the ntfs on it. There seem to be errors on this drive. In windows I was able to run something called "Checkdisk" or "Scandisk" can't remember which, and it would check the disk for errors and automatically fix all errors & recover bad sectors of the disk. Is there an equivalent in Ubuntu? If so, can someone please tell me what it is called & how to use it.
Thank you in advance, Dave

Ubuntu fsck runs approximately every 35 boots.  As far as NTFS volumes, sounds like you have unclean volumes.  You can use the ntfsprogs package.  It contains lots of NTFS tools.

---

### Post by Saghaulor on 2009-04-28
Honestly though, I would try to ditch the ntfs partitioning if you can. Too much hassle.

---

### Post by drdave69 on 2009-04-28
> **Saghaulor said:**
> Are you able to mount the parition? 

Keep in mind that I'm no expert, but.. .

If so, I wouldn't worry about the disk errors, just copy your files over and fritz the partition.


Before formating the ntfs partition, verify that your data has retained it's integrity, ie, the movies work, etc.
I am trying to move the files, but, I get errors while trying.

---

### Post by vgrisham on 2009-06-14
What kind of errors were you getting?

---

### Post by rykel on 2009-12-23
Hi,

I am trying to "Checkdisk"/"Scandisk"/fsck my external hard disks (one is fat32 and another is ntfs) too...

Although they can be mounted, but when I try to copy/move certain folders over to another partition, it would give errors.

I cannot remember the specifics, but I recall that it is something similar to "input/output error".

Any help here is much appreciated!!

Thanks.

---

### Post by justnice980 on 2010-02-03
> **rykel said:**
> Hi,

I am trying to "Checkdisk"/"Scandisk"/fsck my external hard disks (one is fat32 and another is ntfs) too...

Although they can be mounted, but when I try to copy/move certain folders over to another partition, it would give errors.

I cannot remember the specifics, but I recall that it is something similar to "input/output error".

Any help here is much appreciated!!

Thanks.

An I/O error generally means that the drive is either dead or dying. It cannot fully be read and should be replaced.

---

### Post by NCLI on 2010-02-03
@justnice980: Not necessarily. You can mount the drive in Ubuntu and use the built-in Disk Manager app to check how its health is.

---

### Post by Flimm on 2010-02-03
You can use "Disk Utility" to check the health of the hard disk. Gparted (GNOME Partition Editor) can also run filesystem checks on your partitions, just right-click on the partition, choose Unmount, right-click the partition, choose Check, and then click Apply.

---

### Post by bodhi.zazen on 2010-02-03
> **Saghaulor said:**
> Honestly though, I would try to ditch the ntfs partitioning if you can. Too much hassle.

If you are no longer running Windows you should convert to a linux native system such as ext4 or whatever you choose.

The reason is because the file system tools in Linux are not so good at fixing errors in ntfs partitions, often you need to boot to windows and fix the ntfs file system from windows.

With that said, there are many tools in Linux for working with your filesystems, everything from fsck to testdisk to smartmontools

[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

---

