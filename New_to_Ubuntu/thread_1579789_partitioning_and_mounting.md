---
title: "partitioning and mounting"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by jimpy on 2010-09-22
hello i am a bit unsure about the mounting of partitions in the installation.

I manually created the partitions i needed for ubuntu (swap, root and home). 

On the ubuntu dual boot help it says i need to create a mount point for my windows partition. I guess this is so ubuntu can see and use the windows partition? Do i need to create a mount point for other non-ubuntu partitions i want access to from within ubuntu?
   if so what file label and mount label should i use for them in the manual partition section of the installation?

thanks

---

### Post by Arla on 2010-09-22
So it really depends, I don't bother creating mount points for any of my windows stuff, and just mount it ad-hoc when I need it (very simple, just double click it in Nautilus) if you need it all the time (say your data folders) then yes, might be worth mounting them, you can pretty much mount them wherever you want, I mount my data at /media/data just following the convention that Ubuntu uses for mounting partitions/drives in general.

---

### Post by indytim on 2010-09-22
> On the ubuntu dual boot help it says i need to create a mount point for my windows partition.

You do not need to create the mount point UNLESS you plan on accessing windows files while you are using Ubuntu.

For a consistent mount, while you are installing, select the manual partition option as you have done already.

For your Windows partition(s), select the partition and click the "Edit" button.  Identify the type of partition as NTFS and identify the mount point.  

If you want your NTFS partition to appear as an icon on your desktop, then you will identify the mount point as something like this
```

/media/WinXP

```

If, on the other hand you are adverse to a lot of clutter on your desktop, identify the mount point somewhere else (I use /mnt) as in

```

/mnt/WinXP

```

[COLOR="Red"]**Make sure you DO NOT check the FORMAT checkbox on this partition or else bye-bye Windows!**[/COLOR]

Save your changes and proceed.

-IndyTim / DataMan

---

### Post by jimpy on 2010-09-22
ok thanks for the help

---

### Post by Mark Phelps on 2010-09-23
My personal advice, which others would disagree with, is NOT to mount MS Windows OS partitions read/write in fstab.

I used to to that myself, then I started experiencing forced CHKDSKs on rebooting into MS Windows.  This got to the point that it was happening nearly every time.

I removed the entries from fstab and changed to mounting and unmounting only when needed using Places.  After doing that, the CHKDSKs stopped.

Your machine ... your choice.

---

