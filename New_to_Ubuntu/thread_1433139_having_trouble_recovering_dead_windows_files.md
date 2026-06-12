---
title: "having trouble recovering dead windows files"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Auspicious on 2010-03-18
Background:  First, the surge protector emitted a piercing shriek.  In the process of getting it quieted down, the computer tower got knocked around a bit (I had to pretty much climb over it to get to the surge protector.)  Then, my computer wouldn't boot up, but my husband was able to figure out that the computer wasn't finding the hard drive and this was a physical connection issue.  So he got the hard drive reconnected, and the computer found the hard drive and quit trying to boot from a CD, but Windows still won't boot up.  My Ubuntu (Hardy Heron) CD works just fine.

I don't care about Windows.  I am fine with wiping it and becoming an Ubuntu user.  What I want is to get some pictures out of Windows.

I tried this guide: 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

and this one:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-ii-getting-your-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-ii-getting-your-files/)

...but when I enter the stuff to force the thing to mount (and I'm frankly not sure just what that means,) my terminal says this:

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
Failed to sync device /dev/sda2: Input/output error
Failed to close volume /dev/sda2: Input/output error
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by GSF1200S on 2010-03-18
Here is a suggestion for you:

```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/sda2
```

```
sudo mount -t ntfs-3g /dev/sda2 /media/disk
```

This should in theory reset the logfile and grant you access to the ntfs partition. I should warn you though- when it has to do with power outages especially when the hard drive is writing data, the filesystem often time gets corrupted, etc. Let us know if this works or not :)

---

### Post by Daveski on 2010-03-18
This is a great page for all kinds of data recovery if you still can't mount your ntfs parition:

[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Auspicious on 2010-03-18
I got to here:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda2
Mounting volume... Error reading bootsector: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... Error reading bootsector: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.
ubuntu@ubuntu:~$ 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
So... how do I run chkdsk?  (Or should I try to mount again anyhow, or are my files just toast at this point?)

---

### Post by coffeecat on 2010-03-18
+1 for trying out ntfsfix. If you're running a live CD, ntfsprogs might already be available. The live CD partitioner has to be able to manipulate NTFS filesystems, so ntfsprogs is on the live CD, but strangely it doesn't get installed to a fresh HD installation.

Anyway, one word of caution. From man ntfs fix:

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.If ntfsfix doesn't make the NTFS partition readable, consider removing the drive, fitting it into a USB enclosure, attaching it to a Windows system (if you can get access to one) and running chkdsk. Sad fact of life is that you really need a Windows utility to repair a Windows filesystem on occasion.

**Edit:** you posted just before me. It looks as though a chkdsk is necessary.

---

### Post by srs5694 on 2010-03-18
I note that you mentioned, Auspicious, that you're using an Ubuntu *CD.* Is Ubuntu installed at all on your hard disk, or are you booting Ubuntu from CD exclusively and then accessing files on your hard disk? I suspect the latter. If so, the "input/output error" message you get when you run ntfsfix suggests that either your hard drive was not properly reconnected after the computer got banged around or the hard disk may have been physically damaged by the shock. If the latter, recovery of those files may not be possible from *any* OS. I hope that's not the case, but I think you should be aware of the possibility, and you should check the physical connectors to be sure they're firmly inserted. You may even want to try replacing the cables.

Stepping back, chances are the NTFS volume was left in an inconsistent state when power to the computer was cut. This sort of issue is always best handled by the filesystem's native recovery tools, which is why ntfsfix says to run CHKDSK (a Windows utility). Your Windows installation/recovery disc should be able to help with this, assuming the drive isn't physically damaged.

As a side note, you said you didn't know what "mount" meant in the context of disks. Mounting a disk means configuring it to make its files accessible to users. In Linux, this is done by using a directory as an access point -- for instance, a disk might be mounted as /media/myfiles, meaning that you'd go to /media/myfiles/foo.txt to read the file foo.txt on the disk. Note that even the base of the directory tree (/) is a mount point for Linux. In Windows, disks are given drive letters, such as C: and D:. Individual disks, or the partitions they contain, can be mounted or unmounted, so you can have a disk that's physically installed in the computer but inaccessible to users. You'd use a command called "mount" (or GUI interfaces to it) to mount the disk, and another called "umount" (that's typed correctly; there's only one "n") to make it inaccessible again. You can unmount a disk to protect its contents from accidental damage, to keep its contents away from prying eyes, or as a prerequisite to do certain low-level maintenance tasks on it.

---

### Post by Auspicious on 2010-03-18
Googling about, I wonder if it's not hopeless, or if I'm just in waaay over my head...

If I understand correctly, I can't run chkdsk because I can't load Windows?

Should I do this:
e2fsk /dev/sda2
?

---

### Post by Auspicious on 2010-03-18
srs5694... Yes, I am strictly working from the CD.  I can certainly have my husband recheck the connections.  And, I've been afraid of using the Vista installation disc because it says it will erase all data and files.  It doesn't say anything about boot or recovery.  And thank you for explaining mounting!

---

### Post by GSF1200S on 2010-03-18
> **Auspicious said:**
> Googling about, I wonder if it's not hopeless, or if I'm just in waaay over my head...

If I understand correctly, I can't run chkdsk because I can't load Windows?

Should I do this:
e2fsk /dev/sda2
?

No, thats for a EXT2/3/4 filesystem. That will not help you with windows NTFS filesystem. At this point, the best suggestion is to hook that drive up to a Windows computer. Linux cannot by license use all the tools that are property of Microsoft, so obviously its abilities are going to be limited (try fixing a Linux filesytem with a Windows install). Do you have another Windows box around? If so, connect this drive somehow. Whether its plugging the drive into the motherboard and powersupply of another computer running Windows, or putting the drive in a USB enclosure and connecting it that way, that is your best option. At this point, Im afraid you may very well have a corrupted drive. But, at least try and see if a native Windows install can fix it.

---

### Post by Daveski on 2010-03-18
No, all is probably not lost. If the pictures are important to you and you are willing to do some hard work learning a few tools, it is likely that you can recover most if not all of your pictures.

If the drive is spinning (and not making grinding noises ;-) ), and the fact that /dev/sda seems to be contactable, then recovery tools may be able to reconstruct many common file type - especially images.

