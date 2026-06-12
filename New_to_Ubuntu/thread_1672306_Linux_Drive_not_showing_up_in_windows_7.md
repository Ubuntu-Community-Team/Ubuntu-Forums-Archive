---
title: "Linux Drive not showing up in windows 7"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by B3ntleg on 2011-01-20
OK this is kind of a windows question so you will have to forgive me.  I was running windows 7 and put in a 2nd drive with the plan of putting some type of linux on it.  Eventually I got around to putting Ubuntu on it and that all went fine.  But Windows doesn't seem to see the drive.  I wondering if anybody could give me any advice.

Just a side note I am not use to using Linux and until I get more use to it I still am having to use windows.  Also while I know more about computers then anybody I personally know, looking around this forum I am pretty much at the bottom of the pecking order when it comes to technical knowledge.

---

### Post by steve.horsley on 2011-01-20
Your Linux disk was probably formatted with the ext4 filesystem, which windows cannot read. In fact, windows cannot read any modern linux filesystem. There are drivers that claim to be able to read ext3, but even they can't read all ext3 disks.

Linux can read/write FAT and NTFS though, so it will be able to read your windows partitions. Don't think about trying to install linux on NTFS though - that cannot work because FAT/NTFS cannot hold the necessary file attributes. You can't even put peoples home folders on FAT/NTFS.

It is common for people who dual-boot to use an NTFS or FAT partition to hold the data files that they share between OS's.

---

### Post by B3ntleg on 2011-01-20
Thanks, this is what I was talking a out with being on the bottom of the pecking order I had never heard of ext4.  So pretty much I have to keep my Linux drive as an exclusive Linux content drive and will have to put any dual files on my windows drive or an ext hard-drive?

---

### Post by oldfred on 2011-01-20
Even though Linux will read & write your windows system partition, I would not do that. You can read from a system partition, but writing always has a higher risk. It is much better to create a shared NTFS partition. Windows will see it as a D: drive and you can easily set Ubuntu to mount and use the NTFS drive for data.

I have my Firefox & Thunderbird profiles in my shared NTFS partition. Originally in trying to learn Ubuntu, my wife wanted to get on the Internet or check email and I had to reboot. Once I set up shared data I found I did not need windows so much.

---

