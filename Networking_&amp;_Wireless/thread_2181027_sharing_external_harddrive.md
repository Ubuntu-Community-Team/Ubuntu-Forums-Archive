---
title: "sharing external harddrive"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by hop-sings on 2013-10-15
I have tryed everything I could find but have had no results. 

If i have a file in my local harddrive i have no issue sharing the file over my network by right clicking on the file and selecting sharing opptions.
i also notice i have access to the permissions of that file to change owner/group and other folder access permisions.

when i try to do the same thing with my external drive I have no access to the owner/group and other folder access permisions, it just wont let me change the permissions. can anyone help

---

### Post by Bashing-om on 2013-10-15
hop-sings; Hi !

What pops to mind is that the external hard drive is partitioned NTFS (???)
How are you mounting that external drive ?
And what is the partitioning scheme ?

From ubuntu, NTFS access and permissions are set at the time of mounting.

[INDENT]just a thought, I am sure there are others 
[/INDENT]

---

### Post by hop-sings on 2013-10-15
the drive is formated to NTFS with no partitions
mount in the **/media/<username>** directory

---

### Post by Bashing-om on 2013-10-15
hop-sings; Well
General - mind you general - instructions to mount and access NTFS read and write:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
You may employ other mounting options to meet your specific needs. This will get you in the ball park.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by hop-sings on 2013-10-15
from my understanding the drive is mounted, I have local read and write access to the drive. the issue is my ability to change the permissions on any file in the drive under owner/group and other under the properties and permissions.

---

### Post by Bashing-om on 2013-10-15
hop-sings; 

I am short on specific knowledge as I do not use/need/access Windows' NTFS, these accesses are set in the mounting options in specifically the "fstab" file.

Others with that knowledge will have to advise.

[INDENT][INDENT]somethings I just do not want to know
[/INDENT][/INDENT]

---

