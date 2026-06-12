---
title: "Cannot Mount Volume"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by RealG187 on 2009-09-17
I get this error when I plug in my NTFS USB Drive (500 GB SATA drive in USB enclosure)

[SIZE="6"]Cannot mount volume.[/SIZE]
Unable to mount the volume 'Backup2'.

Details
[COLOR="Red"]After clicking the arrow besides details[/COLOR]
Cannot get volume.fstype.alternative

---

### Post by RealG187 on 2009-09-17
sudo mount /dev/sdc1 /media/Backup2 -t ntfs-3g

That seemed to do it, usually when it failed to mount it gives me the command, I had to find out for myself this time...

---

### Post by RealG187 on 2009-09-18
Okay I thought if I mounted it with that command once it would go away, but after unmounting and plugging it back in it asks me everytime, using the command to mount is only a temporary fix...

It even does it for another NTFS Drive I have...

---

### Post by Bucky Ball on 2009-09-18
Have you actually run ntfs-3g from the drop down menus? This will identify whatever ntfs partitions it can find and ask you if you want them added to your fstab. That will auto-mount the partition at boot. 

You can also alter the fstab manually:

```
# /dev/sdb6
**UUID=48AF-C7CD**                            **/media/your_ntfs_partition**  auto   defaults,user,users,dmask=0000,fmask=1111   0   0
```

Easier with ntfs-3g but if you want to do it manually something like that might work but you need to change the parts in bold to the correct UUID and path. You can get the correct UUID with:

```
sudo blkid
```

---

### Post by RealG187 on 2009-09-18
Before I never had to run an command or edit the /etc/fstab fiile for an NTFS drive... I don't wanna have to do it everytime I plug in an new NTFS drive...

---

### Post by Bucky Ball on 2009-09-18
What I'm saying is if you actually run ntfs-3g it will take care of it for you VERY easily and you only need to do that once. 

If you don't have it installed open Synaptics and search for 'ntfs-3g' then install. It will then be in one of you drop-down menus (can't remember which but you'll find it). Just run, it will find the partitions, you choose which ones you want added to fstab, click okay and it will re-write the fstab for you. That easy.

---

### Post by RealG187 on 2009-09-18
mpg@MIKED6:~$ ntfs-3g
ntfs-3g: No device is specified.
Please type 'ntfs-3g --help' for more information.
mpg@MIKED6:~$

---

### Post by Bucky Ball on 2009-09-18
Sorry, install 'ntfs-config'. That will give you the GUI. If you want to know the correct syntax for using it from a terminal run ntfs-3g --help like it says. It's all there.

---

### Post by RealG187 on 2009-09-21
> **Bucky Ball said:**
> Sorry, install 'ntfs-config'. That will give you the GUI. If you want to know the correct syntax for using it from a terminal run ntfs-3g --help like it says. It's all there.

I have ntfs-config
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

Hmm, looks like when I ran it and selected "Enable write support for external drives" it worked. I originally installed it to automount an internal NTFS partition, so external there was off by default. Looks like the default settinng wasn't the best one...

---

