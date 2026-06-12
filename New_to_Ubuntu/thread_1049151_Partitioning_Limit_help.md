---
title: "Partitioning Limit help"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by abauman49 on 2009-01-24
I finally updated my old computer and picked up a ZT system with Intel Quad core processor, 1333 FSB, 4G ram, 750G hd, Vista home premium.
  Following an tutorial I download from a link in this forum I resized the partition with Vista hoping to leave roughly a 500G Vista and 250G Ubuntu partition. that part went fine.  Now when I try to install Ubuntu 8.10 (64bit)  it can't seem to see beyond 500G on the hard drive!  Am I hitting a Ubuntu/Linux limitation or am I doing something wrong?  I tell the Ubuntu partitioner to use manual settings and it wants the whole..500g?

Thanks in advance,
    Tony

---

### Post by emarkd on 2009-01-24
There's no 500 gig limit in linux.  I've got a logical device formatted ext3 that's 1.5 TB in size, so no problems for you.  If I'm reading your post correctly, you've already broken the disk into two partitions before using the ubuntu installer, correct?  So it sounds like the installer is trying to repartition the 500 GB windows part.  Does the installer see both of your partitions?  Can you select the other partition somewhere?

Sorry that's so vague.  I haven't used an ubuntu installer for several versions now.

---

### Post by abauman49 on 2009-01-24
I was following a tutorial from apcmag.com that recommended using the Vista built-in partitioning capability, then installing Ubuntu in the free space.  I will try to resize Vista back to full disk and attempt another install using Ubuntu repartitioning only.  That may be the whole thing...the "unallocated" space that Vista freed up wasn't available to Ubuntu, although it showed it as unallocated....

Thanks

---

### Post by SOULRiDER on 2009-01-24
I always recommend partitioning hard drives witht he GPArted live CD. The Ubuntu live CD has GParted already in it, so you can use that.

---

### Post by Rim on 2009-01-24
<.< alright. When installing linux from the boot cd it will ask u to partition/select partition. When ur there use the MANUAL partitioning.

Once it scans the discs u will notice the windows Vista part and the part left tor linux that u already partitioned. Do the following:

1.Select and delete the partition that u made for Linux, u will have free space to work with now.

2.Make a new primary partition using roughly 20 gigs from the free space.Place it at the begining of the drive, select the EXT3 filesystem for it and mountpoint "/". This will be the Linux drive :) for system files and such.

3.Select free space again and make new partition using 1/2 of ur actual ram memory as disc space. Example if u have 4 gigs use 2 gigs disc space for this 1. place partition at the END using SWAP file system and make it primary. this will be the swap file to make the system run even more smoothly:).

4.take the rest of the free space and make new primary partition using EXT3 filesystem and use "/home" mount point. :) this will be where us store all ur personal programs and stuff such as downloads etcetera so it has to be the biggest drive.

after u set this up it will mark the "/" and "/home" partitions for formating and u can continue with the install.

I hope it helped.

---

### Post by abauman49 on 2009-01-24
Success!  That was it.. once I got rid of the Vista-created "unallocated" partition everything was fine...
  I now have ~500g Vista and ~250G Ubuntu partitions!  I set Vista as the default in case the wife and kids boot it up...

Thanks for the help guys!

---

### Post by Rim on 2009-01-24
:D glad to see it work!

---

