---
title: "&quot;File too large&quot; error copying files &gt; 4.0 GB"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by alfu on 2009-11-12
In trying to back up some large files (> 4.0 GB) to a USB HDD, I get this error at the 4.0 GB point:

[INDENT][FONT="Courier New"]"There was an error copying the file into /media/Dox.BAK
   Show more details
Error writing to file: File too large"[/FONT][/INDENT]

The mainboard I am upgrading to has only one IDE port, so the two cable positions are filled -- I'm booting from the CDROM with 9.04 Live CD and trying to suck files off an older IDE HDD onto a modern USB SATA drive with plenty of space on it.

Anyone know if this is a Ubuntu file size limitation, or something else, and how to get around it?

Yes, it is formatted Fat32 to make it compatible with Mac OS9 and Win2000.  I will see if formatting it NTFS instead will get around this, and post the result.

---

### Post by qamelian on 2009-11-12
> **alfu said:**
> In trying to back up some large files (> 4.0 GB) to a USB HDD, I get this error at the 4.0 GB point:
[INDENT][FONT=Courier New]"There was an error copying the file into /media/Dox.BAK
   Show more details
Error writing to file: File too large"[/FONT][/INDENT]The mainboard I am upgrading to has only one IDE port, so the two cable positions are filled -- I'm booting from the CDROM with 9.04 Live CD and trying to suck files off an older IDE HDD onto a modern USB SATA drive with plenty of space on it.

Anyone know if this is a Ubuntu file size limitation, or something else, and how to get around it?
What filesystem is on the USB drive? If the drive is formated to fat32 for some reason, that will be the root of your problem as fat32 doesn't allow files larger than 4GB. The same limit may apply to some other filesystems as well.

---

### Post by scragar on 2009-11-12
What file system is on the USB HDD?
```
sudo fdisk -l
```

---

### Post by XCan on 2009-11-12
> **qamelian said:**
> if the drive is formated to fat32 for some reason, that will be the root of your problem as fat32 doesn't allow files larger than 4gb. The same limit may apply to some other filesystems as well.

+1

---

### Post by CharlesA on 2009-11-12
The drive is formatted FAT32.

---

### Post by oldfred on 2009-11-12
NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

Phoronix comparison of Formats for USB Flash Drives
[http://www.phoronix.com/scan.php?page=article&item=linux_usb_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_usb_fs&num=1)

---

