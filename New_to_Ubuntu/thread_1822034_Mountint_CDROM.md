---
title: "Mountint CDROM"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by lawman007 on 2011-08-10
Hello to all. This is really great forum. I am new user of LInux Ubuntu.I have installed Ubuntu inside Windows with wubi installer. And its work perfectly.  I have some questions about mounting.
In this moment when I insert CD in my cd-rom ,CD-ROM automatically run and mount CD.This is not problem. But problem is because my brother also use this Linux . He can also mount cd-rom automtically when inject cd in cd-rom.There is no some restriction for normal users. And i am find on google some tricks and tips. I know that I must edited /etc/fstab file.
But problem is because i dont know how edit it and what to cjamge. Also i want to switch off auto mounting.

This is output of file /etc/fstab .

>  # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro,usrquota,grpquota  0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
~                                                                                                       This is just for exam :)Thanx

---

### Post by jtarin on 2011-08-10
I would think this would come under the heading of adding or removing users from groups rather than /etc/fstab. As a rule we do not do homework....keep that in mind if you get some slightly rude remarks.

---

