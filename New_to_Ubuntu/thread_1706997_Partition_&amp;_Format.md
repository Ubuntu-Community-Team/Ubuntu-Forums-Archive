---
title: "Partition &amp; Format"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by bluesz on 2011-03-14
I bought a new drive with big capacity (Hitachi 2T).

 There are several ways for me to partition and format it:

 1) Windows disk management
 2) Win XP OS CD 
 3) Gparted

  1) is definitely slowest 

  2) is faster but still takes 30 min for 200G

  3) is very fast in less than 1 min

  However, my question is how reliable for Gparted with such partition and format operation? 

  Here, I just want NTFS. 

  Thanks

---

### Post by jerome1232 on 2011-03-14
I am certainly not a file-system expert but I would personally use Windows 7 to format the partition to NTFS. If there are any new features in NTFS than Win 7 would be the most likely OS to support the newest, latest, and greatest features of NTFS.

Just my opinion.

---

### Post by Jerry N on 2011-03-14
> **bluesz said:**
>   However, my question is how reliable for Gparted with such partition and format operation? 

  Here, I just want NTFS. 

  Thanks

I have used gparted to create and format NTFS partitions many times and have never had any problem with it at all.  If I am setting up a drive for dual boot, I **always** always use gparted to get the partitions the way I want them, including partitions that will have Win 7, Win XP, or Win2000 installed.  My opinion:  Use gparted with confidence.



Jerry

---

### Post by coffeecat on 2011-03-14
> **bluesz said:**
> 1) Windows disk management
 2) Win XP OS CD 
 3) Gparted

  1) is definitely slowest 

  2) is faster but still takes 30 min for 200G

  3) is very fast in less than 1 min

If Windows is taking that long, it's zeroing the whole partition. Which is a complete waste of time. From what I can remember in Windows you have a "quick format" option which omits the zeroing. Gparted doesn't bother with the zeroing.

I use Gparted for almost everything, including formatting NTFS partitions. I used Gparted to create a 100GB drive to install Windows 7 to, and Windows 7 is working quite happily on the Gparted created partition. Ditto with NTFS data partitions. I agree with Jerry N; use Gparted with confidence.

In fact there are special circumstances where you should avoid using the XP installer to format NTFS partitions - that is if you want an uncorrupted partition table - but that's another story. :-s

**EDIT**: is that an 'advanced format' drive? If so, use the Maverick version of Gparted, not the Lucid one. I'm fairly sure that will be OK.

---

### Post by jerome1232 on 2011-03-14
I think my post was misunderstood, I agree you can use gparted with confidence. But...

I wouldn't expect gparted to _always_ be as current as the newest release of Windows with Microsoft's very own pet file-system. I remember when Win 7 first came out they changed something about the new ntfs volumes that were formated under Win7 and gparted was sometimes failing to re-size NTFS volumes.

I was simply stating that if I were to choose the best route, it would be the most up-to-date recent version of Windows, it is after all their file-system.

---

### Post by coffeecat on 2011-03-14
> **jerome1232 said:**
> I wouldn't expect gparted to _always_ be as current as the newest release of Windows with Microsoft's very own pet file-system. I remember when Win 7 first came out they changed something about the new ntfs volumes that were formated under Win7 and gparted was sometimes failing to re-size NTFS volumes.

Yes, you are quite right and that is one exception I would make. I would indeed use Vista's or Win 7's Disk Management to resize a Windows Vista or 7 C: partition simply to be cautious. There have been problems, but I don't think that's anything to do with the NTFS fileystem that Gparted creates or resizes. I can't remember the exact details, but it's something to do with the sloppy way Windows identifies where the boot files reside. Resize the partition with older versions of Gparted and it "forgets" where they are and then can't boot up. I don't think this is a problem with XP though. And I believe, but am not 100% sure, that later versions of Gparted can deal with this.

---

### Post by RedRat on 2011-03-14
The one that takes the longest is called a low level format. This is useful if you want to insure that your disk is cleaned of all data (although, real forensic experts can recover data even from such a zeroed disk). This basically lays down a new track set. The other formatters merely go through and zero out the file system and journal. If you disk is fresh from the factory, go with gparted or Windows. The suggestion that Windows7 should have the latest and greatest for NTFS is probably true, maybe, who knows.

---

### Post by srs5694 on 2011-03-15
> **coffeecat said:**
> If Windows is taking that long, it's zeroing the whole partition. Which is a complete waste of time. From what I can remember in Windows you have a "quick format" option which omits the zeroing. Gparted doesn't bother with the zeroing.

This analysis is probably correct, although there could conceivably be other explanations (see below)....

> **EDIT**: is that an 'advanced format' drive? If so, use the Maverick version of Gparted, not the Lucid one. I'm fairly sure that will be OK.

Advanced Format drives require proper alignment, which is the core of coffeecat's suggestion. I wrote [an article on this topic](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) a while ago that provides more details -- but note that the advice on partitioning tools is a bit outdated, since some of them have changed since then. In any event, I didn't report the data in that article, but I did find that filesystem creation times varied substantially for some filesystems. Thus, a misaligned partition could conceivably result in sluggish filesystem creation times.

