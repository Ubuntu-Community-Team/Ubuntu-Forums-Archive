---
title: "What Format for Networked Drive?"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by rjmusto on 2008-03-26
I have a laptop set up as a file and print server (using Feisty) and have a mixture of Windows and Macs attached. All working ok.

I want to attach an external drive to the Ubuntu box to act as a further central file store.

Does it actually matter how I format this drive? Do the attached PC's and Macs care if it is formated as a Linux drive or with NTFS etc?

Since it will be handling large file sizes (photos), does one method or another result in more efficient file transfers? (Just not sure if some kind of translation has to be done...)

Thanks.

---

### Post by prshah on 2008-03-26
> **rjmusto said:**
> 
Does it actually matter how I format this drive? Do the attached PC's and Macs care if it is formated as a Linux drive or with NTFS etc? 

Nope; format it as you like; the networking system encapsulates the actual file system in use.

> Since it will be handling large file sizes (photos), does one method or another result in more efficient file transfers? (Just not sure if some kind of translation has to be done...)

Thanks.

I wouldn't call photos LARGE sized. Videos, CD/DVD images, maybe some audio...

In any case, there is no "translation" or extra steps if you use NTFS or FAT32 or etc. But it might be a good idea to stick to ext3 for advantages in file-system consistency, low fragmentation etc.

---

### Post by rjmusto on 2008-03-26
Ok, great. Thanks for that.  I'll stick to native Ext3 then.

Guess I'm showing my age then; still think photo files are big!

---

