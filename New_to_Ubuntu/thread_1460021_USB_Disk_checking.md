---
title: "USB Disk checking"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by javadog on 2010-04-22
Hi All

I have an external drive that I would like to check for bad clusters etc. I have formatted it, it is an old 40GB IDE, it is running in an external casing. I have formated it as a FAT 32 disk and want to put it back into an old machine that will run basic tasks on it and dare I say Windows XP (please don't slam me, its for a buddy and they don't want Linux for some reason)  

I have looked at FSCK as well as BADBLOCKS, but not sure how to get on the drive. I also ran the file check in System>Admin>Disk Utility. I just need to make sure that the drive is not corrupt. 

I am running 9.10.

Thanks

---

### Post by QLee on 2010-04-22
[QUOTE=javadog]I have an external drive that I would like to check for bad clusters etc. I have formatted it, it is an old 40GB IDE, it is running in an external casing. I have formated it as a FAT 32 disk and want to put it back into an old machine that will run basic tasks on it and dare I say Windows XP (please don't slam me, its for a buddy and they don't want Linux for some reason)  [/QUOTE]

I don't see any reason to slam you for someone else's choice, in fact, I don't see any reason to slam them for choosing to use something they are comfortable with.

They will probably have a better experience if you use NTFS for the XP install, I think the installer would probably default to that anyway. In addition, I suggest it would be best to let the operating system that you are going to use format the disk, as it will when installing.

[QUOTE=javadog]I have looked at FSCK as well as BADBLOCKS, but not sure how to get on the drive. I also ran the file check in System>Admin>Disk Utility. I just need to make sure that the drive is not corrupt. 

I am running 9.10.[/QUOTE]

Well, I suppose you could use mkfs with the -c switch to check badblocks and format as a way to check the device if you don't understand the badblocks command. On the other hand, the major HDD manufacturers have downloadable check programs for the specific brand of drive, that would probably be the best test.

---

### Post by Drenriza on 2010-04-22
Do you know how your drive is seen by the OS?
 
example
```
/dev/hda
```
 
if you arnt sure. Connect your drive to your pc and do an
```
dmesg |less
```
in the terminal, and copy plaste the output here.
 
To copy from the terminal, mark what you want to copy with your mouse
ctrl + shift + c
 
and ctrl + v to place it here on the forum.
 
commands to run fsck and badblocks, that automaticly correct errors
examples
```
fsck fat32 -fn /dev/hda1
```
```
badblocks -n /dev/hdb
```

---

### Post by QLee on 2010-04-22
[QUOTE=Drenriza]Do you know how your drive in mounted?
 [/QUOTE]

Huh? You seem to be suggesting running a filesystem check on a mounted drive?

In this particular case it can't hurt anything because the drive is empty but I hope inexperienced users don't get the idea it is recommended to run filesystem check on mounted filesystems.

---

### Post by Drenriza on 2010-04-22
> **QLee said:**
> Huh? You seem to be suggesting running a filesystem check on a mounted drive?
 
In this particular case it can't hurt anything because the drive is empty but I hope inexperienced users don't get the idea it is recommended to run filesystem check on mounted filesystems.
 
 
You need to tell the system, on what device to make the fsck. Theirfore you need to know how the filesystem "see" the device.
i never sayd he should mount anything.
 
I would find it hard just to run
```
fsck FAT32 -fa /dev
```
 
I never sayd he should do
```
mount /dev/hda1 /dev/whatever
```
 
Also by looking at the commands ive written Qlee. you should be able to see that their arnt any mount commands.
Or suggestions to mount the drives. But ive edited the first line, to something else. in #3

---

### Post by QLee on 2010-04-23
[QUOTE=Drenriza] But ive edited the first line, to something else. in #3[/QUOTE]

Yes, you did, you changed history and edited the word mount from your post. Next time you might choose a better word for the designation, how the system "sees" the partition. It's only mounted when it is mounted.

---

### Post by Drenriza on 2010-04-23
> **QLee said:**
> Yes, you did, you changed history and edited the word mount from your post. Next time you might choose a betted word for the designation, how the system "sees" the partition. It's only mounted when it is mounted.
 
Qlee take and relax. And get the stick out of your a.. that makes you so cranky.

---

