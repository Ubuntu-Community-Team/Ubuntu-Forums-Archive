---
title: "Issue accessing USB HD"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Natael on 2008-12-20
Well, I chose Ubuntu as my distrobution, am using GNOME. I messed up boot records and partition tables, decided to just reformat my HD, no issue. Now I have Vista 64-bit and Ubuntu 8.10 32-bit running (chose 32 due to hearing there are some issues with 64).

To the specific issue, Linux will not read my USB Hard Drive (WD 500 megs). Vista will read it automatically, when I had Ubuntu installed before it read it automatically. Initially I had issue with reading my windows partition, but I changed fstab (/dev/sda1 /media/windows ntfs default 0 0) and that works fine. Under that in fstab I put "/dev/sdb1 /media/MyBook vfat defaults 0 0" My Book appears under places and in Computer, but when I click on it I get a pop up:

"Unable to mount My Book"
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

When I try:
sudo mount /dev/sdb1/

Mount: /dev/sdb1 already mounted or /media/MyBook busy
Mount: According to mtab, /dev/sdb1 is already mounted on /media/MyBook

When I:
sudo fdisk -l
It shows the sda drives (1 and 2 for windows and linux partions) and then instead of going back to the command line, just stalls, as though it is trying to communicate with sdb1.

Trying to unmount (using umount) it gives me this:

mount: /media/MyBook: device is busy.

So to check out what's going on I run:

fuser -mv /dev/sdb1

/dev/sdb1 orion 5935 f........ nautilus
orion 5947 f......... gvfs-hal-volume

Both are uninterruptable, and I am unfamiliar with them.

---

### Post by eagle416 on 2008-12-20
I don't know much about this sort of thing, but I had the same problem, and I got rid of it simply by rebooting the computer with the device plugged in. Now it works fine. Maybe you could try that. [shrugs]

---

### Post by Natael on 2008-12-21
I tried rebooting, still get the same error.  

Typed dmesg right after plugging it in and got the following(ton of it, so only an excerpt)

Did so, here's an excerpt of what I got:

[ 261.612475] sd 6:0:0:0: [sdb] Sense Key : No Sense [current]
[ 261.612480] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 266.201644] usb 8-2: USB disconnect, address 2
[ 266.201762] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 266.201771] end_request: I/O error, dev sdb, sector 268435400
[ 266.201853] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 266.201860] end_request: I/O error, dev sdb, sector 268435400
[ 266.201873] FAT: Directory bread(block 268435337) failed
[ 266.201917] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 266.201929] end_request: I/O error, dev sdb, sector 268435401
[ 266.201942] FAT: Directory bread(block 268435338) failed
[ 266.201982] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK

...

[ 266.203119] end_request: I/O error, dev sdb, sector 268435421
[ 266.203130] FAT: Directory bread(block 268435358) failed
[ 266.203162] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 266.203171] end_request: I/O error, dev sdb, sector 268435422
[ 266.203183] FAT: Directory bread(block 268435359) failed
[ 266.203195] FAT: Directory bread(block 268435360) failed
[ 266.203204] FAT: Directory bread(block 268435361) failed
[ 266.203213] FAT: Directory bread(block 268435362) failed
[ 266.203221] FAT: Directory bread(block 268435363) failed
[ 266.203229] FAT: Directory bread(block 268435364) failed
[ 266.203237] FAT: Directory bread(block 268435365) failed

---

