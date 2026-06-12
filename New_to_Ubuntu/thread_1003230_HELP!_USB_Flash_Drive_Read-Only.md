---
title: "HELP! USB Flash Drive Read-Only"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by UserDemos on 2008-12-05
Hello all,

Recently, I found my flash drive was read-only and I could not delete anything. I can't even change the permissions as Ubuntu tells me that "the permissions could not be determined."

I've tried all of the advice in the forums: chmod, chown, and more. I even tried deleting it and starting over. No avail.

Can someone help me? Pretty please. Much appreciated and huge thanks in advance!

---

### Post by taurus on 2008-12-05
Is it fat32/vfat or ntfs filesystem?

```
sudo fdisk -l
```

---

### Post by UserDemos on 2008-12-06
This is the output I got:

[INDENT]   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              14        6616     1980416    b  W95 FAT32
[/INDENT]

So, I think it's Fat32. I think I also copied the right unit on that screen. Any more info needed?

Again, the help is so appreciated.

---

### Post by UserDemos on 2008-12-06
Anyone have any ideas? I could really use the help.

---

### Post by taurus on 2008-12-06
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by UserDemos on 2008-12-06
Should I put this into the terminal editor as one chunk or line by line? Additionally, should I do it when the USB is within the port? 

I tried the line by line and USB within the port and nothing changed. Everything was still read only. 

Did I make a mistake? Thanks for sticking with me and helping so far Taurus.

EDIT: My flash drive has auto-mounted always under media/disk. Does this change anything? It's just always been read-only.

---

### Post by taurus on 2008-12-07
Try unmounting it first and then remount it.  And yes, type in one line at a time by hitting the Enter key.

```
sudo umount /media/disk  [COLOR="Blue"][Enter][/COLOR]
sudo mkdir /media/sdb1  [COLOR="Blue"][Enter][/COLOR]
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000  [COLOR="Blue"][Enter][/COLOR]
ls -la /media  [COLOR="Blue"][Enter][/COLOR]
```

p.s.  Also, make sure you don't accidentally lock the drive.  On some drives, there are a write-protected switch on the side.

---

### Post by UserDemos on 2008-12-09
Hey Taurus,

There is no write protected switch on my drive.

I did all that you coded for me, but unfortunately, it did not remove what was in my trash can (or allow me to) and then when I plugged it in again, it was read-only.

What exactly was that code supposed to do? Would you mind explaining that to me? And, I use another external hard drive that sometimes appears as disk, perhaps there is some confusion between the two?

I appreciate the help so far.

---

