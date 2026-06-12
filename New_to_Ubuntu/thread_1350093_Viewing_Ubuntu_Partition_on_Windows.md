---
title: "Viewing Ubuntu Partition on Windows"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by kristine12 on 2009-12-09
Is there a safe way that I can view my files on Ubuntu with a ext3/ext2 file system on Windows 7

I already tried ext2IFS ( ext2 Installable File System ) but it doesnt work...
I still can't view my file system.

---

### Post by oldfred on 2009-12-09
Generally not, especially if the ext2IFS does not work. IF you are dual booting you may want to create a shared partition that is NTFS. Both windows and Ubuntu will read & write that just fine. While the NTFS writing in Ubuntu is considered good now, I still like to have the separate partition as the windows boot partition seems to not like others using it.

I used to boot windows most of the time 3 years ago and put a lot of data in the shared partition. Now I still use windows occasionally and have a NTFS data partiton and now another ext3 data partition to share between several Ubuntu installs that has data I would never use in windows.

---

### Post by cariboo on 2009-12-09
If you are running Karmic, your partition is formatted to ext4 by default. The windows utilities haven't caught up yet, as they can't read ext4

---

