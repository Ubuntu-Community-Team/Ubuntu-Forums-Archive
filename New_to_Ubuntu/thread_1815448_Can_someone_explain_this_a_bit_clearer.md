---
title: "Can someone explain this a bit clearer?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by c.lennox on 2011-07-31
*"In MS-DOS and windows file systems, drive letters represent different storage devices ...[...]... In Linux, all storage devices are fit into the file system hierarchy..."* - Quote : [SIZE="1"]**"Linux Bible - 2008 edition - Chris Negus - ISBN 978-0-470-23019-0 - page 67"**[/SIZE]

[SIZE="2"]I think this means that say if i plugged a USB Flash drive in for example, that it does not need to be assigned a drive letter, and instead appears as a new folder/directory?

If i understand correctly... Would this mean that where windows systems only have 26 letters availible (and thus a maximum of 26 volumes can be used, including cdroms, usb devices, and network drives/shares), Linux can keep going as it just add's the new device into the file system as a new folder/file/directory, and there is the potential to have an unlimited amount of device's attached?[/SIZE]

---

### Post by CatKiller on 2011-07-31
Pretty much.

I don't think Windows is limited to 26, though. I think if you try really hard you end up with AA: and so on.

EDIT: actually it looks like you get numbers instead of double letters after 26 in Windows.

---

### Post by coffeecat on 2011-07-31
> **c.lennox said:**
> I think this means that say if i plugged a USB Flash drive in for example, that it does not need to be assigned a drive letter, and instead appears as a new folder/directory?

It's also important to distinguish device nodes and mount points in Linux, both of which appear in the file hierarchy.

To take your example, when you plug your flash drive in, the kernel will assign device nodes, one for the device and one for each partition. Let's say you already have two internal hard drives, sda and sdb, the kernel will assign the device node /dev/sdc to the flash drive as soon as it detects its presence and /dev/sdc1 to the first partition on it.

In Ubuntu, another part of the system (udev) will create a mountpoint. Let's say the partition sdc1 has the label "FLASH". The mountpoint /media/FLASH will be created dynamically and /dev/sdc1 mounted to that mountpoint, so that you can access partition sdc1's contents through the filesystem at /media/FLASH.

Everything in Linux/Unix is a file.

---

