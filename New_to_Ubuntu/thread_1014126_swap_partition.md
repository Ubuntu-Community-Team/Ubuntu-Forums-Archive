---
title: "swap partition"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by OllieGab on 2008-12-17
I realised, a while after installing Ubuntu (on a disc already containing Windows), that maybe I should have made my swap partition a little bit larger (it's now 127MB with a memeory of 1.5G).
So I booted up in Windows, used a Windows application to make the Windows part of the HD a little bit smaller. This gave me some "empty" space.
After booting up in Linux again I used gparted to try to resize my swap partition. However, it was only possible to make the partition smaller - not bigger...and "into" the un-used space as I thought it would.
I also wasn't able to delete the existing one -  thinking that I would be able to create a new swap partition, filling out the available space on the HD.
I am obviously doing somthing wrong....

Ollie

---

### Post by xjcannonx on 2008-12-17
What windows application did you use? can you reverse that and just resize windows with gparted?

---

### Post by OllieGab on 2008-12-17
What the Windows application is called I can't recall as I have uninstalled it (and I tried several) but I was not able to re-size the Windows partition with gparted and I don't seem able to "touch" the Linux part of the HD.
Haven't got enough experience to know if this is normal...

---

### Post by drs305 on 2008-12-17
You should be able to delete the existing one via gparted after you have highlighted the partition and then selected Partition, Swapoff. It must be unmounted. If gparted doesn't give you that option, open a terminal and run:
```

sudo swapoff -a

```
You should be able to delete that partition and create a new swap partititon in the larger unused space.

Once you have done that, run "sudo blkid" and place the swap's new UUID into the swap listing in fstab, if it is identified by UUID.

You would also want to update the resume image by making sure the swap uuid in the following file is correct:
```

gksudo gedit /etc/initramfs-tools/conf.d/resume

```

If it changed, then run:
```

sudo update-initramfs -u 
sudo swapon -a

```

---

