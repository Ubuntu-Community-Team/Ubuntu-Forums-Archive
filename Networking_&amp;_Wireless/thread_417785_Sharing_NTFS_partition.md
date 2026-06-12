---
title: "Sharing NTFS partition"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Rizeup on 2007-04-21
I'm slowly trying to get rid of windows xp. In the meantime, I'd like to be able to share my mounted NTFS partitions. I can access these partitions fine. However, when I try to "share folder" I get an error message "the folder contents could not be displayed".

Then I still get the Share folder dialog but no matter what I do there it wont do a thing.

Anyway around this?

Thanks

---

### Post by attelas on 2007-05-07
I had the same problem and have it solved.
Start a terminal session and enter "sudo gedit /etc/fstab"
Now first make a backup of the fstab file (just in case of)
In the fstab file you see something similar to this:

UUID=B658C53658C4F661 /media/sda6     ntfs-3g defaults,nls=utf8,umask=007,gid=46 0       1

Go to the line of the partition you want to alter, replace the "umask=007" with "umask=000" and exit with saving the file. (000 'sets' the read/write/execute permission to the partition)
Back in terminal enter " sudo umount /media/'reference to your partition' "
After this enter "sudo mount -a" which command mounts all your partitions from /etc/fstab
Done.

---

### Post by vladk2k on 2007-09-21
**DELETED**

P.S.: When sharing, make sure the folde ryou want to share actually exists, don't spend half a day hitting your head on the wall like me

---

