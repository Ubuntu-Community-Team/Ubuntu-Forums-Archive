---
title: "removing vista partition"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Wylkar on 2009-01-15
I currently duel boot vista and ubuntu. I don't use the vista partition and I was thinking of getting rid of it and running a different version of windows in virtualbox.
 I was wondering:
a) how to uninstall vista and resize the ubuntu partition.
b) if virtualbox is a viable substitute for a duel boot.
c) if I used the windows 7 beta in virtualbox if it is possible a bug could mess up any/all of my files.
Thanks

---

### Post by jbrown96 on 2009-01-16
I doubt you need to "uninstall" Vista. Obviously, you will need to copy any files that you want preserved to external storage or to your Ubuntu partition. To get a better idea of you hard drive setup please post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

When you boot your computer, do you have a GRUB loading screen? If so, then you won't need to change anything, unless Vista is your first partition, but we will determine that from the commands above. 

I really like Virtualbox, but it depends on what you do in Windows. Generally USB devices just work now (you will need to configure them in the Virtualbox manager though but it's really easy). I am able to use my iPhone with iTunes in VB, since it's encrypted and won't work in Linux. If you do anything that requires **a lot** of processing power (i.e. video editing), then it's probably not for you if you have a multi-core system. Virtualbox can only use a single core, but for day-to-day tasks it works great. 

I've heard some good things about Windows 7, so you might as well give it a spin. However, I've heard that a lot of apps don't work yet, and there's a nasty bug in Windows Media Player that messes up MP3s, although I think it has been patched, but you will need an official version from MS to get updates. It is beta software, so you should always be careful about giving it your files, especially if you don't have backups.

---

### Post by zvacet on 2009-01-16
1. Download [Gparted live CD]("http://gparted.sourceforge.net/") an with it remove your Windows partition and unallocated space add to the Ubuntu partition.

2.In general,yes.But you will depend on your ram,because Virtualbox can use just a half of your ram.

3.No,because Windows 7 will be on virtual drive,but nothing is 100% proof.

---

### Post by earthpigg on 2009-01-16
booting from a live cd, and run 'gparted' from a terminal to wipe the partition.

VBox will not do at all if you want 3d graphics/rendering.... for office and stuff, its fine.

---

### Post by mgranet on 2009-01-16
> **earthpigg said:**
> booting from a live cd, and run 'gparted' from a terminal to wipe the partition.

VBox will not do at all if you want 3d graphics/rendering.... for office and stuff, its fine.

That's not entirely accurate. The latest version supports 3D acceleration on Windows **guests**. It's currently only OpenGL capable, but it does work.

---

### Post by jbrown96 on 2009-01-16
There may be a problem just removing the Vista partition with Gparted. Swap could get in the way. I know that I always put my swap first, and if he had the following partition layout, then it will be more complicated.


/dev/sda1    Vista
/dev/sda2    Swap
/dev/sda3    Ubuntu

---

### Post by Wylkar on 2009-01-16
here is what I get from those two commands:
fdisk1:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x232f232e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11364    91281298+   7  HPFS/NTFS
/dev/sda2           28698       30401    13687380    7  HPFS/NTFS
/dev/sda3           11365       28697   139227322+   5  Extended
/dev/sda5           11365       27988   133532248+  83  Linux
/dev/sda6           27989       28697     5695011   82  Linux swap / Solaris

Partition table entries are not in disk order

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=f5734f0d-6f1d-498c-843d-a064d7aa09eb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=dff2296e-45de-49e1-afad-0bbacbfc6826 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



I do have the GRUB menu and ubuntu is listed as the first partition. Also gparted will not let me delete the ntfs file system.

---

