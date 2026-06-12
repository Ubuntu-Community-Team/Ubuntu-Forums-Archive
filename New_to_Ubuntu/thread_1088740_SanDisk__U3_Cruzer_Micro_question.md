---
title: "SanDisk  U3 Cruzer Micro question"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by fiskking on 2009-03-06
Hello guys.

  Here is my problem.  I recently formatted a memory stick to FAT32 on windows yesterday, now Linux nor Windose is unable to see it.  I have no means of getting to a windows box to format it again is there a way for ubuntu (thru terminal) to reformat the storage drive back to its original state??

---

### Post by MrWES on 2009-03-06
> **fiskking said:**
> Hello guys.

  Here is my problem.  I recently formatted a memory stick to FAT32 on windows yesterday, now Linux nor Windose is unable to see it.  I have no means of getting to a windows box to format it again is there a way for ubuntu (thru terminal) to reformat the storage drive back to its original state??


Install gparted from the repositories and you can then reformat your usb flash drive. Make sure the drive is not mounted and you're absolutely sure you have the correct drive before you apply your changes in gparted.

Bill

---

### Post by lindsay7 on 2009-03-06
If you get to a windows machine, this tool will clean and format the usb back to factory settings, HP USB Disk Storage Format Tool v2.1.8. Search for it on the internert.

---

### Post by fiskking on 2009-03-06
> **MrWES said:**
> Install gparted from the repositories and you can then reformat your usb flash drive. Make sure the drive is not mounted and you're absolutely sure you have the correct drive before you apply your changes in gparted.

Bill

I was able to format...thanks!

---

