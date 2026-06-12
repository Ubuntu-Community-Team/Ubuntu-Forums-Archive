---
title: "Install into a prior partition"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by womble3367 on 2009-01-28
Can't install to prior partation that I set up for Ubunto.

When I initially installed Win Xp I set aside 100GB for Ubuntu knowing that I was going to install it later. Ubuntu wants to partition my Games partition to install Ubuntu...I do not want that! I can't find any way to get around this. I am computer literat (have built 5 machines) but I am Linux illitirate.

If this has already been posted, please give me a link to it or where it is located.       

Thanks

---

### Post by taurus on 2009-01-28
What happens to that space?  Is there a filesystem on that space?  From the LiveCD, post the output of this command and point to which partition you want to install Ubuntu on?

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by womble3367 on 2009-01-29
The partition is has not been formatted. I am not at home right now so I cannot try the sudo fdisk -l. I will try it tonight and report back.

womble3367

---

### Post by womble3367 on 2009-01-30
Here is the output of the fdisk -l :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67286728

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       91201   681372877+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       25496   102398278+   6  FAT16
/dev/sda7           25497       38244   102398278+   7  HPFS/NTFS
/dev/sda8           38245       50992   102398278+   7  HPFS/NTFS
/dev/sda9           50993       91201   322978761    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

But I have no Idea which one of these are the is the one to put it one
It was the third partition that I made on my hard drive.

Wonder if Windows 7 beta messed something up?

Thanks for any help.

I am going to shut down the live disk down and go into Windows XP to see if my HDD is how I partitioned it originally.

---

### Post by womble3367 on 2009-01-30
I think that I have figured the output of sudo fdsik -1.

sda1 is my initial WinXP
sda2 is my extended partition
sda5 is my first partition in the extended partition with Win7
sda6 is my third partition where I want to install Ubunto

It incorrectly states that it is a fat16, but it is not...hasn't been formatted and WinXP doesn't indicate their is anything here.

So I need to install Ubuntu on sda6...but how?

---

### Post by taurus on 2009-01-30
You also have /dev/sda7, /dev/sda8, & /dev/sda9 which are all ntfs filesystem.

---

### Post by womble3367 on 2009-02-02
This is true, but sda 6 is where I want to install Ununtu! How do I accomplish this?

---

