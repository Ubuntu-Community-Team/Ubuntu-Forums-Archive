---
title: "Master Boot Record"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by theozzlives on 2009-07-02
I put my old laptop HD in an external box and formatted it NTFS. Everything went fine except GRUB is still in the MBR. It tries to load but errors out (understandably so). How do I rewrite the MBR so it's just a slave and don't try to boot. I've tried using Gparted to write a new partition table, but I need to write a new MBR.

---

### Post by unutbu on 2009-07-02
You can install the Windows bootloader to the drive using a Windows recovery CD. (I think the command is fixboot). But you have to be careful to specify which drive you want to install the Windows bootloader too. Since I don't know how to do that, I'll direct you to the Linux way of doing it:

[http://ubuntuforums.org/showpost.php?p=4691608&postcount=2](http://ubuntuforums.org/showpost.php?p=4691608&postcount=2)

Or if you wish to just zero-out the MBR (without touching the partition table), run 
```

sudo dd if=/dev/zero of=/dev/sdX bs=446 count=1
```
(change sdX to the appropriate drive name).

---

### Post by theozzlives on 2009-07-02
> **unutbu said:**
> You can install the Windows bootloader to the drive using a Windows recovery CD. (I think the command is fixboot). But you have to be careful to specify which drive you want to install the Windows bootloader too. Since I don't know how to do that, I'll direct you to the Linux way of doing it:

[http://ubuntuforums.org/showpost.php?p=4691608&postcount=2](http://ubuntuforums.org/showpost.php?p=4691608&postcount=2)

Or if you wish to just zero-out the MBR (without touching the partition table), run 
```

sudo dd if=/dev/zero of=/dev/sdX bs=446 count=1
```
(change sdX to the appropriate drive name).

thanx!

---

### Post by ainsworth_t on 2009-07-02
Also try completely erasing the drive and then re-formatting it. [Darik's Boot and Nuke (DBAN)]("http://www.dban.org/") is a very handy tool for erasing hard drives.

---

### Post by theozzlives on 2009-07-03
> **ainsworth_t said:**
> Also try completely erasing the drive and then re-formatting it. [Darik's Boot and Nuke (DBAN)]("http://www.dban.org/") is a very handy tool for erasing hard drives.

Writing zeros to the MBR seemed to take off GRUB, but I appreciate the help. I'm just gonna use it to backup.

---

