---
title: "Set name for mp3 player"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by medic8ted on 2008-12-30
I have edited fstab to set mount point for mp3 player but it mounts as 4.1 GB media.  Is there a way to mount it as a name?  I am using UUID in fstab, it reads 
> 
# /dev/sdc
UUID=0123-4567		/media/disk	vfat	defaults,norelatime,users		0 0
Surely there is a way to mount it as "Sansa Clip"?

---

### Post by cariboo on 2008-12-30
You could use gparted to change the volume label of your mp3 player. If you haven't got gparted installed, it is in the repositories and you can use Synaptic Package Manger and of course the command line to install it. then go to System-->Administration-->Partition Editor.

Jim

---

### Post by medic8ted on 2008-12-30
The model name in gparted shows SanDisk Sansa Clip 4Gb.  Shouldn't fstab be able to name it for the mount point?

---

### Post by cariboo on 2008-12-30
It may not, as deep down Linux doesn't deal well with spaces in names. Maybe try Sansa_Clip and see what happens.

Jim

---

