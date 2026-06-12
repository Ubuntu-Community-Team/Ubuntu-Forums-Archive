---
title: "no write access to a mounted usb disk"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-09-02
I am beating my head here...!

i have an external 200GB seagate usb drive.
It shows up in the device notifier (in kubuntu) and also in dolphin.  I can see it and it has mounted.

I just cannot seem to get write permission to it.

Here is the output from doing a "mount -l"

```
/dev/sdd1 on /media/seagate type ext3 (rw,noexec,nosuid,nodev)
```

here is the output from fdisk -l
```
Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf96c5dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24321   195358401   83  Linux

```

BTW, I formatted the drive as EXT3.   Its not a windows drive (NTFS).

Any ideas?
thks

---

### Post by gatorbrit on 2009-09-02
I think i solved it....

```
sudo chmod 777 /media/seagate
```

It appears that I can write to the drive now.   Don't know why I couldn't before...

---

