---
title: "memory and formatting"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by emsai on 2010-11-14
I am moving from XP Pro to Ubuntu 10.10 and have two basic questions:

1.  I will be installing a new Transcend 32 gb ssd; what format should I choose (NTFS or one of the 4 format types for linux OS?)

2.  I have 4 gb memory but only 3 are recognized under xp Pro; will Ubuntu recognize/allow the use of all 4 gb?

Thanks
Mr Ed

---

### Post by NightwishFan on 2010-11-14
> 1.  I will be installing a new Transcend 32 gb ssd; what format should I choose (NTFS or one of the 4 format types for linux OS?)

If you are only using a Linux OS I recommend using ext3 or ext4.

> 2.  I have 4 gb memory but only 3 are recognized under xp Pro; will Ubuntu recognize/allow the use of all 4 gb?

32-bit Ubuntu will automatically download the PAE kernel if you are connected to the Internet when you install. This means it will let you use all 4gb of RAM. If you have a 64-bit machine, use the 64-bit Ubuntu as huge amounts of RAM are natively supported.

> Thanks

No problems. :) Anything else?

---

### Post by techunit on 2010-11-14
> **NightwishFan said:**
> If you are only using a Linux OS I recommend using ext3 or ext4.



32-bit Ubuntu will automatically download the PAE kernel if you are connected to the Internet when you install. This means it will let you use all 4gb of RAM. If you have a 64-bit machine, use the 64-bit Ubuntu as huge amounts of RAM are natively supported.



No problems. :) Anything else?
In addition to this I would recommend you manually partition the SSD with no SWAP (Prolongs the life of SSD and you have plenty of ram). In the Ubuntu installer it will ask you if you want to allow Ubuntu to automatically format your HD (Harddisk) or manually partition it. Click to manually partition it and create a partition with the following criteria.

EXT4 - Full size of SSD - bootlocation at / - and check format.
please allow others to confirm this recommendation as it may no longer be valid. It over the last two years SSDs have changed alot and swap may be allowable now, but I am not aware of it.

I would also recommend Ubuntu 64bit if it is supported.

---

