---
title: "USB stick troubles"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by arpeggi on 2009-10-04
ello all, 

i'm having a bit of trouble with my 16gb usb stick. i don't really care for the content currently on there so wouldn't mind a straight format. when i try to edit/delete any of the content on there or add content i get the error that it's a read only file system. i have a feeling it might be formatted in ntfs but not really sure where t go from here.

i know it's probably a super easy problem but i'm a bit of a newbie with these things :P

---

### Post by t0p on 2009-10-04
It could be that some data on the stick has been corrupted.  If that happens, Ubuntu will often mount the drive read-only to protect the rest of the contents.

I would advice backing up what you can then reformat the stick.

---

### Post by wilee-nilee on 2009-10-04
You can do several things, you can change it to read and write, you can also look at how it is formatted with partition manager and reformat there as well. It probably is formatted fat32; which is what you want if you reformat.

---

### Post by corncob on 2009-10-04
> **arpeggi said:**
> 
i'm having a bit of trouble with my 16gb usb stick. i don't really care for the content currently on there so wouldn't mind a straight format. when i try to edit/delete any of the content on there or add content i get the error that it's a read only file system. i have a feeling it might be formatted in ntfs but not really sure where t go from here.


If somehow you have any problems with partition manager and still have a Windows machine, put the stick in there and format it.  Just don't use FAT16 as it only supports 2 GB.

---

### Post by arpeggi on 2009-10-04
ok when i go into gparted i get this error:

[INDENT][B]The kernel is unable to re-read the partition tables on the following devices:
- /dev/sda[/B]

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access.[/INDENT]

even when i unmount the usb drive i'm getting the same error. i don't care about the contents of the drive all i'm looking to do is format.

---

### Post by wilee-nilee on 2009-10-04
> **arpeggi said:**
> ok when i go into gparted i get this error:

[INDENT][B]The kernel is unable to re-read the partition tables on the following devices:
- /dev/sda[/B]

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access.[/INDENT]

even when i unmount the usb drive i'm getting the same error. i don't care about the contents of the drive all i'm looking to do is format.
Are you sure that your looking at the Thumb Drive in Gparted the upper right corner drop down gives you a choice as to what your looking at.

---

### Post by arpeggi on 2009-10-04
yep definitely. i get that error as soon as i load up.

well after another attempt i've managed to format the device and it's working fine. will let you know if i have any troubles with it. thanks for the input guys!

p.s another quick question - how do i rename usb devices in ubuntu?

---

