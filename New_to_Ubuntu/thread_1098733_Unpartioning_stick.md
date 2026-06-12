---
title: "Unpartioning stick"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by carrarin on 2009-03-17
I tried the ubuntu on a stick, and i couldn't get it to work on my computer. 

Regardless, i am now left with a partitioned 16gb stick. :( 

I want to remove the all the partitions and format the stick. How do i do this? Also, im going to be using a live cd on a computer with no internet


Thanks

---

### Post by finer recliner on 2009-03-17
well if you're in windows, i think you can just plug your USB drive in, go to "my computer", right click on the USB drive and choose "format". Choose NTFS if you have more than one option. 

**Please note this will perminately wipe out ALL data on your USB drive!**

---

### Post by carrarin on 2009-03-17
update: tryed removing partition now when i stick it in windows i get an error message that says it can't read the disk

---

### Post by finer recliner on 2009-03-17
i think thats to be expected. The USB drive is formated in a file system that windows doesn't know how to read. It's okay that windows can't read it, because you're going to wipe it out anyways... just right click the drive in "My Computer" and choose "Format".

---

### Post by sgosnell on 2009-03-17
My method would be to use the Ubuntu live CD, boot to the desktop, and then run Partition Manager (Gparted), with the USB stick plugged in.  Select that drive, unmount all the partitions, remove all the partitions, then add a new partition that takes the entire drive, and format it to FAT32.  That should restore your stick to its original state.

---

### Post by finer recliner on 2009-03-17
a 16GB drive formated in FAT32 is going to lead to terrible fragmentation and poor effiencency...

---

### Post by sgosnell on 2009-03-17
Fragmentation on a flash drive is not a problem.  That's the way they come.  You could probably format it as NTFS, but I don't think it's worth it.

---

