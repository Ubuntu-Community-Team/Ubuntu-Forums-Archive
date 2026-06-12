---
title: "mount and browse sda2.ntfs-img a backed up ntfs partition (made by clonezilla)"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by baybe1111 on 2009-01-24
Hi, really stuck on this- so are others I think, but no replys for weeks.. trying to uncompress, mount and browse a backed up ntfs partition (made by clonezilla) from my laptop into my external USB drive. I've >80G free there and its ext3 format (NTFS partition was ~50 gig). Where clonezilla created the image is where I'm trying to extract it.

I get the error in the first attempt so I removed the .* as my images are single files, but the Permission Denied has me stumped- I'm using sudo- so I'm root right?

andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ dir
disk           Info-packages.txt  sda1           sda-chs.sf     sda-pt.sf
Info-dmi.txt   NTFS               sda2.ntfs-img  sda-mbr
Info-lshw.txt  parts              sda3.ntfs-img  sda-pt.parted
andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ sudo cat sda2.ntfs-img.* | gzip -d -c | ntfsclone --restore-image -o sda2.img -
ntfsclone v1.13.1 (libntfs 9:0:0)
cat: sda2.ntfs-img.*: No such file or directory

gzip: stdin: unexpected end of file

andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ sudo cat sda2.ntfs-img | gzip -d -c | ntfsclone --restore-image -o sda2.img -
ntfsclone v1.13.1 (libntfs 9:0:0)
ERROR(13): Opening file 'sda2.img' failed: Permission denied
andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ sudo cat sda2.ntfs-img | gzip -d -c | ntfsclone --restore-image -o sda2.img -

---

### Post by yeats on 2009-01-24
> Hi, really stuck on this- so are others I think, but no replys for weeks..

You might get better help on the General Help forum for things like this.  This is mostly novices and beginners trying to help each other get started with the basics. . . .  Sounds like you have much more experience than the people you're asking for help.

That said, you can become root by doing

```
sudo su
```

Then try your command again.  Or you can ls -l to see the owner and permissions level for the file you're trying to access.

---

### Post by baybe1111 on 2009-01-24
OK, will repost to general. Tied your sugestions but still not going. THanks anyway.

---

### Post by cariboo on 2009-01-24
Could you repost your error message using the code tags, your output is to confusing to comment on. Click New Reply on the left side of the page, once in the editor click on the **#** this will give the code tags:

[noparse]```

```[/noparse]

Jim

---

