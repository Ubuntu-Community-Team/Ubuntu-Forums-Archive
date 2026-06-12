---
title: "Creating the Equivalent of a Spanned Drive"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by c3ntury on 2011-07-21
I have a server hosted with OVH, with a fair amount of disk space (2 x 2TB drives). The server is running Ubuntu 11.04 with a custom kernel because the default one is a bit ... bizarre.

What I'm trying to achieve is the equivalent of a spanned drive, e.g, turning the 2 x 2TB drives into a single 4TB drive so that I can use use it to its full potential. 

Here's some screen-shots regarding the hard-drives :)

SSH information -
[img]http://imgf.tw/563440823.png[/img]

First Drive -
[IMG]http://www.imgftw.net/img/590937847.png[/IMG]

Second Drive -
[IMG]http://www.imgftw.net/img/226172580.png[/IMG]

Any ideas how I could create this kind of system?

Thanks and regards,
Cameron J Allan.

---

### Post by oldfred on 2011-07-21
If you are going over 2TiB then you have to convert to gpt fromMBR(msdos).

You may want to review LVM. I have not used it as it is another level of drive allocation, but I think it does exactly what you want.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)


GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

---

### Post by c3ntury on 2011-07-21
I'm actually somewhat of a Linux newbie.. :/

Is there a program which can say, do some of this process as I'm not comfortable with screwing up my server xD

---

### Post by anewguy on 2011-07-21
It sounds to me like you are talking about a RAID 0 striped set - using 2 devices as one.  I don't know what your experience with it might be, so please be aware of the following:

- a RAID 0 striped set, if 1 of the disks goes down, is normally not recoverable - remember the I/O's are spread across 2 volumes, treating them as 1 large volume

- if it was me (and it has been back when I was working), I would always set up a RAID 1 shadow array for redundancy - everything you do to the striped set is copied on the shadow array.  In this way if a disk died in your striped set you could put in a new drive and the shadowing would "refresh" the new drive without ever loosing data.  In my opinion, I would NEVER stripe without shadowing.

I don't know if your disk controller supports RAID.  If not, there is software RAID.  I've never tried software RAID in Linux.  I also don't know if there is any limit imposed on the size of a striped and/or shadowed set in Linux either (i.e., 2 - 2tb drives striped to a single 4tb drive - I just don't know.

Dave ;)

---

### Post by ratcheer on 2011-07-21
@anewguy, it could be either concatenated or striped sets of drives. Concatenated is what the OP is asking about, but RAID0 stripe sets offer better performance. However, RAID0 also puts the data at a higher risk, demanding regular backups. Of course, everything should be regularly backed up, anyway.

Tim

---

### Post by anewguy on 2011-07-21
I was thinking a concatenated set was the same as a RAID JBOD.  I thought they were still just as much in need of either constant backup or RAID shadow.  I say that because I thought (and let me tell you, I don't do that very often ;) ) that say you had 3 disks of various sizes in a JBOD array and the 2nd failed, you were just as screwed on recovery as you are with a striped set - your only choice being to go back to your last backup and lose anything you've done since.  Since the 2 disks are the same size, I just thought striping made sense because it gives the combination size and as you said should be faster since I/O's are spread across the drives.

However, we didn't have JBOD available back in the days when we were doing RAID 0 (disk sets) with RAID 1 (shadow).  The end result being I really don't understand how JBOD works.  If it works as a concatenation, does that mean that there is only 1 master volume descriptor and file table?  If so, I would think that would be vunerable as well.

Oh well, like I said I don't know JBOD (volume concatenation).

If there is a fail-safe of some sort built in so if a disk in the set fails it is recoverable without going to a backup then that sounds good.  Otherwise, depending on the importance of the data, I would think shadowing a striped set would work.  Of course, the OP only mentions 2 drives, so it would be a little difficult to make a striped shadow set with only 2 drives if you get my drift! ;)

At any rate, if you wouldn't mind posting back more on a JBOD array and how "safe" they are for data recovery I would sure be interested in knowing!

Thanks!
Dave ;)

---

### Post by ratcheer on 2011-07-22
I agree (and I think I finally said it in my prior post), backup is just as important no matter which way you do it. It is a little more critical with RAID0 because, if you lose one drive, you lose all files on any drives. With simple concatenation, the files aren't striped across all the drives, so...

But, we never did it that way, either. We always built RAID-10, where all the drives were mirrored in pairs, then the mirror sets were concatenated into large stripe sets. I was managing Oracle database systems and, over the years we had several disk drive failures with the systems never going down until we were ready to take them down to fix them. That is why I am such a proponent of RAID-10. It is expensive, but it works.

Tim

---

### Post by Grenage on 2011-07-22
> **c3ntury said:**
> I have a server hosted with OVH, with a fair amount of disk space (2 x 2TB drives). The server is running Ubuntu 11.04 with a custom kernel because the default one is a bit ... bizarre.

What I'm trying to achieve is the equivalent of a spanned drive, e.g, turning the 2 x 2TB drives into a single 4TB drive so that I can use use it to its full potential.

I'm going to second LVM, it's ideal for what you want.

---

### Post by anewguy on 2011-07-22
> **ratcheer said:**
> I agree (and I think I finally said it in my prior post), backup is just as important no matter which way you do it. It is a little more critical with RAID0 because, if you lose one drive, you lose all files on any drives. With simple concatenation, the files aren't striped across all the drives, so...

But, we never did it that way, either. We always built RAID-10, where all the drives were mirrored in pairs, then the mirror sets were concatenated into large stripe sets. I was managing Oracle database systems and, over the years we had several disk drive failures with the systems never going down until we were ready to take them down to fix them. That is why I am such a proponent of RAID-10. It is expensive, but it works.

Tim

Thanks for the information!  It's been so many years now I really just don't remember if we had that option and used it, or if it was purely striped shadow sets.  We also had a very large Oracle database with the same result - the system never went down unless we brought it down.  About the only thing I remember anymore is being on call 24/7 and needing to be able to get either online or at the system within 15 minutes of a call.  For the most part it never failed that they would call those of us in system support first at 3 a.m., only so we could tell them it's a programming error so call someone on call on that side.

Also, I understand from your thread that concantenation is not striping but rather just an array of disks made to look as a single disk, but I was wondering how the internals are on that - if the system just sees a large disk, and concatenation to me, not being familiar with it at all, would imply use one, then the next, then the next, etc.. can files span volumes, and if so, how/where is a master file table, etc., stored? Is such an array relying on no failure on a given device or is there some sort of reduncancy built in?  Hope you understand I'm asking because I don't know and would like to learn even though I haven't worked for years ;)  Also, I know the kind of things we are talking about aren't a normal users concern, but I would like to understand ;)

So, with the OP having the 2 - 2tb drives available, I would suspect indeed just making it look like one large disk is great, with, like we've mentioned, attention to backups - like everyone should be doing anyway.  Then I guess it comes down to the one which is less vunerable on a failure - if as you say concatenation is better that way then I would sure agree with that. Indeed losing a member of a striped set leaves you up the fast flowing water location without the method of movement device.  That's why I'm also curious on the file table and if a file can span volumes on a concatenated set.

And please, if I come across as arguing I don't mean to at all - I'm trying to learn something I don't remember having used before, and you seem to be a great source for info on that!


Again, thanks much for the information!  Very interesting setup!

Dave ;)

---

