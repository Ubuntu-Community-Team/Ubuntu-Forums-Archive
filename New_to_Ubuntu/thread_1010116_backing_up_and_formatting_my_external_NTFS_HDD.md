---
title: "backing up and formatting my external NTFS HDD"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by transkinetic on 2008-12-13
I have an external HDD formatted as NTFS. It has some music on it. I want to format it to fat32 so that I may use it easily with both Ubuntu and Windows and Osx. I also want to keep my music.

I want to partition off the music part and then format the rest of the drive to fat32, then copy the music from the reduced NTFS partition on to the new fat 32 partition, then expand the fat32 partition to fill the disk.

Is that the best way to go about this?

I'm really not sure about partitioning. I looked at the guides but there was so much information there that it was a little over my head.

Can anyone help me?

---

### Post by transkinetic on 2008-12-13
So I found this neat GUI program called G-Parted and totally installed that. Woe is me, it doesn't let me add a new partition to my external drive! It has some sort of error about can't read this file system. So odd that it cannot read the file system seeing as it mounts and I play my music in Xubuntu. Well, it will let me delete the partition but I do not wish to lose my music. I would copy my music to my internal HDD but it is far to small for that.

---

### Post by rlunger on 2008-12-13
If you don't have an excessive amount of space taken up by your music files, it might be easier to just back them up to another drive.  Then you could format your external one (as long as it's mounted) like so:

    sudo mkfs -t vfat /dev/your_device

Just interested, but why FAT32?  Does Osx not support NTFS?  I've found NTFS to be much better than the FAT32 filesystem.  You can get an installable ext2 file system for windows (google 'EXT2IFS') that can read ext2 file systems, if it would help with your decision.  If you choose ext2, format your external via:

    sudo mkfs -t ext2 -I 128 /dev/your_device

(The ext2 installable file system for Windows only works if the drive's inode size is 128.)

I suggest this because I didn't have much luck resizing my NTFS partition with GParted.

Good luck.

-Ryan

---

### Post by rlunger on 2008-12-13
> **transkinetic said:**
>  I would copy my music to my internal HDD but it is far to small for that.

Sorry, didn't read that part!

---

### Post by albinootje on 2008-12-13
Can you tell us the exact error message ?

And to resize with gparted i think the partition you want to resize needs to be unmounted!
Also resizing needs a certain amount of free disk space to work with during the resizing.

---

### Post by transkinetic on 2008-12-13
Size: 465 GB, Used: 33 GB
To paraphrase the error,
"This filesystem could not be read; some operations may not be available."

I'm preparing to install 8.1, will that support NTFS? The main reason I was avoiding NTFS was that I wanted compatability with Ubuntu...right now it mounts it as read-only.

---

### Post by albinootje on 2008-12-13
Since quite some time support for NTFS in Linux has been fine. 
Before that the NTFS-support in Linux was labeled too experimental, and would mount read-only by default. 
But that's years ago.

Now with the ntfs-3g project software in Ubuntu it should mount ntfs-partitions as read/write by default, unless a ntfs-partition is labeled "dirty", in that case it will be mounted read-only to prevent problems.

You can do the following :
1) Use your external disk on some MS-Windows machine, and use "safely remove device".
2) Install ntfsprogs in Ubuntu, and use ntfsfix.
3) Use the ntfs-3g force option when you mount the ntfs-partition.

But like i mentioned before, you probably need to unmount the ntfs-partition before gparted can start resizing it!

---

### Post by albinootje on 2008-12-13
And you have loads of free diskspace so resizing should not be a problem for that reason. :)

---

### Post by transkinetic on 2008-12-13
ntfsprogs with ntfs fix worked perfectly

Thanks for all the info albinootje and rlunger.

---

### Post by sneeks on 2008-12-13
this should not be a problem,so u are doing something wrong,i have a video at blip.tv on gparted,just give it a search mate.

---

