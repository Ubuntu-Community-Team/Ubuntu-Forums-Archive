---
title: "sync duplicate folder between macosx and ubuntu, dual boot"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Whenry on 2011-04-21
I realize that I can not read and write to the same folder because my mac os x hard drive is journaled.

But is there a solution to keeping synced copies of the same folder between my partitions?

I am thinking I can do this with drop box, didn't know if there is a different way

I also had the idea of creating a small, non-journaled, partition to store shared folders on. But, when I try to create the partition in Disk Utility in Mac OSX I get an error 'MediaKit an not find partition'

sincerely,

Will

---

### Post by Chronon on 2011-04-22
Dropbox has a capacity limit of 2GB for the free version.  It will also duplicate the items placed in the shared folder.  If you're willing to deal with duplication you could just rsync the HFS+ folder to an ext4 (or other partition with read/write access in linux) partition.

How about non-journaled HFS?  Another user has recommended thusly:
[http://ubuntuforums.org/showpost.php?p=9260557&postcount=8](http://ubuntuforums.org/showpost.php?p=9260557&postcount=8)

Unfortunately, I have no idea about the error you're getting.

---

