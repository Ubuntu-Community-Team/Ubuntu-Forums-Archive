---
title: "can't change the name of a usb drive"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by gatorbrit on 2010-01-12
I have a USB external drive that mounts automatically as "/media/ T"
Yes, there is a space between the second "/" and T.

I want to rename it something more useful like "maxtor"

I tried going to gparted which allowed me to type in a new label but it wouldn't "stick".  I also tried this in the disk utility.  Why won't these changes hold?

I basically followed the instructions here.   [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

The drive is /dev/sdc5 and is formatted vfat

Thanks

---

### Post by Unlimited Bit on 2010-01-12
Had the same problem a while ago - the only workaround I found was to unmount it and change the label from the *format* dialog.

---

### Post by philinux on 2010-01-12
> **gatorbrit said:**
> I have a USB external drive that mounts automatically as "/media/ T"
Yes, there is a space between the second "/" and T.

I want to rename it something more useful like "maxtor"

I tried going to gparted which allowed me to type in a new label but it wouldn't "stick".  I also tried this in the disk utility.  Why won't these changes hold?

I basically followed the instructions here.   [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

The drive is /dev/sdc5 and is formatted vfat

Thanks

Plug in the usb drive. Then right click it and choose unmount.

Now, system>Admin>disk utility. Click the usb drive and then change the label for it to what you need.

---

