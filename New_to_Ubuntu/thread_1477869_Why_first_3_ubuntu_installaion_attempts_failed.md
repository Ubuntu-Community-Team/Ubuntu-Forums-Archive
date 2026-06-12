---
title: "Why first 3 ubuntu installaion attempts failed?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-09
Yesterday i installed ubuntu 10.04, dual boot with windows 7. It was successfully installed in 4th attempt. The question is why first 3 attempts failed?

Before Installing i had 5 NTFS partitions:
C: 32GB NTFS (Primary)
D: 32GB NTFS (Logical)
E: 32GB NTFS (Logical)
F: 32GB NTFS (Logical)
G: 21GB NTFS (Primary)

In first 3 failed installation attempts i deleted 5th partition( G: ) and divided it into 3 primary partitions 1 for each /, /home & swap. This makes a total of 7 partitions.

While in 4th attempt which was successful, I was not able to make a partition for /home because free space was "unusable". So i left it as it was and got on with the installation. This installation attempt was successful. Although i lost 10GB of unusable space.

after that i logged on to Windows 7 and opened "disk management" to get my 10GB space back. And when i tried to make a partition of 10GB unallocated space, windows 7 gave me the following error:
"You can not create a new volume in this unallocated space because the disk already contains the maximum number of partitions."

My question is "was number of partitions the reason for first 3 unsuccessful ubuntu installation attempts?"

---

### Post by ankspo71 on 2010-05-09
Did you have more than a total of 4 primary partitions? You would be limited to only 3 if there is 1 extended partition containing any number (up to 24) of logical partitions.

Here is more on partitioning: (good reading material for any OS)
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

---

### Post by SKhan on 2010-05-09
> **ankspo71 said:**
> Did you have more than a total of 4 primary partitions? You would be limited to only 3 if there is 1 extended partition containing any number (up to 24) of logical partitions.

Here is more on partitioning: (good reading material for any OS)
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

Only C: and G: were primary. I deleted G: and divided it into 3 primary partitions. So this way, there should have been 4 primary partitions after the installation. (not 5 because G: was deleted.)
I am not sure, but I vaguely remember that i also tried to mount /home on logical partition. So that, after the installation there should be only 3 primary partitions in total, but that attempt was failed.

---

### Post by QLee on 2010-05-09
[QUOTE=SKhan]Only C: and G: were primary. I deleted G: and divided it into 3 primary partitions. So this way, there should have been 4 primary partitions after the installation. (not 5 because G: was deleted.)
I am not sure, but I vaguely remember that i also tried to mount /home on logical partition. So that, after the installation there should be only 3 primary partitions in total, but that attempt was failed.[/QUOTE]

What you might not be taking into account is that the volume, the extended partition, that holds your logical drives is itself counted as one of the primaries.

You might want to review that link that was given.

---

### Post by SKhan on 2010-05-10
> **QLee said:**
> What you might not be taking into account is that the volume, the extended partition, that holds your logical drives is itself counted as one of the primaries.

You might want to review that link that was given.

thanks man. The link given by ankspo was visited and read instantly. Now i have got my lost space back and have isntalled Kubuntu.

---

