---
title: "New Partition recognized as &quot;removable drive&quot;"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by shafin on 2009-03-12
Hi,
When I installed ubuntu on my HDD, I left some free space for installing OSx86 later. But after I downloaded and tested that in a VM, I decided against installing it and formatted the partition using NTFS. Then I edited fstab to auto mount the partition. The problem is, the partition is automounting as a removable drive. THat means it goes under the menu "removable drives" in places menu. So it needs three clicks to reach it instead of two. How can I get ubuntu to register the paririon as a normal HDD partition rathere than a removable drive?

Thanks in advance.

---

### Post by Elfy on 2009-03-12
Can you post your fstab please so we can see it

---

### Post by ewj1876 on 2009-03-12
Are you using Jaunty? I think partitions and harddrives mounted under Jaunty are being listed as removable media. I'm not using Jaunty but remember reading this on a site reviewing the 9.04 Alpha a few days ago.

The reviewer wasn't sure if this was a Gnome or Unbuntu issue.

---

### Post by Elfy on 2009-03-12
Well I haven't got any drives mounted as removable here on jaunty - but I mount my drives in /mnt not /media.

---

### Post by shafin on 2009-03-12
I'm using Intrepid.
Here is my fstab. sda3 is the partition in question
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=9ff098af-4781-4e14-ad40-586504a29561 /               ext3    defaults,relatime 0       1
# /dev/sda1
UUID=B8C08833C087F5C2 /media/sda1     ntfs    force,defaults,umask=007,gid=46 0       0
# /dev/sda10
UUID=E2DCF808DCF7D4AF /media/sda10    ntfs    force,defaults,umask=007,gid=46 0       0
# /dev/sda3 
UUID=AE446CD3446C9FB7 /media/sda3     ntfs    force,defaults,umask=007,gid=46 0       0
# /dev/sda5
UUID=1C14ABF714ABD1D6 /media/sda5     ntfs    force,defaults,umask=007,gid=46 0       0
# /dev/sda6
UUID=401808F81808EEAA /media/sda6     ntfs    force,defaults,umask=007,gid=46 0       0
# /dev/sda9
UUID=86CCE8F6CCE8E183 /media/sda9     ntfs    force,defaults,umask=007,gid=46 0       0
# /dev/sda7
UUID=ec16da3f-4fad-406f-92d7-36667c0fa413 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda11
UUID=bb056cc1-bd28-4bd2-a6f2-5754816f4dee         /home        ext3         defaults,relatime                             0     2


```

---

### Post by Elfy on 2009-03-13
Try changing it to 

```
UUID=AE446CD3446C9FB7 /media/sda3 ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

---

### Post by shafin on 2009-03-23
> **forestpixie said:**
> Try changing it to 

```
UUID=AE446CD3446C9FB7 /media/sda3 ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```
Didn't work.

Can you think of some other solution?

---

