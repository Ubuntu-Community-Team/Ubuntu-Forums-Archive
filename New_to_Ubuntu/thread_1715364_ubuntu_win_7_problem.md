---
title: "ubuntu win 7 problem"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by solu61 on 2011-03-26
I have Windows 7 and Ubuntu 10.04.1 installed in the same hard drive on my laptop. The problem is that the files that I copy through Ubuntu are not visible on Windows. I have divided my hard drive into 3 partitions. One where i installed Ubuntu, one where i installed Windows, and a partition where i usually store all my data(drive G). The data copied through ubuntu, on drive G is not visible on windows. What do I do guys?

---

### Post by GWBouge on 2011-03-26
Do you mean that Windows can't read the files you copy onto your Ubuntu partition, or the files you copy onto your Windows partition from Ubuntu?

Windows itself can't read ext2/3/4 file systems, and ext4 is the default for Ubuntu.  To access your Ubuntu partition from Windows, you'll have to install a driver/utility such as [Ext2Fsd]("http://www.ext2fsd.com/") or [Ext2Read]("http://sourceforge.net/projects/ext2read/").  However ... as far as I know, the Windows utilities don't pay any attention to permissions or security on the ext4 end, which would make it *really* easy to bork your Ubuntu system, and I imagine a virus or malware wouldn't have many issues corrupting it as well.

If you can't see files you copied onto your Windows NTFS partition from Ubuntu ... that's an issue I'm not qualified to answer, lol.

---

### Post by garvinrick4 on 2011-03-26
I always make a partition for data for both Linux and Windows in NTFS format. Windows gives it a letter like G for example and Linux gives it a sda7 for example. So both Operating Systems can read.

---

### Post by samcot on 2011-03-26
Garvinrick, I've heard that if you want a common partition for Windows and Linux, the recommendation is FAT32. Is that incorrect? Is it better to use NTFS?

---

### Post by GWBouge on 2011-03-26
I've always used NTFS for a 'common' drive, such as the external Backup/Media drive I'm using now, and haven't had any issues with it ... BUT, Ubuntu doesn't seem to be able to put deleted files from an NTFS drive into the Trash bin ... it'll really just delete them!

Granted, that's not to say others haven't had any issues ... I really don't know much about file systems, I just opted to use my Windows' native format for my external drive and haven't looked back.

---