Do not try loads of tools to try to repair the parition, the less changes you make the more chance of something like foremost or photorec working.

---

### Post by srs5694 on 2010-03-18
No, do *not* run e2fsck on a Windows (NTFS or FAT) partition! That's a tool for fixing problems with ext2, ext3, and ext4 filesystems, not Windows filesystems. I'm pretty sure it's smart enough to realize it's not looking at a Linux filesystem and will refuse to do anything bad to them, but there's no point in tempting fate.

As I wrote before, you should locate your Windows installation disc. If you can't find one, borrow one from a neighbor, friend, or colleague. It may not even need to be the same version of Windows as you've got, so long as it's fairly recent (Windows XP or later, but not Windows Me, say). The installation disc can spot disks that have been improperly shut down and can do repairs on them even if the system on the disk won't boot.

As I noted in my earlier post, the messages you posted included comments about input/output errors. You shouldn't see such messages even on filesystems that have been badly corrupted (damaged data); they should appear only if there's something physically wrong with the drive -- a loose or damaged cable or something more serious. Thus, you should check your cable connectors (try unplugging them and plugging them back in even if they *look* OK). OTOH, I'm not intimately familiar with the Linux NTFS code; it could be that it's using the term "input/output error" in a somewhat loose or misleading way.

---

### Post by srs5694 on 2010-03-18
> **Auspicious said:**
> srs5694... Yes, I am strictly working from the CD.  I can certainly have my husband recheck the connections.  And, I've been afraid of using the Vista installation disc because it says it will erase all data and files.  It doesn't say anything about boot or recovery.  And thank you for explaining mounting!

Your latest post hadn't appeared by the time I posted again, so sorry for repeating myself on a couple of points.

I'm not 100% familiar with what Vista's recovery/install disc does in all cases, but I believe that it differs somewhat from one recovery disc to another. By all means, don't do anything that sounds like it might trash the disk. Connecting the disk to another computer, as others have suggested, will certainly be safer in this respect, but also more work.

Another suggestion: Buy a new hard disk that's at least as big as the original, then use Linux tools to clone the current drive. This will do a couple of things. First, if the Linux tools report I/O errors when doing a simple drive clone, then you'll know that your original disk is misconnected or physically damaged. Second, it'll provide you with a backup you can use in case recovery attempts make matters worse. I recommend using a utility called ntfsclone to do the backup. This is a text-mode program; type "man ntfsclone" at a command prompt to read its documentation. It will back up only the sectors that are in use, which may help if there are a few bad sectors in areas of the disk that happen not to be used. OTOH, I'm not sure offhand if ntfsclone will back up a disk that's in an unclean state. If ntfsclone fails, you can use dd:

```

dd if=/dev/sda of=/mnt/backup/windows.img

```

This creates a copy of the entire first drive /dev/sda onto the windows.img file on the disk mounted at /mnt/backup. (You'll have to mount your backup drive there first, of course, and you may need to change the device filename (/dev/sda) for your system.) Such a backup will take a long time, though -- you may need to leave it running overnight, depending on disk speeds and size.

In all these cases, you'll need to prepare the new disk before you do anything else. The GParted program in your Ubuntu CD can do this. For the moment, you can just create one big ext3fs partition. Alternatively, you could install Ubuntu (or even Windows) to the new disk. That could simplify post-recovery cleanup, but it will also take up space, so if your new disk is only as big as the original, I wouldn't install an OS on the new disk.

Another thought: Even if you can't mount your drive, there are Linux tools that enable you to access files on an unmounted NTFS volume. See if ntfsls and ntfscat are present on your system. If so, read their man pages ("man ntfsls" and "man ntfscat"). These may be enough to let you retrieve the files that are important to you. I'm afraid I've never used these tools myself, though, so I can't offer much practical advice on how to use them.

Best of luck recovering your files!

---

### Post by Auspicious on 2010-03-27
I just wanted to come back and thank you all for sharing information with me!  We finally hired a pro to come in, and he couldn't get anywhere with the hard drive, so now it's sitting in the closet waiting for us to decide whether or not it's worth the money and effort to take to some sepcialty place to recover those files...

...the upshot is, I have a spiffy new hard drive, and this was the kick I needed to just install Ubuntu!  Installation was a breeze, internet's fine, so far, so good!  I'm just poking around the beginner stickies now...

---

