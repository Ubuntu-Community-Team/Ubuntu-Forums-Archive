---
title: "cannot unmount windows (hp backup) partition"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by rsv.suresh on 2010-07-25
hi guys,in my dual boot laptop(Compaq with windows and Ubuntu 10.04), I have two windows partitions
one is hp backup partition and other is the file system in windows. I tried to share windows files in Ubuntu with ntfs-config, but now the problem is I can only see the hp backup partition on my desktop. When I try to unmount it I could not. My question is how can I unmount the hp backup partition permanently and mount the other partition for file sharing in Ubuntu, I almost forgot..I have also uninstalled ntfs configuration tool.thanks/

---

### Post by Morbius1 on 2010-07-25
Please post the output of the following commands so we can all see what's up:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by rsv.suresh on 2010-07-25
output for 
 ```
sudo blkid -c /dev/nul
```
/dev/loop0: UUID="b5c510b3-43e3-49b0-858c-ff437717070d" TYPE="ext4" 
/dev/sda1: UUID="600C00CB0C009E62" TYPE="ntfs" 
/dev/sda2: LABEL="PRESARIO_RP" UUID="2C88743C8874071C" TYPE="ntfs" 

and output for ```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/host	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
/dev/sda2	/media/PRESARIO_RP	ntfs	defaults,nls=utf8,umask=0222	00
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0

---

### Post by Morbius1 on 2010-07-25
Um ... this looks like a Wubi install to me - You installed Ubuntu within Windows? I don't know very much about Wubi but I think the host Windows partitions are already mounted for you at:
> /host
/media
You don't need to have anything else mounted in fstab.

If I were you I would change the title of your post to include the word Wubi so that someone who has experience with that can respond.

---

### Post by rsv.suresh on 2010-07-25
thanks for the reply morbius1. I'll change the title to wubi.

---

### Post by wilee-nilee on 2010-07-25
If your trying to use this method as a longterm use your going about in a a manner that is balancing on the Windows program always working, not good odds. The two OS can have stuff transferred, but a real dual boot would be a better option.

---

