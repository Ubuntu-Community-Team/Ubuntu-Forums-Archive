---
title: "Moving photos."
date: 2008-12-13
forum: New to Ubuntu
---

### Post by wavemaker on 2008-12-13
Gooday all. I have downloaded some photos from a disk onto my computer, I would now like to put them on a 16gb usb stick. When I try to do this I am told that I don't have the necessary permissions to do this. Wth. I am the only user on the machine, so how can I not have permission. Any input gratefully received. Regards, James.

---

### Post by handydan918 on 2008-12-13
> **wavemaker said:**
> Gooday all. I have downloaded some photos from a disk onto my computer, I would now like to put them on a 16gb usb stick. When I try to do this I am told that I don't have the necessary permissions to do this. Wth. I am the only user on the machine, so how can I not have permission. Any input gratefully received. Regards, James.

What the permission error probably means is that the device you are trying to write to (the usb stick) is "owned" by root. If you can post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
``` I bet one of the geniuses here (genii?) can help figger it out.

---

### Post by wavemaker on 2008-12-14
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf074

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d7d7d7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          25      200781   83  Linux
/dev/sdb2              26        4111    32820795   8e  Linux LVM

Disk /dev/sdc: 16.7 GB, 16710107136 bytes
255 heads, 63 sectors/track, 2031 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b1f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             383        2031    13245592+  83  Linux
/dev/sdc2               1         382     3068383+  82  Linux swap / Solaris

Partition table entries are not in disk order
james@james:~$

---

### Post by wavemaker on 2008-12-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3011f52-159a-4a70-81b1-34f824c50dee /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5e511e9a-85e1-4a2f-a91e-4165356dfd7d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
james@james:~$

---

### Post by wavemaker on 2008-12-14
Hi, I was having a little trouble with that. Here are the outputs requested. Many thanks. James.

---

### Post by cariboo on 2008-12-14
I would suggest using nautilus as root. Press Alt-F2 and type:

```
gksu nautilus
```

This wil start nautilus in /root, you'll have to navigate to where your photos are, and then copy them to your usb device.

Jim

---

### Post by taurus on 2008-12-14
> 
Disk /dev/sdc: 16.7 GB, 16710107136 bytes
255 heads, 63 sectors/track, 2031 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b1f9

Device Boot Start End Blocks Id System
/dev/sdc1 383 2031 13245592+ 83 Linux
/dev/sdc2 1 382 3068383+ 82 Linux swap / Solaris

Is this the one you want to copy to?  Looks like you have a Linux distro on it.

---

### Post by wavemaker on 2008-12-14
Thanks all, I now have the photos on the stick. I am trying to delete them from the computer now. Will I have to do the same to do that? Thanks in advance.

---

### Post by egalvan on 2008-12-14
> **cariboo907 said:**
> I would suggest using nautilus as root. Press Alt-F2 and type:

```
gksu nautilus
```
This wil start nautilus in /root


Is there any difference to this code?

```
gksudo nautilus
```

are 'su' and 'sudo' equivalent?

Thanks

ErnestG

---

