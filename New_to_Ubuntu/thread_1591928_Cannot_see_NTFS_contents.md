---
title: "Cannot see NTFS contents"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by scorpion279 on 2010-10-10
I cannot see or access my ntfs (external) drive's contents.

scoine@ubuntu:~$ df -Th
Filesystem        Type         Size       Used     Avail    Use%     Mounted on
/dev/sdb5            ext4           11G        7.6G     2.6G     75%       /
***/dev/sdc3       fuseblk     299G       238G      61G       80%      /media/279_***

scoine@ubuntu:/media/279_$ ls
*** ls: reading directory .: Invalid or incomplete multibyte or wide character***

Using ***nautilus /media/279/<directory name>***  I got access to my directories n files but now this one is also not working

when I open the drive, despite containing the data, it shows absolutely nothing  
How can I get access to my data or at least recover it.

---

### Post by luvshines on 2010-10-10
Can you print output of:
```
echo $LANG
```

---

