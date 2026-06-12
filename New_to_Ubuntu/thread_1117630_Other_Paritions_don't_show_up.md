---
title: "Other Paritions don't show up"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Warpnow on 2009-04-06
I have Ubuntu and Xubuntu both installed on my machien on partitions.

On my ubuntu I can see my Xubuntu partition, but on Xubuntu I cannot see my Ubuntu partition.

Any idea why?

---

### Post by MrWES on 2009-04-06
> **Warpnow said:**
> I have Ubuntu and Xubuntu both installed on my machien on partitions.

On my ubuntu I can see my Xubuntu partition, but on Xubuntu I cannot see my Ubuntu partition.

Any idea why?

While in xbuntu post the output of 

```
sudo fdisk -l
``` (lower case L)


And the output of:

```
cat /etc/fstab
```


Bill

---

### Post by Warpnow on 2009-04-06
```
brinson@brinson-desktop:~/Desktop/merge/area$ sudo fdisk -l
[sudo] password for brinson: 

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095065

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32014   257152423+   7  HPFS/NTFS
/dev/sda2           32015       91201   475419577+   5  Extended
/dev/sda5           32015       87945   449265726   83  Linux
/dev/sda6           90452       91201     6024343+  82  Linux swap / Solaris
/dev/sda7           87946       90341    19245838+  83  Linux
/dev/sda8           90342       90451      883543+  82  Linux swap / Solaris

Partition table entries are not in disk order
brinson@brinson-desktop:~/Desktop/merge/area$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=fbbc247a-fa09-42c7-8ba5-4216311c492e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=76348954-11dd-4511-a288-911dfd493eb4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
brinson@brinson-desktop:~/Desktop/merge/area$ 

```

---

### Post by MrWES on 2009-04-06
I see two swap partitions, did you mistakeningly make two? You only need one even if you're running two different window managers. Heck, even my puppylinux will pick up my Ubuntu swap and mount for use.

I'm, assuming it's the larger partition, /dev/sda6 you want to properly mount. You need to make a mount point for it, and change the the partition type in gparted. Remember to umount /dev/sda6 first, or you might neet to do a sudo swapoff /dev/sda6 first.

IMPORTANT: Do not format that partition with gparted if you have important data on it.

Bill

---

### Post by archdlx on 2009-04-06
I was looking to add another OS (another LINUX flavor) to my Dell inspiron 9400. This was one of the threads I found in the search. I actually "killed" my vista install, and could not recover it....oh well.
Anyway I also found two swap part.'s on my disk....


Will start a new thread on my questions.
Thanks for the great info on this site!

archdlx

---

