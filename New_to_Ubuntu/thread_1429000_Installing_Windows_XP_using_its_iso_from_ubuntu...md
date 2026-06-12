---
title: "Installing Windows XP using its iso from ubuntu.."
date: 2010-03-13
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-13
How to install Windows XP from Ubuntu using its ISO image?Can it be done using **Grub4Dos**?

---

### Post by sandyd on 2010-03-13
> **getyourkarthick said:**
> How to install Windows XP from Ubuntu using its ISO image?Can it be done using **Grub4Dos**?
virtrualbox?

---

### Post by karthick87 on 2010-03-13
Already i have tried virtual box,i would like to try something new..

---

### Post by sandyd on 2010-03-13
burn it to cd,
then boot ubuntu livecd, open gparted and resize the ubuntu partition to make space for windows.

format it as ntfs

get the winxp cd in the drive
boot from it.

install it onto the ntfs partition you just created (make sure your not messing with any parttiions deemed "unknown" bu the installer.

set up windows

boot from the linux livecd
```

sudo fdisk -l
```
make note of your ubuntu partition (the /dev/sdaxx) part. in the next step, replace /dev/sdaxx with your ubuntu partition

```

sudo mount -t ext4 /dev/sdaxx /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt

```
```

grub-install /dev/sda
update-grub
```

boot up back into ubuntu, run
```

update-grub
```

---

