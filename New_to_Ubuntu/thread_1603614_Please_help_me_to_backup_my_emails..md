---
title: "Please help me to backup my emails."
date: 2010-10-22
forum: New to Ubuntu
---

### Post by tahitiwibble on 2010-10-22
Hi to all,

When I try to copy my home folder to an external HD, one folder is not being backed up which is my ".mozilla-thunderbird".

I am told that "Filesystem does not support symbolic links" and have to skip the folder. Please can someone tell me what that means and how to get round it so that I can backup my oh-so-important emails.

Thanks much.

Could I just create another folder by the same name and then copy my Thunderbird folders to it?

---

### Post by ArgusVision on 2010-10-22
Is the external drive formatted as FAT32? I think that could be the problem...

---

### Post by tahitiwibble on 2010-10-22
> **ArgusVision said:**
> Is the external drive formatted as FAT32? I think that could be the problem...

I just looked; yes it is. Why does this happen only to the Thunderbird folder though?

For some reason the folder in question has a different icon from the others and has a little right-pointing arrow in the lower left-hand corner

---

### Post by ArgusVision on 2010-10-23
> **tahitiwibble said:**
> I just looked; yes it is. Why does this happen only to the Thunderbird folder though?

I'm not sure why Thunderbird's folder is different, (maybe a linux expert could help explain...) but if you format a usb drive (or partition a portion of your current drive) to ntfs or ext3/ext4. I think these file system types will support the symbolic links you need.

---

### Post by tahitiwibble on 2010-10-23
ArgusVision, thank you very much for the help. It appears that your suggestion is correct. I just tried to copy the same folder to one of my internal HD partitions with no trouble at all.

Thanks again. :) Have a good one.

---

### Post by ArgusVision on 2010-10-23
You're very welcome. Glad I could help.
Be sure to update the post to Solved.

---

### Post by tahitiwibble on 2010-10-23
USB HD reformatted, all going smoothly, problem definitively solved :)

---

### Post by jesuspresley on 2012-11-08
> **tahitiwibble said:**
> USB HD reformatted, all going smoothly...
What file format? NTFS or EXT3/4?

---

### Post by lisati on 2012-11-08
Old and solved thread closed.

---

