---
title: "[SOLVED] Corrupted Hard Drive"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by cmo220 on 2008-12-21
I have an external ext3 formatted Hard Drive with all my music, and videos on it.  I usually access it through windows.  Yesterday, When I wanted to browse through it windows told me it was corrupted and unreadable.  I'm Looking for a way to get that stuff off of that drive.  How would I be able to access the info using linux.  Thanks.

---

### Post by w4ett on 2008-12-21
Is the Drive accessible in Linux?  How are you reading the ext3 drive from windows, EXT2Ifs?

---

### Post by northern lights on 2008-12-21
Plug it into your machine. Boot into Linux. Should be automounted in /media/ and appear under the Places menu in gnome. If not you can manually mount the device:

Run ```
blkid
```pick the correct device and remember its name (/dev/sXX)Subsequently run
```
sudo mkdir /mnt/ExternalHDD/
sudo mount /dev/sXX/ /mnt/ExternalHDD/
```

(where the XX needs to be replaced by the respective figures...)

---

### Post by cmo220 on 2008-12-21
Yes, I'm using ext2IFS, and it is available under ubuntu.  I'm not going to have a drive to back up everything to until christmas tho.  Is there any thing anyone knows I can do to make it readable in windows now?

---

### Post by w4ett on 2008-12-21
I would try to uninstall ext2ifs in windows...and then reinstall it.....it is only a tool to access ext2/3..I'd give it another chance :)

---

### Post by cmo220 on 2008-12-21
I really thought I uninstalled it and reinstalled it last night, apparently not tho,  It worked.  Thank You, and everyone else who helped out.

---

### Post by cmo220 on 2008-12-21
Now, how do I mark this thread as solved?

---

### Post by w4ett on 2008-12-21
> **cmo220 said:**
> Now, how do I mark this thread as solved?

It's under "Thread Tools"

---

