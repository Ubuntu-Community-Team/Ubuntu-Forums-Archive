---
title: "startup"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by konsta82 on 2009-06-26
I just installed fresh 9.04 on dell inspiron 1525 , but uptime is 40 s which is slower than 8.04 or vista. What is this about ?

---

### Post by theozzlives on 2009-06-26
> **konsta82 said:**
> I just installed fresh 9.04 on dell inspiron 1525 , but uptime is 40 s which is slower than 8.04 or vista. What is this about ?

I don't know, my 1525 flies with 9.04. You using ext4 file-system?

---

### Post by konsta82 on 2009-06-26
I'm using ext3. This is not expected, I thought it will be faster than 8.04 or at least faster than crapy vista

---

### Post by mikechant on 2009-06-26
My grub-to-login time on my eeePC 1000 SSD went from about 35 to 25s when I switched from ext3 to ext4.

---

### Post by konsta82 on 2009-06-26
I updated kernel but nothing changed. does ext4 have any conflicts with applications , should I try it out ?

---

### Post by mikechant on 2009-06-26
> does ext4 have any conflicts with applications , should I try it out ? 

'Normal' applications should not notice the difference. Standard filesystem utilities have been updated to work with it.

Possible problems:
If you use a partitioning utility that doesn't use the standard ext2/3/4 utils and libs it might not have been updated to support ext4 (gparted is fine though). Other specialist filesystem related utilities might not work for the same reason.

Any existing LiveCDs built without ext4 support won't work fully (e.g. old version of gparted with no ext4 support).

Boot loaders can be a problem. I've got a small seperate /boot partition formatted as ext2 and the main / (root) partition as ext4 which prevents any boot loader issues, but I think the latest version of grub might support ext4. Other bootloaders and old versions of grub probably won't support it.

Being naturally cautious with a new filesystem, I have so far only used ext4 for the root partition on my netbook, since this contains no important user data but gives a signifcant boot time improvement.

I don't think I've seen any recent reports of data corrupting bugs in ext4, but there have been some issues regarding the design leading to undesirable behaviour in the event of a machine crash (e.g. when updating kde config files I believe you could end up with a significant time window in which a machine crash would leave you with an empty config file instead of the old version or the new version of the file). I think those issues are supposed to have been largely addressed though.

I haven't had any problems myself and I've been using ext4 daily for about 2 months now.

---

