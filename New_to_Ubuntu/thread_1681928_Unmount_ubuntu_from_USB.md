---
title: "Unmount ubuntu from USB"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by angelazou on 2011-02-05
Hi all,

  I tried to install Ubuntu on a USB by following the instructions at your website's main page. However, now that OSE Virtualbox doesn't boot from USB, I have to figure out how to remove those files and make the USB unbootable to store other types of data, or just to undo everything and make it a simple USB.

Regards,
Angela

---

### Post by fabricator4 on 2011-02-05
Just format the USB drive under the OS of your choice and it will be ready to accept any data you copy to it.

---

### Post by angelazou on 2011-02-24
Hi,

  Thanks for the reply, however, once I added the Ubuntu disk using 'sudo dd' command, now the USB is not formattable at all! I can't erase the disk or partition it using the Disk Utility. I don't really know what should I do now...

Regards,
Angela

---

### Post by fabricator4 on 2011-02-24
What error messages are you getting, or what is it doing?  Start Disk Utility:

1. Select the USB drive.  Make sure you've got the right one.
2. Select the first partition on the drive.
3. Click on "Unmount Volume".
4. Repeat 2 & 3 for any other partitions
5. Select each partition and delete it. Note: you can probably do this as you unmount each one if you wish.
6. Select unallocated space
7. Add a partition, using the whole drive.
8. Format the partition using the FS type of your choice eg FAT32, ext2 etc.

The only time I've had trouble was with a new USB drive that was formated in the factory as W95 FS (Verbatim Store'n'Go 4GB). It seemed to take a bit of juggling to delete the partition. My memory is a bit hazy, but I think I had to unmount the partition in terminal, Disk Utility couldn't do it for some reason.


Chris.

---

