---
title: "Concern for Data: How does G-parted work?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by geebob on 2009-05-14
I have a friend with an older computer for whom I may install a linux distro (It won't be ubuntu, the computer  has too little memory.  I intend to use Puppy).  I started to partition his drive and while it scrunched all the data to the left side of the hard disk graph, it still left a strand on the right side.  Whenever I've defragmented drives, if memory serves me, I'm used to seeing all of the data go to the left.

Sorry if this is a stupid question, but I hope to minimize the perceived risk here of repartitioning the hard drive.

How does G-parted work?  I assume that it will see the data, on the right side, pick it up and move it when I expand new partitions into that area.  But I was a little concerned that G-parted may be dumber than that.  That it would just assume that aall the data was on the left and just shrink the drive right over the strand of data hanging on the right.

I would just like some confirmation that g-parted works the smart way given what I assume is a strange thing defragmenter to do

---

### Post by AndThenWhat on 2009-05-14
If you are unsure then you should research online or provide us with some screenshots.  It is always better to be extremely cautious with someone's hard drive because if you mess it up then they will end up hating linux.

---

### Post by Bartender on 2009-05-14
Try running defrag several times.  If it still refuses to move that data over then you're taking a chance moving forward with GParted.  It's not at all uncommon to render the PC unbootable when moving data.  Far far safer to create partitions on empty space.
Maybe try an aftermarket defrag tool if Windows doesn't want to move it?  I've seen the same thing before; a strip of data way out to the right that didn't want to move.

What's he got on the HDD now?
How hard would it be to save personal data and reinstall Windows?

One bombproof way to do this is to wipe the drive with GParted and create a primary NTFS partition at the "front" (left-hand side) of the drive.  Then install Windows.  The Windows installer will only see the NTFS partition.  When done installing Windows, install Ubuntu to the rest of the drive.

---

### Post by cneil on 2009-05-14
G-Parted will reliably make new partitions.  Even if there is a little data to the side, it will figure it out.

However, do not try to change the filesystem of a drive.  It will delete everything!  I thought that I could change a drive from FAT32 to NTFS without losing data.  Unfortunately, G-Parted isn't that smart.  However, if you just want to add a partition and there is blank space on the drive, you don't have much to fear.  However, if you make the partition and decide to remove it, you could be in for big trouble....

Back Up, please....

---

### Post by Niniel on 2009-05-14
There was a tool in Windows to converted FAT32 to NTFS... GPartEd is just a partitioner, don't expect it to be a tool that does everything. :)

Please remember, the nice graphs you see when defragmenting/partitioning are just visualizations to help you understand the process and give you an idea/illusion that something is happening, not necessarily to show the actual layout of the disk. It doesn't mean that data is actually moved to any "end" of the hd. Normally, all these tools do is unite fragments. However, there are defragmenters that do "compact" the data, e.g. move it all to one continuous block on the hd. I like one that's called "[DirMS]("http://www.dirms.com/home/docs/dirms1.asp")".

I've successfully used GPartEd to shrink an NTFS partition on a laptop computer from 100 % to something like 80 % so I consider this a pretty safe tool. 
Still, saving important data before messing with partitions is always a good idea.

---

### Post by mapes12 on 2009-05-14
Make sure you're running GParted from a LiveCD. It will not configure a HDD if that's where it's running from. Can you back up this data to an external device then wipe the disk ready for your install? You could then just restore the data after the install.

---

### Post by Bartender on 2009-05-15
+1 on mapes' comment.  The dedicated GParted LiveCD is a far better tool than GParted on the Ubuntu install CD.

---

### Post by NHArticleTen on 2009-05-15
Puppy Linux distro has gparted on it and I've used it repeatedly to tame hard drives.

I've taken an 80gb laptop hard drive with XP(ntfs) on it and used the Puppy live-run to reduce the ntfs partition by FIFTY PERCENT.

As always, your mileage may vary...

As usual, backups are mandatory...

Damn Small Linux
Puppy Linux
Clonezilla
Killdisk
MBRTool
Ubuntu
DBAN

---

