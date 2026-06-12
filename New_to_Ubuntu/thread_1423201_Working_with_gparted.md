---
title: "Working with gparted"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by RevKeltina on 2010-03-06
Ok, this weekend I am prepping my system for the removal of windows and all it's associated 'content'.  I will be giving all available space to Ubuntu 9.10.  I grabbed a copy of gparted and took a look in there which left me with a few questions...

1. How do I know which partition is which, as they are all labeled differently than the list I get a startup?

2. When I remove a partition with files on it, what happens to the disk space - i.e. does it automatically combine with the rest of the drive or is it just an empty volume?

3. I would like to do a 50/50 split for Ubuntu...one partition for the os and one for the backup...will I begin with a blank volume to write the backups to or can I move the information over with gparted?

I have time left, it won't get done today (and maybe not this week)!  I'm still waiting on the hubby to move his crap off the windows install!

---

### Post by mikeyphi on 2010-03-06
Welcome!!

Unless you've been using Ubuntu for some time, you might want to consider starting with a dual-boot option alongside windows or even trying Ubuntu inside windows. Have a look through this guide:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Answers to your questions:
1. windows will be on the file system ntfs; probably on /dev/sda1. Ubuntu (if already present) will be on file system ext3.
2. If you deleate a partition you will have empty space - available for a new partition.
3. You can't move data with gparted; it's for formatting and creating partitions. Create 2 partitions, one for the OS the other for back-up. However, I repeat my first comments above!!

---

### Post by ajgreeny on 2010-03-06
When you run gparted (from the live CD) you will get to a screen which looks like the attached pic.  This shows the filesystem type (ntfs shown in the pic) and it is that partition which will be windows, though it could also be fat32, not ntfs.

Make sure you have backups of all files needed from there, and also be aware that it is possible, depending on your setup that the partition could be a shared one for data, readable and writable from both windows and ubuntu.  Once you are sure about all that, you can delete the partition, provided it is unmounted.  If it is mounted the delete icon will be greyed out and unusable, so right click on the partition and choose "unmount".

Any deleted partitions will leave unallocated space which you can either leave as a separate partition and format it to an appropriate filesystem (ext3, ext4, etc etc) or you can expand your current ubuntu partition into that space.  The latter will usually take a long time as, in effect, it copies and pastes everything from place to place, so I would suggest you keep it separate, and perhaps even shrink your current ubuntu partition to end up with the 50:50 split you suggest.  You can not use gparted to copy and paste in the way you asked about, but you can use rsync or grsync later to do that quickly and easily.

Show us the gparted window when you run it and we can help you and suggest a course of action more easily.

---

### Post by oldfred on 2010-03-06
In gparted you should see sda1, sda2 etc as your partitions. It will also show format - ext3, NTFS and label if you have labeled them  which is recommend just to identify them) and a boot flag which is usually set on the windows partition or any linux bootable partition. Linux does not need a boot flag but some BIOS will not boot without one.

If manually partitioning you also need swap and should think about a separate /home for your data and configuration settings.

Some links on partitioning:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by switch10 on 2010-03-06
1.  In gparted they are labeled, and color coded.  NTFS is your windows partition.  EXT4 (or EXT2 or 3) are linux partitions.  It won't show up in the same order as your grub list.  Chances are Windows is on the first partition.

2.  it will become unallocated.  You can make a new partition here, or resize an existing partition over it.  You can mess with different settings, resizing and stuff, before you make actual changes.

3.  If you want, you can make an EXT3 or EXT4 partition named backup or something similar, with nothing on it, that could be used just for backup.  

I am including a screenshot of one of my hard disks.  Take a look at it.  It will give you an idea what you are trying to achieve.  Mine is a little more complicated though because I am booting 4 OS's, and I have a seperate /home partition.

---

### Post by baddnady23 on 2010-03-06
> 1. How do I know which partition is which, as they are all labeled differently than the list I get a startup?

They will eventually all be labeled differently.  Something along the lines of sda1, sda2, etc...

> 2. When I remove a partition with files on it, what happens to the disk space - i.e. does it automatically combine with the rest of the drive or is it just an empty volume?

It will become emplt disk space but still remain the same file system that it was formated in. 

> 3. I would like to do a 50/50 split for Ubuntu...one partition for the os and one for the backup...will I begin with a blank volume to write the backups to or can I move the information over with gparted?

Gparted is for formatting drives.  You can use it to format your backup partition into the filesystem that you want, for example EXT3 or EXT4.  Why backup up to a different partition on the same drive as the origional though...If that drive fails, you will lose all information including the backup.  It would be much more wise to at least store the backup on a different disk and even better to store it on a different machine all together.  Check this link out for more: [http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by RevKeltina on 2010-03-06
Ok, that is a great start.  I'm not worried about ditching Windows completely, as I have had a dual boot machine with both for a few months and have been reduced to just storing things on Windows.  I have everything backed up on external media that I need from the windows partition but want to get some more education before I do something horrible through ignorance!

Would it be a better idea for a back-up if I stored on a removable drive...like a flash drive?  I don't have more than one system at the moment since my hd in old bessie clunked.  

I rechecked the drives and can see that I have two ntsf and a fat32 listed in gparted.  That tells me that those two should be the ones that have windows on it?  Yes, there are two incidents of windows on this....thing.  I have XP and Media Center.....came from the factory that way.  So, I am guessing that I would remove both ntsf and the fat 32 sections....here is the screenshot of my gparted screen:

[http://i14.photobucket.com/albums/a338/privateer1967/Screenshot.png](http://i14.photobucket.com/albums/a338/privateer1967/Screenshot.png)

LOL This might take me longer than I thought!  Oh well, I have all the time in the world to decide what to do!

Would it be any easier to just run the live cd of Ubuntu and re-install it, do you think?  I could do that too.

---

### Post by switch10 on 2010-03-06
> **RevKeltina said:**
> Ok, that is a great start.  I'm not worried about ditching Windows completely, as I have had a dual boot machine with both for a few months and have been reduced to just storing things on Windows.  I have everything backed up on external media that I need from the windows partition but want to get some more education before I do something horrible through ignorance!

Would it be a better idea for a back-up if I stored on a removable drive...like a flash drive?  I don't have more than one system at the moment since my hd in old bessie clunked.  

I rechecked the drives and can see that I have two ntsf and a fat32 listed in gparted.  That tells me that those two should be the ones that have windows on it?  Yes, there are two incidents of windows on this....thing.  I have XP and Media Center.....came from the factory that way.  So, I am guessing that I would remove both ntsf and the fat 32 sections....here is the screenshot of my gparted screen:

[http://i14.photobucket.com/albums/a338/privateer1967/Screenshot.png](http://i14.photobucket.com/albums/a338/privateer1967/Screenshot.png)

LOL This might take me longer than I thought!  Oh well, I have all the time in the world to decide what to do!

Would it be any easier to just run the live cd of Ubuntu and re-install it, do you think?  I could do that too.

yeah FAT32 in what windows used to use.  It wont take long at all once you get all your data backed up.  Maybe 15 mins tops.

It would be very easy to put in a live CD, and choose "use entire disk" when you get to the partitioning part.  It will erase all partitions that are on there now.

Good luck.

---

### Post by RevKeltina on 2010-03-06
I think I will take the advice of loading it a-fresh from the live cd and just adding the back-ups back to it.  Sounds like there is less of a chance to create catastrophic mayhem! lol  I need all the help I can get in that department!

Thanks Everyone! :-)

---

