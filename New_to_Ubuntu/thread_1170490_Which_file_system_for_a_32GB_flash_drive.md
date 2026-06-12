---
title: "Which file system for a 32GB flash drive?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-05-26
Please read a little more before you react. 

I have a 32GB flash drive which works fine with vfat format, except that I can not carry files larger than 4GB. If I format it ext3, this problem disappears, but the drive is mounted with root owner when inserted. So, every writing is to be done as root (sudo). I consider this a bad idea. 

Any suggestion will be appreciated.

---

### Post by wizard10000 on 2009-05-26
> **mmasroorali said:**
> Please read a little more before you react. 

I have a 32GB flash drive which works fine with vfat format, except that I can not carry files larger than 4GB. If I format it ext3, this problem disappears, but the drive is mounted with root owner when inserted. So, every writing is to be done as root (sudo). I consider this a bad idea. 

Any suggestion will be appreciated.

If you need Windows compatibility format it as NTFS.

If you don't, then it might be a good idea to dig a little and find out why only root can write to the drive.  I think you'll find your answer in System --> Administration --> Authorizations.  If you tweak policykit a little regular users should be able to mount, read and write to the drive just fine.

---

### Post by mmasroorali on 2009-05-26
Thanks. How do I create NTFS? mkfs does not seem to come with an ntfs extension.

---

### Post by mcduck on 2009-05-26
> **mmasroorali said:**
> If I format it ext3, this problem disappears, but the drive is mounted with root owner when inserted. So, every writing is to be done as root (sudo). I consider this a bad idea. 

Any suggestion will be appreciated.

Just create a directory on that drive and chown it to your user. Since it's a proper Linux filesystem the permissions of the directory will stay and you don't need to be root to access anything inside that directory.

So, root owns the root of the drive, but you own that directory and everything inside it.

---

### Post by wizard10000 on 2009-05-26
> **mmasroorali said:**
> Thanks. How do I create NTFS? mkfs does not seem to come with an ntfs extension.

Easiest way is with gparted.

System --> Administration --> Partition Editor

But - make sure you unmount the drive before altering the partition table.

---

### Post by Miljet on 2009-05-26
If you are only going to use the flash drive with Ubuntu (or any Linux distribution), I would keep the EXT3 format.

The easiest way to mount it is to create a directory for a mount point in your home directory. That way you will own the mount point and everything mounted there.

---

### Post by Dougie187 on 2009-05-26
Wouldn't Fat32 be better for cross platform compatibility?

---

### Post by meindian523 on 2009-05-26
> **Dougie187 said:**
> Wouldn't Fat32 be better for cross platform compatibility?
Please read before you post.OP has problems with FAT which is why he posted here in the first place.

---

### Post by NightwishFan on 2009-05-26
I believe you can tweak ext2/3 to allow any user access to a drive. I use OpenSUSE and there is an option for it in YAST partitioner.

I cannot remember the name of the software that tweaks ext, though it is installed on Ubuntu by default, and is a command line program.

---

### Post by wizard10000 on 2009-05-26
> **NightwishFan said:**
> I believe you can tweak ext2/3 to allow any user access to a drive.

chmod -R 777 *

;)

---

### Post by binbash on 2009-05-26
Why don't you format it as ntfs?You can put files which are larger than 4gb, you can use it both with ubuntu and windows.

---

### Post by NightwishFan on 2009-05-27
What I was thinking of was **tune2fs**, however I am not sure it has that functionality.

---

### Post by mmasroorali on 2009-05-27
I tried using gparted to create an NTFS partition, but why is ntfs dimmed out? 

Am I missing something here?

---

### Post by zeroseven0183 on 2009-05-27
Install **ntfsprogs** from the Terminal/Synaptics first then restart Gparted. After that, you can see it in the options.

---

### Post by niteshifter on 2009-05-28
> **mmasroorali said:**
> Please read a little more before you react. 

I have a 32GB flash drive which works fine with vfat format, except that I can not carry files larger than 4GB. If I format it ext3, this problem disappears, but the drive is mounted with root owner when inserted. So, every writing is to be done as root (sudo). I consider this a bad idea. 

Any suggestion will be appreciated.

To fix that root owner problem. Your particular system may name things differently but generally such devices will show up in /media with the name disk. So this command below will change the ownership, assuming "fred" is the user name (login name):

```
sudo chown -R  fred:fred /media/disk
```

Thing is, lots of devices will use that name "disk". Let's make that 32GB formatted as ext3 have it's own name. There's no danger in this naming - other unlabeled devices when added will be named disk1, disk2, etc - but it can be confusing: Which "disk*" is what physical device?

With the device inserted and mounted do this (still assuming the name is disk):

Use the mount command to find out the device name:
```
mount
```
Several lines will be printed. For a USB device look for a line like this:
```
/dev/sdb1 on /media/disk type ext3  
```
A memory card, if your machine has an internal reader may look like this:
```
/dev/mmcblk0p1 on /media/disk type ext3  
```

(In either case there will be more test after ext3. Ignore it.)

The first part "/dev/sdb1" (yours will most likely be different) is what you need. First unmount it (but leave it plugged in):
```
sudo umount /media/disk
```
Then label it (give that physical device a name):
```
sudo tune2fs -L 32GDisk /dev/sdb1
```
Will label (name) that unit as "32GDisk". Remove the unit from the system and insert it again, it will now mount as /media/32GDisk.

---

