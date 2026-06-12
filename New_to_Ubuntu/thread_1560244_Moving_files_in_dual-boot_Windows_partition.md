---
title: "Moving files in dual-boot Windows partition"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-08-24
I'm trying to repair a dual-booted windows install from Ubuntu by moving a backed up file back into the windows/system32 directory when the windows partition is mounted in Ubuntu.

When I try to copy the file into /system32 (either using nautilus or terminal) I get the message "cannot stat `/media/A69C21169C20E313/WINDOWS/system32/ntoskrnl.exe': Input/output error" or similar.

ntoskrnl is the file I'm trying to move.  I've tried using sudo command, opened the partition as administrator etc but no joy.  What does this mean?

---

### Post by TeoBigusGeekus on 2010-08-24
Bad sectors, damaged disk?
Run a fsck on the windows partition.

---

### Post by aquascrotum on 2010-08-24
How would I do that now?

---

### Post by jtarin on 2010-08-24
Depends on your version of Windows.

Resolution:

Generally this error means there is file system corruption. Try to rename, mv <filename> <new filename>, or list files to confirm that this error is occurring to all files in a particular directory. Once confirmed use the following steps to attempt to recover your filesystem.

1. First, if you are going to perform a filesystem check you need to ensure the filesystem is unmounted. If the file system is your root partition then you will need boot into rescue mode so you can check the filesystem while it is unmounted. See additional articles in the Knowledgebase regarding this.

2. To run a filesystem check, use the command e2fsck. For example, if you are getting the above error on a filesystem that is mounted on the partition /dev/hda4 run the following command:```
e2fsck /dev/hda4
```3. If the above command returns with errors complaining about a "bad superblock" then run the following command:```
dumpe2fs /dev/hda4
```Look for the Backup superblock in the output:```
[Group 1: (Blocks 8193-16384)
Backup superblock at 8193, Group descriptors at 8194-8194
Block bitmap at 8195 (+2), Inode bitmap at 8196 (+3)
Inode table at 8197-8447 (+4)
7937 free blocks, 2008 free inodes, 0 directories
```4. Now run e2fsck again, specifying the superblock number:```
e2fsck -b 8193 /dev/hda4
```5. If this fails then reboot your system as a filesystem check will probably be forced. If you drop to a shell then run e2fsck on the partition that is reporting the errors.

---

