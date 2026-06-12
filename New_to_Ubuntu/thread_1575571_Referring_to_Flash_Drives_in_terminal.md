---
title: "Referring to Flash Drives in terminal"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by FredVanH on 2010-09-15
Hi.  I want to Shred the contents of a flash drive.  The command Shred runs in Terminal.  If I want to go to a directory on the hard drive I use the "cd" command with the directory name.  How do I "go to" the flash drive?
Thanks for any help,
Fred

---

### Post by CharlesA on 2010-09-15
It's seen as just another disk.

```
sudo fdisk -l
``` 

Should show it, and then you just need to "shred" it.

---

### Post by papibe on 2010-09-15
Chances are it was automounted either on /media or ~/.gvfs.

In order to check all mounted devices do this:
```
$ mount -l
```
if it got recognized but not mounted on the desktop try this:
```
$ sudo fdisk -l
```

Good Luck!

---

### Post by ezhik on 2010-09-15
Flash drives are ussualy mounted into /media directory. If I have pen drive that is called "mydrive" I can access it by
```

cd /media/mydrive

```

---

### Post by HermanAB on 2010-09-16
ls /media
cd /media/whatever

However, 'shredding' is quite useless, especially on a flash drive.  Just format the thing - since that will erase it:
plug disk in
dmesg
mkfs.vfat /dev/sdb1

---

### Post by FredVanH on 2010-09-16
:)All good stuff.  If I don't use it all now, I certainly will later.  Thanks a lot to all of you!
Regards,
Fred

---

