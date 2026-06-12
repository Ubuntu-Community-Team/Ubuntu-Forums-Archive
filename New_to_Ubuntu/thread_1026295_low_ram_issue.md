---
title: "low ram issue"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Clean1414 on 2008-12-31
im working on someones pc, they put a bunch of viruses on their computer with windows xp. i then removed xp and in its place i installed ubuntu 8.10 x64, the system lags horribly when opening about two applications at once (it has 300mb of DDR 400MHz ram and they dont want to buy more ram). my question is there any way i could move the swap file to a different hard drive and increase the size of said page file? if so how? thanks in advance

---

### Post by handydan918 on 2008-12-31
> **Clean1414 said:**
> im working on someones pc, they put a bunch of viruses on their computer with windows xp. i then removed xp and in its place i installed ubuntu 8.10 x64, the system lags horribly when opening about two applications at once (it has 300mb of DDR 400MHz ram and they dont want to buy more ram). my question is there any way i could move the swap file to a different hard drive and increase the size of said page file? if so how? thanks in advance

Yeah, you can put a swap partition wherever you want to. If the standard live cd doesn't allow it, try the alternative install cd, it allows much more granular control.

You can use gparted to create a swap partition, and just delete the old one and edit fstab to point to the new one.

---

### Post by cdtech on 2008-12-31
You can have your swap partition anywhere and can even share the windows page file. As handydan918 suggested, you could reinstall Ubuntu and increase the size. 

If you don't want to reinstall, Linux also supports a swap file that you can create, prepare, and mount in a fashion similar to that of a swap partition. The advantage of swap files is that you don't need to find an empty partition or repartition a disk to add additional swap space.

To create a swap file, use the dd command to create an empty file. To create a 1GB file, type:
```
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```

/swapfile is the name of the swap file, and the count of 1048576 is the size in kilobytes (i.e. 1GB).

Prepare the swap file using mkswap just as you would a partition, but this time use the name of the swap file:
```
mkswap /swapfile
```

And similarly, mount it using the swapon command:
```
swapon /swapfile
```

The /etc/fstab entry for a swap file would look like this:
```
/swapfile       none    swap    sw      0       0
```
Just some information for thought............

---

### Post by beastrace91 on 2008-12-31
If I am correct you might also want to consider installing Xubuntu, as it is a more light weight version of *buntu for slightly slower system.

~Jeff

---

### Post by sirebral on 2008-12-31
I second what beastrace said.  I am looking into Xubuntu now because I want it on my Mini 9.

---

