---
title: "hard disk partition created with ubuntu not appearing in Windows XP"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by raju50 on 2011-01-02
I had used ubuntu 10.10. I had made partitions. Now, I am using Windows XP service pack 2. But I have lost 9 GB of my hard disk space.

---

### Post by mikewhatever on 2011-01-02
Windows can't see Linux file systems (ext2/3/4, etc) by default. If you want the partition to visible in both Ubuntu and Windows, format it as NTFS or FAT32, which are both Windows file systems.

---

### Post by raju50 on 2011-01-02
How to format it as NTFS/FAT32?

---

### Post by Miter_J on 2011-01-02
When installing Ubuntu, there're options for you to choose which format you prefer, I remember.
But after installation, I don't know how to change it.

---

### Post by mikewhatever on 2011-01-02
> **raju50 said:**
> How to format it as NTFS/FAT32?

Select a file system when formatting. You can use the Disk Utility under System->Administration.

---

