---
title: "Partitions and Multiple OS interactions"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by mattyg225 on 2010-10-23
I've decided to take the plunge into Linux.  I plan on installing ubuntu alongside XP, but have limited space on the HD.  I've got a 90gig HD, mostly full with multimedia files that I want access to from both OS environments.

I am not sure how the two partitions with each other.  If I create 2 partitions and keep all of the files I need access to on the XP partition, can I easily navigate to them and use the files when I boot into Ubuntu and vice versa?

If not, does it make sense to create 3 partitions 10g XP /10g Ubuntu /70 (for files)?

Thanks in advance for any advice or suggestions,
MG

---

### Post by SavageWolf on 2010-10-23
Yes, you can read files from an NTFS (The one XP uses) filesystem, but I wouldn't recommend it (You'd have to go through "Documents and Settings" and such). I'd recommend making a 3rd partition, of type [s]FAT (I don't think Linux is very good with NTFS fss, but I may be wrong)[/s] NTFS. I would also recommend, if you have the space, to give more than 10GBs for the OSes, and 2-4GB of swap (swap is like the "page file" in Windows).

---

### Post by spiky001 on 2010-10-23
yes to the 3rd option in my opion, if anything happens to either os then data is safe in another partition

---

### Post by Hippytaff on 2010-10-23
I would say it's worth backing up all those files before partitioning you HDD. I partitioned my HDD the first time without any problems, but problems do occur...there are ways to access your files stored on the windows partition and vice versa :-)

---

### Post by oldfred on 2010-10-23
Back up is always a good idea. 

But use NTFS for the shared partition. I had a FAT partition originally and it did not tell me files over 4GB were just truncated (ruined). Also NTFS is journaled so it is easier to repair. You still need to run chkdsk on it occasionally.  

NTFS and Fat info:
FAT 4GB max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by mattyg225 on 2010-10-24
Great, thats exactly the info I was looking for.  Thanks for the quick replies!

MG

---

### Post by swoody on 2010-10-24
I agree with the suggestions of everyone so far. Creating a seperate NTFS partition for your shared data would be the simplest and probably best route. On top of the file size issue with fat mentioned above, fat doesn't support encryption or compression either. These are both rather useful if you decide you want to either protect your data (TrueCrypt is available for Windows and Linux) or try to maximize the amount you can fit onto the partition.

Generally speaking, I would *always* recommend backups when it comes to partitioning or modifying filesystems, although I work in a datacenter where many clients *might* get upset if we lose some/all of their data ;) However, if you don't have backups of pictures, documents, etc. which *cannot* be replaced, and you haven't suffered from data loss yet, you are both lucky and unknowing of the pain that can come with it. I am sure once you do lose some important data that you will have an entirely new perception of backups :) Even with something as simple as burning them to CDs can save you headache down the road.

- Woody

---

