---
title: "PLease help me"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by coolpete on 2009-03-01
Please help me i cannot access files from the dvd-rw ? there  r lots of pics& vids contained in it. wat is thereason behind it? iam using the latest version 8.10 . Please reply asap.:(

---

### Post by kahlil88 on 2009-03-01
Can your drive read any optical discs, or is it specifically this one disc? Is the disc scratched on either the top or bottom? What kind of disc drive is it?

---

### Post by coolpete on 2009-03-01
well it is a UDF file system iam using Matishita dvd ram drive. well it reads in vista so y it is not reading in ubuntu:confused:

---

### Post by clive littlewood on 2009-03-01
Hi

It is posible that your DVD-Rom is not mounted in Ubuntu.

Copy and paste the following in a terminal Apps > Accessories > Terminal.

To mount :   sudo mount /media/cdrom0/ -o unhide

To unmount :  sudo umount /media/cdrom0/

Also if the DVD was burnt in Vista then it is posible that Ubuntu will not recognise the format (just a guess as i do not transfer between os's)

Hope this helps      :P

Clive

---

### Post by linux_tech on 2009-03-01
If you click on place in the menu then cd/dvd does it open a new window?

---

### Post by t0p on 2009-03-01
> **linux_tech said:**
> If you click on place in the menu then cd/dvd does it open a new window?

Indeed. It would be made infinitely easier for us to help you if you posted the exact error message/exactly what happens when you try to load a disk. Just saying "It doesn't work" means nothing.

---

### Post by kahlil88 on 2009-03-01
I think you have to install a driver for UDF.

---

### Post by coolpete on 2009-03-02
hey clive ya it is burned in vista i typed the following command in terminal first command showed n o medium found, second command showed no sign of reply. which driver should i install kahill88?. Please reply:(

---

### Post by Buffalo Soldier on 2009-03-02
[http://en.wikipedia.org/wiki/Universal_Disk_Format#Why_a_computer_might_not_read_a_particular_UDF_disk](http://en.wikipedia.org/wiki/Universal_Disk_Format#Why_a_computer_might_not_read_a_particular_UDF_disk)

It seems Universal Disk Format (UDF) is a **relatively** new format. It is intended as a replacement for the current ISO standard for optical storage, ISO 9660.

> Even if an operating system claims to be able to read UDF 1.50, it still may only support the plain build and not necessarily either the VAT or Spared build.

An example is Mac OS X (10.4.5), which claims to support UDF 1.50 (see man mount_udf), yet it can only mount disks of the plain build properly (it cannot mount UDF disks with a VAT at all, see Sony Mavica problem, and while it appears to be able to mount CD-RWs written with a Sparing Table, it does not read its files correctly in the case those files are actually remapped).

The solution is to update the computer’s operating system (OS) to any later version of the OS, available without charge up to version 10.4.11 for both Intel and PowerPC Macintosh computers.

Similarly, Microsoft Windows XP Service Pack 2 (SP2), cannot read DVD-RW disks that use the Universal Disk Format (UDF) 2.00 defect management system. When you view the DVD contents by using Windows Explorer, you see an empty root folder. This problem occurs if the UDF defect management system creates a sparing table that spans more than one sector on the DVD-RW disk. Windows XP SP2 cannot read a sparing table that is larger than one sector. Windows XP SP2 can recognize that a DVD is using UDF. However, Windows Explorer displays the contents of a DVD as an empty folder.

---

### Post by mikechant on 2009-03-02
Some discs need to be 'finalized' in Windows before you can read them in non-Windows systems. I think (but I'm not sure) that the finalize option appears on the 'file' menu in Windows Explorer when you have a disc inserted which has data on but is not finalized.

---

