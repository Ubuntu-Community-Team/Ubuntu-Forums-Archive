---
title: "To increase the size of my Ubuntu Folder"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by vivek.purushoth on 2011-07-13
Thanks in Advance . I have installed Ubuntu inside Windows. And i had selected just 17GB of memory for Ubuntu partition. Now i want to increase the Memory of My Ubuntu . I have so much space left in other Drives but i wanted to know how am i supposed to append it to my Ubuntu so that i will be able to use more space in Ubuntu say 100GB or something .

---

### Post by mikewhatever on 2011-07-13
You can't append space from other drivers to the 'inside Windows' installation. If you are done evaluating, and plan on using Ubuntu, install it to its own partition.

---

### Post by lmarmisa on 2011-07-13
Try to mount the other hard drives (or partitions) where you have free space and use this space from Ubuntu (I recommend to use this space for your data files like photos, music, documents or video, not for programs).

This link can help you for mounting automatically these other drives:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Anyway, if you want to access to the partition of the Windows OS, you do not have to mount it. This unit is located at **/host** (see the capture).

A final comment. Symbolic links could help you for accessing to files or folders located in other drives different to the Ubuntu partition.

These could be two examples:

```

ln -s /host/MyPhotos ~/MyPhotos
ln -s /media/MyData/MyDocuments ~/MyDocuments

```

---

### Post by wildmanne39 on 2011-07-14
> **vivek.purushoth said:**
> Thanks in Advance . I have installed Ubuntu inside Windows. And i had selected just 17GB of memory for Ubuntu partition. Now i want to increase the Memory of My Ubuntu . I have so much space left in other Drives but i wanted to know how am i supposed to append it to my Ubuntu so that i will be able to use more space in Ubuntu say 100GB or something .Hi, also if you want you can use this guide to resize your wubi partition.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by vivek.purushoth on 2011-07-14
Thanks a lot :) I want to keep more space for Ubuntu . So i'll now create a whole dedicated drive for Ubuntu and then install it.

---

