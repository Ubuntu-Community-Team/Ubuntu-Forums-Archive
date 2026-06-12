---
title: "Disappearing Folders/Files 8gig Flash Drive"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by pj_kare on 2009-09-11
Was trying to transfer contents of My Docs from XP to Ubuntu using an 8gig flash drive. Started moving pics from flash drive to Home Folder/Pictures and then decided to cancel. I later noticed that the entire folder/files that I started to move had disappeared from the flash drive, along with a folder from inside a completely different folder. Later on a folder named something like "Found.000" appeared on the flash drive containing all the missing files renamed as Unknown01234.chk (for example). Can anyone shed any light on why this occured? I was glad to have the files back but not going to be able to remember all the files original names. :confused:

---

### Post by zephyrcat on 2009-09-11
The renaming of the missing files suggests that the Windows CHKDSK utility was responcible for recovering the files.

I'm not sure exactly how this would have happened, but CHKDSK is a command-link utility found in Windows that scans drives for anything messed up on the filesystem. If CHKDSK finds problems and recovers files, it will name them like the missing files you have (Unknownxxxx.chk).

As to why CHKDSK found problems or why it ran, I have no idea. If you removed the flash drive before it was done writing to/reading from it that could explain it. Otherwise, you could have a bad flash drive. If you are sure you haven't removed the flash drive too early, I would consider backing up and reformatting or returning the flash drive.

Unfortunately, I don't think there is any automatic way of renaming those files.

Hope that helps.

---

### Post by pj_kare on 2009-09-12
> **zephyrcat said:**
> The renaming of the missing files suggests that the Windows CHKDSK utility was responsible for recovering the files.

I'm not sure exactly how this would have happened, but CHKDSK is a command-link utility found in Windows that scans drives for anything messed up on the filesystem. If CHKDSK finds problems and recovers files, it will name them like the missing files you have (Unknownxxxx.chk).

As to why CHKDSK found problems or why it ran, I have no idea. If you removed the flash drive before it was done writing to/reading from it that could explain it. Otherwise, you could have a bad flash drive. If you are sure you haven't removed the flash drive too early, I would consider backing up and reformatting or returning the flash drive.

Unfortunately, I don't think there is any automatic way of renaming those files.

Hope that helps.

Thanks zephyrcat.....hadn't thought about chkdsk, but that makes sense, as I booted into XP shortly after losing the files, and chkdsk did run. I was hoping the missing folder would still be there if I looked using XP.
While it is possible the flash drive is faulty, it is brand new, 2-3 weeks.
Not too concerned about file names, it's just a pain in the ......

---

### Post by zephyrcat on 2009-09-12
> **pj_kare said:**
> Thanks zephyrcat.....hadn't thought about chkdsk, but that makes sense, as I booted into XP shortly after losing the files, and chkdsk did run. I was hoping the missing folder would still be there if I looked using XP.
While it is possible the flash drive is faulty, it is brand new, 2-3 weeks.
Not too concerned about file names, it's just a pain in the ......

Glad I could help. I'd be especially concerned about a new flash drive, since it could just be a bad unit. If you experience any additional issues with that drive, I'd send it back.

---

