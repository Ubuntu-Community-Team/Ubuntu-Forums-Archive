---
title: "Everything is messed up!"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-08-28
Hello all,
I am very disappointed that something like this is happening!
But just to explaine:
I've installed KernelCheck and give it a try!
Everything was going well but I don't know what happened that the addons on Firefox stoped working without restart, also the theme, also I can't make printscreen, in Places the Picture,Documents,Videos etc has dissapeared, pidgin is not connecting.
  When making pritscreen:```
Imposible to save the screenshot to file:///home...Error was Error writing to file:No space left on device.Please choose an other location or retry.
```

For example in Firefox if I go to Tools Addons and push it the application is killing.

And I am sure that are more problems but i didn't discovered them yet.

Can anyoane help me to resolve this problem?

Thanks you!

I have Ubuntu 9.04 and I didn;t have any problems so difficult!

---

### Post by zkriesse on 2009-08-28
If you have a Live CD stick it in and use the repair system option. See if that helps.

---

### Post by Penguin Guy on 2009-08-28
> **vasiauvi said:**
> ```
Error writing to file:No space left on device.
```
It looks like your HDD is full, to confirm this please post back the results of [COLOR="Green"]sudo fdisk -l[/COLOR].

---

### Post by vasiauvi on 2009-08-28
Output of sudo fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8d32665

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100       11714    53126955    7  HPFS/NTFS
/dev/sda6           11714       14504    22418644+   b  W95 FAT32
/dev/sda7           14505       15951    11622996    b  W95 FAT32
/dev/sda8           15952       19306    26949006   83  Linux
/dev/sda9           19307       19457     1212876   82  Linux swap / Solaris

```

---

### Post by vasiauvi on 2009-08-28
I've entered in 
/home/usr/src/
where the linux-2.6.30 kernel was compiled and the folder with the kernel has 3Gb.
How is this possible?

If I don't want to use this kernel anymore can I delete the folder? :confused:

---

### Post by vasiauvi on 2009-08-28
Ok, I'm filling so stupid.
Thanks Penguin Guy, i really didn't have any more space on the drive after i've compiled the kernel. 
But it shouldn't announce me that I'm remaining without space?
In Windows there is this feature to announce when you have the disk full.

I am glad that now it's OK.
But one question though: how can I remove a kernel that i don't use anymore?

Thank you and sorry for this!

---

### Post by muteXe on 2009-08-28
That error message DID tell you you've got no space.

---

### Post by jrox717 on 2009-08-28
>  But one question though: how can I remove a kernel that i don't use anymore? 

In Synaptic, search for the old kernel and delete it. Just make sure you don't uninstall your current kernel. And it's sometimes good to keep one around just in case.

---

