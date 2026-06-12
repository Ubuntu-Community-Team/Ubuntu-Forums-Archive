---
title: "Problem with the partition tables"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by II0II on 2009-02-18
Hello, I want to install Ubuntu 8.10, but I've got a problem with preparing of the HDD, because there is Win XP. I used Partition Magic to free space - I've got C: and D: with NTFS, so I separated 5GB for linux.
Couples time I tried to install, but linux see 5.2GB instead of 5GB, or 4,2GB instead of 4GB(when I create with PM swap 1GB) and when I let linux to format the partition come problem with partition table, because I receive error 116 in PM that LBA and CHS values don't &#1077;qual after fix them come error 117.
What do I need to do that linux format in correct size?

---

### Post by zvacet on 2009-02-18
Decide how much space you want for Windows and rest leave as unallocated space (not partition).On that free space install Ubuntu.

---

### Post by scorchgeek on 2009-02-18
Is the freed space a partition? Deleting the new 5GB partition, if it is there, will create unallocated space, which makes the Ubuntu installer much happier in my experience.

---

### Post by II0II on 2009-02-19
Yes, last time I created 5GB unallocated space with PM, but when installation began ubuntu see 5.2GB instead of 5GB, so I know if I let to linux to do your job even if I write correct size of 5GB, will be mess after that with partition tables - LBA and CHS values don't equal, error 116, error 117, etc.

---

