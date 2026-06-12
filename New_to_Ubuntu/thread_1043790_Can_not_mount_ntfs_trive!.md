---
title: "Can not mount ntfs trive!"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-18
Another problem of mine...
I can not mount my data drive in Ubuntu! Over 100 gigs of data!
I could mount it normally just by clicking on it, but I wanted it to mount at startup so I thought I'll experiment, in the right click menu options, in Volume tab I entered into mount point field: /drive. Unmounted and now when I try to mount it i get an error: mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usally /). OK that is clear, but now when I go to that drive (witch is unmounted) I get diferent window and options - I can not correct or delete what I wrote in the mounting point field because its not there anymore...:(
Help...

---

### Post by taurus on 2009-01-18
If you want to have it mount when you boot Ubuntu, just edit /etc/fstab and add an entry for it.  What filesystem is that drive?

```
sudo fdisk -l
sudo blikd
cat /etc/fstab
df -h
```

---

### Post by Ben Page on 2009-01-18
Now its not important to mount it on startup, just to mount it, how can i do that, or change the mounting point via terminal? I cant see anything that I could edit in fstab and that is related to this drive .

here is the fdisk output, that 120GB NTFS is the problem

```
ben@ben-desktop:~/Desktop$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b6a1b6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       20023   140351872+   f  W95 Ext'd (LBA)
/dev/sda5            2551       17663   121395141    7  HPFS/NTFS
/dev/sda6           19892       20023     1060258+  82  Linux swap / Solaris
/dev/sda7           17664       19891    17896378+  83  Linux

```

---

### Post by honkthrast on 2009-01-18
I would try:

```

mkdir /media/media
sudo mount /dev/sda5 /media/media

```

See if that works for you.

---

### Post by Ben Page on 2009-01-18
Thnx vm, it works perfectly, you saved my evening!\\:D/

---

