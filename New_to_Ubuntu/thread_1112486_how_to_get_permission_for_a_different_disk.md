---
title: "how to get permission for a different disk"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by squimmy on 2009-03-31
Hi, I'm trying to copy some files from one hard disk to another, the one I want to copy them to has its own installation of ubuntu on it and thus it won't give me permission to add any files to it, how do i get this permission?

---

### Post by lindsay7 on 2009-03-31
.

---

### Post by bodhi.zazen on 2009-03-31
Please do not invoke root powers without teaching about permissions. IMO root powers should not be abused in this way, you should teach how to sys admin.

The answer to your question is that it depends on the file system. Permissions are set at the time of mounting , but the way they are set and options are determined by the underlying file system and FAT/NTFS is different then Lniux native file systems.

See :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

