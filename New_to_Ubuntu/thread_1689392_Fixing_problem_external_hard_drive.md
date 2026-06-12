---
title: "Fixing problem external hard drive"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by duffers on 2011-02-16
Hi all,

I have a EXT3 formatted external hard drive which is used on a media player. Somehow Windows XP stopped recognising the drive one morning. I managed to fix this with EXT2FSD but now the drive is giving a false space reading, won't accept new files and crashes Windows when I try. I've tried to sort it with a fsck on Ubuntu but I know next to nothing about Linux so could anyone hold my hand and tell me what exactly I need to put on the command line? Even better, if anyone has a clue what's going on with the drive, I'd love to hear it.

Thanks,

---

### Post by Paqman on 2011-02-16
Ext2Fsd seems to be a bit of a work-in-progress. Wouldn't it just be easier to use NTFS? Both Linux and Windows can read and write to NTFS just fine.

---

### Post by duffers on 2011-02-16
I don't think EXT2FSD is to blame here. And yes, it would be easier but now the drive is almost full with files so I couldn't reformat it.

---

### Post by Keiran230 on 2011-02-18
EXT2FSD isn't all that stable yet, so as much as it'll be a pain, backing up files and reformatting is probably best. Also, although you can reformat using mkfs.ntfs, it's probably better to format it using Windows. I've never had an issue with mkfs.ntfs, but since NTFS is native to Windows, I let Windows do it.

There are known limitations to the Linux NTFS-3g driver, like the inability to read compressed or encrypted partitions, and no native support for NTFS file permissions. If you use NTFS, don't use BitLocker or any other full-partition encryption software, and don't check "compress this drive to save disk space" in the properties dialog of the drive. I've never had any issues with the Linux NTFS-3g driver other than this, which doesn't cause that much of an issue.

---

### Post by duffers on 2011-02-18
If I wasn't clear in my post, I just need walking through how to fix the drive with fsck. The drive in question is 1TB and as I don't have anything even near that to back up onto, it's not an option. If I can't fix it, I'd rather just leave it as it is.

---

