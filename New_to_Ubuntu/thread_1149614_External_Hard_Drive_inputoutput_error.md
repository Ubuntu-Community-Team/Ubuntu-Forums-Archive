---
title: "External Hard Drive input/output error"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by wuchun05161990 on 2009-05-05
Hello, I have Ubuntu 9.04 installed using Wubi under Vista. I have an external hard drive that worked fine. However, today I copied some files from my work desktop (windows XP) to the hard drive, and after that I have the following problems with the external hard drive:

1. Whenever I try to copy anything to /media/name_of_external_hard_drive, the prompt says input/output error.
2. The same thing happens when I want to delete any files under /media/name_of_external_hard_drive.
3. However, when I tried to remove /change a file in a directory under the hard drive, like /media/name_of_hard_dirve/a_dir, there was no problem. 
4. If I run vista and try to open the hard drive, the prompt says it's corrupted and non readable. So I can't even open the drive under Vista. I did a chkdisk under vista but that didn't work. 

Note the files I copied from work are in the /media/name_of_hard_dirve. They should be large files, but I checked the properties of two of them, the size appears to be zero. I guess they are corrupted.

So what should I do? I can copy all the files from this drive to somewhere to backup since I can still access them under Ubuntu, but they are like 300 GB altogether. Is there anything I can do before I need to format the drive?

Any help is appreciated!

---

### Post by e_james on 2009-05-06
The standard procedure for repairing a hard drive or a flash drive is to retrieve as much information as possible from it before attempting any repairs. The commercial data recovery services copy the entire contents of the drive (including any data corruption) to new storage and then do any necessary data repairs. There are a few techniques which might restore some of the data (assuming the drive has no physical faults) but it is likely that, even if the data restoration is easily successful, some data will be lost.

I have around 4TB of storage in operation, spread over 7 drives, and the same again in backup capacity. My first strategy is always to have at least 2 copies of anything I don't want to lose and my second is to replace any drive that looks as if it may be failing with a new one. At present day prices, it is by far the cheapest option.

I have yet to try out Wubi but I believe it would add undesirable complications to any linux based drive repair operation.

---

### Post by meindian523 on 2009-05-06
If you can get off your files,or have a backup copy somewhere,it's best to format the drive.My flash drive had a similar problem which was cleared when it got it's first(and only) format from a friend's XP machine.Somehow flash drives and externals need Windows to be formatted is my best guess.

---