That said, Windows Vista and later create partitions aligned to 2048-sector boundaries by default, which is correct for these drives *unless* you set the "XP compatibility" jumper. If you use Windows XP or earlier, you're likely to get improperly aligned partitions unless you set the jumper -- and if you set the jumper, chances are only the first partition will be properly aligned. Confused yet? ;) My advice: *Do not* set the XP compatibility jumper and use Windows Vista, Windows 7, or a Linux utility that enables you to set 1 MiB alignment to do the partitioning. Then check the partitioning (using "sudo fdisk -lu /dev/whatever") and be sure that every primary and logical partition begins on a sector value that's a multiple of 8. Don't worry about extended partitions; they contain other logical partitions, rather than filesystems, so they aren't an issue.

Another point: There is something to be said for a filesystem creation operation that zeroes out the whole disk. On previously used disks, this will erase old data, which could confuse subsequent data recovery efforts, should they become necessary down the road. On a new disk, zeroing everything out will force the drive to write and read the vast majority of its sectors. Thus, any manufacturing defect will be discovered early. If you run a SMART utility on the disk after you create your filesystem, you'll be able to see if it's detected any serious problems. Since most electronics devices, including hard disks, fail either very early in their lives or very late in their lives, doing an early check like this can make sense if you intend to store important data on the drive.

[quote=RedRat]The one that takes the longest is called a low level format. This is  useful if you want to insure that your disk is cleaned of all data  (although, real forensic experts can recover data even from such a  zeroed disk). This basically lays down a new track set. The other  formatters merely go through and zero out the file system and journal.[/quote]

There are a couple of things wrong with these claims. First, low-level formats involve creating new low-level data structures that define the disk's tracks and sectors. Such formatting is possible on floppy disks and on *very* old hard disks, but modern hard disks are low-level formatted at the factory. It's not possible for end users to perform low-level formats on modern hard disks; the firmware simply lacks the functionality. What modern disk utilities mean whey they refer to "formatting" a hard disk is creating a filesystem (aka a high-level format). Whether or not that process writes 0 values to all the sectors doesn't change its nature as a high-level format.

Second, the claim that it's possible to recover data from a disk that's been zeroed out is suspect at best. I've seen claims from experts that it's *theoretically* possible to do this, given the right hardware. It's quite a leap from a theoretical possibility to a practical possibility to do something, though. There's also the issue of the hardware -- you might need to replace the disk's heads and firmware, or move the platters to a special rig. This would be ridiculously expensive. I have yet to see any company advertising a service to do this job, much less software that could do it. My suspicion is that it's either not a practical possibility or it's something that's only done in secret labs at the CIA, the NSA, or the like. If you've got a reference to a company that can do this commercially, even if it's very expensive, I'd love to hear about it. (Note that plenty of companies do offer data recovery, but AFAIK they just recover data that's been deleted in a non-destructive manner, like an ordinary "rm" operation under Linux.)

---

### Post by coffeecat on 2011-03-15
> **srs5694 said:**
> 
Another point: There is something to be said for a filesystem creation operation that zeroes out the whole disk. On previously used disks, this will erase old data, which could confuse subsequent data recovery efforts, should they become necessary down the road. On a new disk, zeroing everything out will force the drive to write and read the vast majority of its sectors. Thus, any manufacturing defect will be discovered early. If you run a SMART utility on the disk after you create your filesystem, you'll be able to see if it's detected any serious problems. Since most electronics devices, including hard disks, fail either very early in their lives or very late in their lives, doing an early check like this can make sense if you intend to store important data on the drive.

Thanks for that clarification.

---

### Post by RedRat on 2011-03-15
[srs5694]("http://ubuntuforums.org/member.php?u=1032238")
Thanks for clarifying the HD formatting in modern hard drives. That was very informative.

---

### Post by Paqman on 2011-03-15
> **srs5694 said:**
> 
Second, the claim that it's possible to recover data from a disk that's been zeroed out is suspect at best. I've seen claims from experts that it's *theoretically* possible to do this, given the right hardware. It's quite a leap from a theoretical possibility to a practical possibility to do something, though. There's also the issue of the hardware -- you might need to replace the disk's heads and firmware, or move the platters to a special rig. This would be ridiculously expensive. I have yet to see any company advertising a service to do this job, much less software that could do it. My suspicion is that it's either not a practical possibility or it's something that's only done in secret labs at the CIA, the NSA, or the like. If you've got a reference to a company that can do this commercially, even if it's very expensive, I'd love to hear about it. (Note that plenty of companies do offer data recovery, but AFAIK they just recover data that's been deleted in a non-destructive manner, like an ordinary "rm" operation under Linux.)

AFAIK, even law enforcement just image the drive before doing forensics on the image using software tools. Messing about with the actual drive itself would risk rendering it inadmissible as evidence, so it's just not done. So if they aren't doing it, then you can bet commercial data recovery isn't either.

Maybe spooks do use scanning electron microscopes on hard drives, but I doubt it. Bottom line is that a single pass is going to mean your data is gone for good.

---

