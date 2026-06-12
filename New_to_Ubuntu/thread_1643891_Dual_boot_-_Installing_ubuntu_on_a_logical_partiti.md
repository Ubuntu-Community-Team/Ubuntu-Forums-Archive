---
title: "Dual boot - Installing ubuntu on a logical partition"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by kit21 on 2010-12-12
Hello all,

Just got a new laptop and want to dual boot windows 7 and Ubuntu.  I tried to partition my hard drive and create a primary partition on which to install Ubuntu (the laptop has a 500GB hard drive, I assigned 50GB to Ubuntu, just to see if that would be sufficient).  However, I cannot seem to make this partition a primary - it is a logical partition, I guess due to Windows 7 having 2 primary partitions and recovery partition....which is annoying.  Can I install and boot Ubuntu 10.10 from a logical partition?

Thanks!

Fran

---

### Post by Jetso on 2010-12-12
Yes, it is possible to boot Ubuntu from a logical partition. That is what I do now.

---

### Post by sikander3786 on 2010-12-12
Linux doesn't need a primary partition to boot from. So, yes you can install Ubuntu to a logical partition. And actually, thats what most of the people do ;-)

Before going to install Ubuntu, make sure you don't have Dynamic Disks. They should be basic partitions in order to install Ubuntu. I've mentioned that because I have seen many problems regarding Dynamic Disks recently on the forums.

You can check in your Windows Partitioner Tools if they are Dynamic or Basic.

Or boot and Ubuntu Live CD/USB, test all your hardware and post the output of this command as well.

Applications > Accessories > Terminal:

```
sudo fdisk -lu
```

I would also recommend not to use the Windows partitioning tool for creating partitions for Ubuntu. Instead use gparted from the Live CD or just use the installer's partitioner during installation.

---

### Post by Jetso on 2010-12-12
Whoops! I used the Windows tool for mine. Haha, but everything works, so I'm fine.

---

### Post by amjjawad on 2010-12-12
> **kit21 said:**
> Can I install and boot Ubuntu 10.10 from a logical partition?

Thanks!

Fran

Ubuntu is not Windows and it doesn't mind at all to be installed on a Logical Partition.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

---

### Post by amjjawad on 2010-12-12
> **sikander3786 said:**
> Linux doesn't need a primary partition to boot from. So, yes you can install Ubuntu to a logical partition. And actually, thats what most of the people do ;-)

Before going to install Ubuntu, make sure you don't have Dynamic Disks. They should be basic partitions in order to install Ubuntu. I've mentioned that because I have seen many problems regarding Dynamic Disks recently on the forums.

You can check in your Windows Partitioner Tools if they are Dynamic or Basic.

Or boot and Ubuntu Live CD/USB, test all your hardware and post the output of this command as well.

Applications > Accessories > Terminal:

```
sudo fdisk -lu
```I would also recommend not to use the Windows partitioning tool for creating partitions for Ubuntu. Instead use gparted from the Live CD or just use the installer's partitioner during installation.

+ Do NOT forget to backup your important data and do a disk defragment for Windows just in case and to be in the safe side.

---

### Post by kit21 on 2010-12-12
That's great!  Thanks for your help :)  I booted the disk and installed alongside windows 7, it created a partition for me...still.  At least i can create a logical partition in windows now.... :s

On a random side note - when I run Skype and try to preview my video, signs me out of skype and closes the application.  Any idea why this might be?

Thanks again for all your speedy help!

---

