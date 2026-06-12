---
title: "How should I partition my 64GB SSD for dual boot (Vista, Ubuntu)?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by andresmh on 2009-04-04
I was thinking about creating the partitions in the following order:
 
[LIST]
[*]20GB fat32: partition for documents, /home, and personal files

[*]25GB ntfs: for Vista (I wish it was smaller but it is currently using 23GB with OpenOffice and other small apps)

[*]19GB ext3: for Linux
[/LIST]

Also, if I make these changes, will Vista stop booting because I moved its partition? How do you deal with that?

---

### Post by hessczoo on 2009-04-04
That sounds good, just adjust accordingly to how much Windows and Linux you will be using.

Remember with the fat partition no file can exceed 4GB.

Vista should be okay, it can be picky but if it does it can be repaired. But if it's a fresh install, do Vista first then Linux.

---

### Post by andresmh on 2009-04-04
Thanks! Should I consider NTFS instead of FAT32 for the documents partition?

---

### Post by hessczoo on 2009-04-04
I would think it is better to do that. Also check out guides on mounting your Windows partition in Linux. I'm not sure if it's much mucking around. Fat32 is fine though for regular sized documents though and I'm sure would meet your needs!

---

### Post by Racecar56 on 2009-04-04
I agree that it is better for NTFS instead of FAT32.
Just be noted, that you can access EXT2/EXT3 (and I didn't try, but probably EXT4) partitions with [EXT2FSD]("http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd") so you don't **have** to put /home in a NTFS/FAT32 but if you don't want EXT2FSD then that's OK.

---

### Post by andresmh on 2009-04-04
Great! So Ubuntu supports read/write for NTFS out of the box?

---

### Post by billgoldberg on 2009-04-04
You should read this article on optimizing Linux for SDD drives:

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

It did wonders on my eeepc.

---

### Post by Racecar56 on 2009-04-04
> **andresmh said:**
> Great! So Ubuntu supports read/write for NTFS out of the box?
Yes.
NTFS-3G.

---

