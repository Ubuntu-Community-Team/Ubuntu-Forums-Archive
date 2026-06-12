---
title: "Universal USB installer"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by akshay2000 on 2010-05-28
I am now installing the Ubuntu 10.04 LTS on my 16 GB pen drive. I've kept persistacne to 3 GB. Now, my question is, will the remaining space available on my windows system to use?

---

### Post by -humanaut- on 2010-05-28
Yeah, It should be though you might have to partition the unused space to Fat32

---

### Post by arubislander on 2010-05-28
The quick answer is yes.

The longer answer is: yes, but that is courting disaster... Since everything is just a file on the stick you could accidentally delete an important file, and render your Ubuntu unbootable.

What I usually do is make two partitions, both FAT32, on the pen drive. In your case I'd size the first one to 12 GB, and use the rest on the second one. Make the second one bootable and install Ubuntu on that. 

For some reason, that we use to our advantage here, only the first partition is visible under Windows. But both partitions are visible to the BIOS so you can safely boot boot from there.

---

