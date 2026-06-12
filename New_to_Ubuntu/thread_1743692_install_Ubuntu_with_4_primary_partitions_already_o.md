---
title: "install Ubuntu with 4 primary partitions already occupied"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Linjie on 2011-04-29
Hello, I want to install ubuntu on my new laptop. It already has four primary partitions: 
 
SYSTEM (199MB, NTFS)
C (NTFS)
Recovery (15GB, NTFS)
HP_TOOLS (103MB, FAT32)
 
I'm going to shrink the C partition. And I think I should delete one of the others in order to install ubuntu, but I don't know which one I should delete. Any suggestions, please?

---

### Post by bodhi.zazen on 2011-04-29
You can only have 4 primary partitions, but you can have more then 4 extended / logical partitions.

You will need to either:

1. Get a new hard drive.

2. Copy / back up the data on one partition (you get to choose which one) and then delete the partition and make an extended partition.

Ubuntu should have two partitions, a root ( / ) partition and a swap partition. 

If you have enough RAM you can go without a swap partition , or you can use a file on the root partition as swap, but you would need to configure this manually as the installer will not do a swap file for you.

See also:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by Linjie on 2011-04-29
Hi, Thanks for your answer! It's very helpful. I think I'll not use a swap since it looks like it may slow things down. And I probably have enough RAM for me.
 
But I'm kinda confused about the /data and /home. Shall I use both or shall I just use /data? If I should use both, how large should they relatively be? I will only have one ubuntu and a Windows OS. 
 
And about the partitions, I've made a recovery disk in Windows, so now I think it's safe to delete the recovery partition. So the steps are: shrink the C partition, delete the recovery partition and then use all the free spaces as the extended partition. Is this right?

---

