---
title: "Remove Live CD boot entry?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Thilo Kuhlman on 2009-01-28
I booted from a Live CD on a new Acer Computer to see if it works...
it did, but also left a boot entry, that directs it towards the CD, which I don't need.
How do I delete this boot entry?
Many people I have talked to think Ubuntu 8.10 made a small boot partion on my harddrive. 
I don't know.
Any help?
:)

---

### Post by drs305 on 2009-01-28
To see if there is a /boot partition, run this:
```
sudo fdisk -l
```

Are you saying that you installed ubuntu and now you see a menu item for the CD during boot?  If so, post the results of this:
```
cat /boot/grub/menu.lst
```

---

### Post by Thilo Kuhlman on 2009-01-28
Is their anyway I can simply remove it through Windows?
Thanks.

---

### Post by drs305 on 2009-01-29
I still am not sure where the boot entry you are referring to is. There are ways to view ext3 files from within Windows. One such method uses an app called ext2fs/ext2fsd. 

If you can see the linux files and can find /boot/grub/menu.lst, you should be able to use ext2fs/ext2fsd to open the file and edit the menu.lst if it contains the entry you are seeking to eliminate.

[Ext2 File System Driver for Windows: FAQ for Ext2fsd]("http://sourceforge.net/docman/display_doc.php?docid=12211&group_id=43775")

---

### Post by cariboo on 2009-01-29
Can you show us a screenshot of this "LiveCD boot" entry. The LiveCD doesn't make any changes to your system unless you tell it to. How did you start the LiveCD, did you boot from it, or did you start it up inside Windows? If you started it from inside windows, you have more than likely done a wubi install.

Jim

---

