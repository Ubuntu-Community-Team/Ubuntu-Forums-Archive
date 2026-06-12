---
title: "Reducing the size of partition post install"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by oo00oo00 on 2010-05-19
Hi,

I had 30.1 GB NTFS for Windows7 and I installed Ubuntu 10.04 as per prompts made during install. I later discovered that Ubuntu installed itself on an extended partition and killed GAG in the process. I will install GAG later and restore the boot order. 

I've a 320 GB SATA HDD and post install the windows, which were 30.1 GB previously were extended to 155 GB and Ubuntu installed itself on an extended partition of 146 GB. I got confused with the new look install manager. My plan was to install Ubuntu on primary partition (20GB) and use remaining space for data partition under zfs in order to save efforts of backing up data and moving files to disks after every new release of Ubuntu. In order to correct this I used 9.10 live cd and modified the disk using GParted. My current geometry is Windows 40GB, 106 GB empty partition and 146 GB extended partition with Ubuntu. In extended partition I shrunk the Ubuntu partition to 20 GB and created free space of 116 GB followed by a swap partition. GParted or Disk Utilities in 10.04 or 9.10 live cd are not able to delete the free space in extended partition. I have tried windows disk management services but it failed with an error - Not enough disk space. 

If you can could you please let me know how do I merge the free space in extended partition with Free Primary Partition. If it is not doable then I might reinstall Ubuntu but that would be a last choice and in that case where I can find a guide for partitioning the disks in the manner mentioned above or something similar to OpenSolaris install. 

Best,

Dave

---

### Post by ubunterooster on 2010-05-19
You don't delete free space. Using Gparted in liveCD, resize the Ubuntu partition, making it as large as possible. This will take up the empty space.

---

### Post by wilee-nilee on 2010-05-19
> **oo00oo00 said:**
> Hi,

I had 30.1 GB NTFS for Windows7 and I installed Ubuntu 10.04 as per prompts made during install. I later discovered that Ubuntu installed itself on an extended partition and killed GAG in the process. I will install GAG later and restore the boot order. 

I've a 320 GB SATA HDD and post install the windows, which were 30.1 GB previously were extended to 155 GB and Ubuntu installed itself on an extended partition of 146 GB. I got confused with the new look install manager. My plan was to install Ubuntu on primary partition (20GB) and use remaining space for data partition under zfs in order to save efforts of backing up data and moving files to disks after every new release of Ubuntu. In order to correct this I used 9.10 live cd and modified the disk using GParted. My current geometry is Windows 40GB, 106 GB empty partition and 146 GB extended partition with Ubuntu. In extended partition I shrunk the Ubuntu partition to 20 GB and created free space of 116 GB followed by a swap partition. GParted or Disk Utilities in 10.04 or 9.10 live cd are not able to delete the free space in extended partition. I have tried windows disk management services but it failed with an error - Not enough disk space. 

If you can could you please let me know how do I merge the free space in extended partition with Free Primary Partition. If it is not doable then I might reinstall Ubuntu but that would be a last choice and in that case where I can find a guide for partitioning the disks in the manner mentioned above or something similar to OpenSolaris install. 

Best,

Dave

For me this description is way more complicated then it could be, maybe not for others. Maybe clean it up so it is more understandable, just get to the point. ;)

You have to remember what seems to make sense to you, may be do to your being familiar with the situation.

---

### Post by oo00oo00 on 2010-05-19
> **wilee-nilee said:**
> For me this description is way more complicated then it could be, maybe not for others. Maybe clean it up so it is more understandable, just get to the point. ;)

You have to remember what seems to make sense to you, may be do to your being familiar with the situation.

Hi,

Here is what I need to do -
1. Merge an empty partition from extended partition with empty primary partition. 
2. Make data partition with ext4 FS.

Now if it makes any sense and you know where you come from please help me with it.

Best,

David

---

### Post by oo00oo00 on 2010-05-19
> **ubunterooster said:**
> You don't delete free space. Using Gparted in liveCD, resize the Ubuntu partition, making it as large as possible. This will take up the empty space.

I do not wish to extend Ubuntu partition for various reasons. The idea is to make an independent data partition with ext4 file system and share it from 4 OS. I have dropped ZFS concept for now.

---

### Post by oo00oo00 on 2010-05-19
I've managed a work around and resized the volume turning sawpon to swapoff by left clicking the swap partition in GParted. It opened the lock and I was able to merge the unallocated 115.6GB partition with extended partition. This is just short of my expectations. I will like to keep data volume independent and looking forward for assistance from experts.  Please write on how to do that.

---

### Post by oo00oo00 on 2010-05-19
> **ubunterooster said:**
> You don't delete free space. Using Gparted in liveCD, resize the Ubuntu partition, making it as large as possible. This will take up the empty space.


Been there done that. I would like to keep data partition independent. Have lost data with Buntu 9.04 just recently and wish to avoid that in future. I will now try to shrink the extended partition with parted magic.

---

