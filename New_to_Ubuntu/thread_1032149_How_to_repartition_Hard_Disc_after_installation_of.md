---
title: "How to repartition Hard Disc after installation of Ubuntu"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by cannybody22 on 2009-01-06
I have just installed Ubuntu and allowed it to partition the disc for dual booting of Windows Vista home premium and Ubuntu. Unfortunately it has left Vista with only 10% of the disc which means that while vista is still working it has no spare space.Ubuntu has a vast amount of space beyond its requirements.
I am a relative novice and would appreciate clear direction on how to re partition the disc to allow 50/50 use.It is 200 gig capacity.
I like what I see of Ubuntu so far and hope that I:confused: can resolve the problem

---

### Post by ELF_O8 on 2009-01-06
First, you will need a partition tool, but you will need it without using it in the OS itself. You can use the one on the LiveCD (System->Administration->Partition Editor), or you could make a GParted LiveCD.
Once you have either of these open you can shrink the Ext3 file system by however much you need. Am I right to assume that Windows is in front on the partition table and Ubuntu is behind it? (Left to Right)

---

### Post by nhasian on 2009-01-06
you would need to boot off the liveCD and go to System->Administration->Partition Editor.  then resize the ubuntu partition and shrink it to the desired size.  Then rather than using the partition editor to adjust the ntfs partition, lets let windows do that.  so boot into vista and then go to disk manager.  expand the vista partition to fill the empty space.

make sure to backup any critical data before resizing partitions!

---

### Post by ELF_O8 on 2009-01-06
> **nhasian said:**
> you would need to boot off the liveCD and go to System->Administration->Partition Editor.  then resize the ubuntu partition and shrink it to the desired size.  Then rather than using the partition editor to adjust the ntfs partition, lets let windows do that.  so boot into vista and then go to disk manager.  expand the vista partition to fill the empty space.

make sure to backup any critical data before resizing partitions!

It's not quite as simple as that; the unallocated space needs to be next to the Windows partition instead of on the other side of the Ubuntu partition. However, resizing from the front of a partition (what you would need to do if the Windows partition is in front) has certain risks: it can misplace the boot sector (though this is rather more fixable in Linux than Windows). As nhasian said, backup, backup, BACKUP all important data before any resizing.

---

### Post by cannybody22 on 2009-01-14
Sadly you were right it really is not as simple as that.Did reduce the Ubuntu partition but windows could not be persuaded to use any of the  the free space.The only solution now seems to re format the hard drive and re install both Vista and Ubuntu but this time control the space used for Ubuntu.Learning is sometimes hard!Probably saved the major part of my data.

---

### Post by zvacet on 2009-01-14
With [Gparted live Cd]("http://gparted.sourceforge.net/") you should be able to expand your Windows partition to unallocated space you create before.

---

