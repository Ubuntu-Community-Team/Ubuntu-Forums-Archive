---
title: "How to remove an item from Places menu"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by jarhead8286 on 2009-03-07
I have a menu item in "Places" called RECOVERY.  RECOVERY is a partition name on the laptop that came with my Dell laptop.  Is there a way to remove it from "Places"?

---

### Post by SunnyRabbiera on 2009-03-07
Try to open up nautilus (your file manager) and in the side pane try right clicking on the unwanted item and select "remove"
It might not work though as some items are locked.

---

### Post by jarhead8286 on 2009-03-07
> **SunnyRabbiera said:**
> Try to open up nautilus (your file manager) and in the side pane try right clicking on the unwanted item and select "remove"Can't find how to launch nautilus - please guide.

---

### Post by RiceMonster on 2009-03-07
Nautilus is the file manager, open up your home folder and you've opened up nautilus

---

### Post by SunnyRabbiera on 2009-03-07
The simplest way to open nautilus is to simply open up your home directory under places.
By default when you do this nautilus will open unless you changed things around like use PCmanFM or something.
But since you are new I doubt you have done this :D

---

### Post by mister_pink on 2009-03-07
Unfortunately you can't just delete a mounted partition. If you never want to access it from ubuntu (which is likely) you need to stop it being mounted at boot. 
Open up /etc/fstab for editing, by pressing Alt+F2 and typing
```

gksu gedit /etc/fstab
```

Then remove the line referring to something like /media/RECOVERY. If this doesn't exist then don't do anything. Instead, open a terminal and type "sudo fstab -l" (thats a lower case L) and post the output here, along with the contents of /etc/fstab for further help.

You'll also probably need to delete the directory from /media.
First make sure its unmounted:
```
sudo umount /media/RECOVERY
```
Then remove the directory:
```
sudo rmdir /media/RECOVERY
```

---

### Post by jarhead8286 on 2009-03-07
> **SunnyRabbiera said:**
> Try to open up nautilus (your file manager) and in the side pane try right clicking on the unwanted item and select "remove"
It might not work though as some items are locked.That didn't work; "Remove" was greyed out and mount was the other option.

> **mister_pink said:**
> Unfortunately you can't just delete a mounted partition. If you never want to access it from ubuntu (which is likely) you need to stop it being mounted at boot. 
Open up /etc/fstab for editing, by pressing Alt+F2 and typing
```

gksu gedit /etc/fstab
```

Then remove the line referring to something like /media/RECOVERY. If this doesn't exist then don't do anything. Instead, open a terminal and type "sudo fstab -l" (thats a lower case L) and post the output here, along with the contents of /etc/fstab for further help.

You'll also probably need to delete the directory from /media.
First make sure its unmounted:
```
sudo umount /media/RECOVERY
```
Then remove the directory:
```
sudo rmdir /media/RECOVERY
```

Contents of fstab:
```

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/sda5 /media/NTFS ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

typing "sudo fstab -l" returned command not found.  Did you want me to type "sudo fdisk -l"?

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        1320    10485760    7  HPFS/NTFS
/dev/sda3            1321       38912   301957740    f  W95 Ext'd (LBA)
/dev/sda5            1321       38912   301957708+   7  HPFS/NTFS


```

---

### Post by mister_pink on 2009-03-07
> **jarhead8286 said:**
> 
Contents of fstab:
```

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/sda5 /media/NTFS ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

typing "sudo fstab -l" returned command not found.  Did you want me to type "sudo fdisk -l"?

Doh. Yep. fstab on the brain
> 

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        1320    10485760    7  HPFS/NTFS
/dev/sda3            1321       38912   301957740    f  W95 Ext'd (LBA)
/dev/sda5            1321       38912   301957708+   7  HPFS/NTFS


```

Have you installed with wubi? I've never seen an fstab that looks like that before. At a guess I'd say the recovery partition is sda2, but that doesn't appear in your fstab. What folders exist inside /media?

---

### Post by jarhead8286 on 2009-03-09
> **mister_pink said:**
> 
Have you installed with wubi? I've never seen an fstab that looks like that before. At a guess I'd say the recovery partition is sda2, but that doesn't appear in your fstab. What folders exist inside /media?I did install with wubi.  Inside /media I see NTFS directory.

---

