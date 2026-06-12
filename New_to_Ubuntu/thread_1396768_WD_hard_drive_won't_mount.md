---
title: "WD hard drive won't mount"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by ravendark82 on 2010-02-02
I have a Western Digital 500gb hard drive. I have it connected via firewire and it says that it mounts and will create an icon on the desktop but when I click on it to review the files it says:  

"Error mounting: mount exited with exit code 32: mount: /dev/sdf1: can't read superblock"

I tried connecting it via USB but it does not mount it at all.  I have been using it on Windows XP to manually back up my files at least once a month.  I recently got a nasty virus that I can't seem to get rid of on Windows and chose to install Ubuntu. I cannot currently access the hard drive through Windows on my machine. I have several USB and firewire ports but Windows will not look in the correct one. I usually use my drive in drive E but Windows keep looking in drive J and then saying the drive is corrupted.  I am wondering if this has something to do with why it is not working in Ubuntu.  Perhaps the virus did something to my drive and if it did, how do I get Ubuntu to read the data?  Thank you for any help you can provide.

---

### Post by skatinjj on 2010-02-02
I would connect via USB then open a terminal and run:

```
sudo fdisk -l
```

Find what device it is (i.e /dev/sdb)

then run:
```
sudo mount /dev/sdb /media
```

Just replace /dev/sdb with whatever device yours is.
An icon will appear on the desktop for the device once it mounts.

To unmount run:
```
sudo umount /media
```

---

