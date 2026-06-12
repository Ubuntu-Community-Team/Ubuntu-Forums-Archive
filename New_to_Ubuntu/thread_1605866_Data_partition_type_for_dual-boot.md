---
title: "Data partition type for dual-boot"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by japhyr on 2010-10-25
Hello,

I have been using ubuntu for a couple years now, but I am about to make my first dual-boot setup.  I have read numerous guides and tutorials, but have a couple questions before committing to the process.

I have separate /home and /data partitions on my ubuntu machine, to make upgrades easier.  I have been using ext4 for these partitions.  Now it seems I need to use ntfs for the data partition so the windows os will be able to access the data partition.  Is this correct, that my newly-configured data partition must be ntfs?

My external backup drive is still ext4.  Will I be able to restore my data and configuration files from that drive once I have 10.04 reinstalled?

---

### Post by beew on 2010-10-25
Don't know about ext4 but ext3 is supposedly ok if you install this in Windows
[URL="http://www.fs-driver.org/"]http://www.fs-driver.org/
[/URL]
it is called ext2 for windows but it works for ext3 as well according to the FAQ

---

### Post by oldfred on 2010-10-25
I originally used FAT32 4 years ago, but then found the 4GB limit destroyed some files I thought I had saved, so I converted to NTFS. Not had any issues with Ubuntu and XP. I have Firefox & Thunderbird profiles plus some misc data in my NTFS partition. Most of my data now is in my ext3 or ext4 partitions.

I do not like having foreign systems write directly into system partitions, so I try to make my system partition small and data partition large. I only write into my window system partition from Ubuntu, when I have to do repairs or occasionally to read data, and never use windows to write into ext partitions.

---

### Post by ArgusVision on 2010-10-25
If you plan to use both systems to access the data, then definatly NTFS.

---

### Post by japhyr on 2010-10-25
From what people are saying, I am leaning towards using NTFS for the data partition as well.

Will I be able to copy my backed up data from my ext4 hard drive directly to my new ntfs data partition?

Will I need to reformat my external hard drive to ntfs for future backups?

---

### Post by oldfred on 2010-10-25
It depends on what you want to backup. NTFS does not support Linux file permissions & ownership. So you cannot backup any system related or /home files to NTFS without losing ownership or permissions. But anything that is data can easily be backed up to NTFS.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
**Ownership and permissions of vfat / ntfs are set at the time of mounting**. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ArgusVision on 2010-10-25
> **japhyr said:**
> 
Will I be able to copy my backed up data from my ext4 hard drive directly to my new ntfs data partition? 

Yes. After you mount it.

> **japhyr said:**
> 
Will I need to reformat my external hard drive to ntfs for future backups?

What format is it? If it's FAT32 then maybe. Dynamic links aren't supported in FAT32.

---

### Post by srs5694 on 2010-10-26
> **oldfred said:**
> It depends on what you want to backup. NTFS does not support Linux file permissions & ownership. So you cannot backup any system related or /home files to NTFS without losing ownership or permissions.

That's true of direct file-to-file backups using cp, rsync, or the like; however, it's possible to back up ext2/3/4 (or any other Linux-native filesystem) to NTFS by employing a carrier of some sort, such as using tar to back up the files to a tarball. This makes it slower and less convenient to see what's in the backup and to restore individual files, but it's a good way to preserve Unix/Linux-style filesystem features on a non-Unix/Linux filesystem. You can also apply compression to a tarball, enabling a smaller drive to completely back up a larger one. (Compression doesn't work well for some very large files, such as MPEG files, though.)

---

### Post by japhyr on 2010-10-26
> **ArgusVision said:**
> What format is it? If it's FAT32 then maybe. Dynamic links aren't supported in FAT32.

The external drive is currently formatted as ext4.  Will I have to reformat it to ntfs if I want to back up the new ntfs data partition to this external drive?  Or can you back up an ntfs partition to an ext4 drive?

---

### Post by ArgusVision on 2010-10-27
I don't believe it will be a problem. I haven't tried that while using a "backup" software. But I have copied files without any issue, so I don't see where it should cause any problems.

Sorry it took so long to respond. I'm trying to go back through threads I've responded to and close up any ones I may have left hanging...

---

