---
title: "Ext hard drive mount problem"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by OllieGab on 2010-04-04
Had my external hard drive disconnected from my 9.10 system for a couple of days. When I went to plug the HD in again Ubuntu won't recognise it. Or, rather, it won't mount it.
**fdisk -ls** tells me it's there but if I do **mount /dev/sdb /media/** it tells me it needs to know the file system.
I've never had that before, but if I do tell it it's a FAT32 system it still won't let me mount.
Normally I just plug the HD into the USB port and it sort itself out after just a couple of seconds....so what went wrong?

Cheers Ollie

---

### Post by Rocket2DMn on 2010-04-04
Please plug in the drive and post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
Thanks.

---

### Post by falconindy on 2010-04-04
/dev/sdb is a block device, not a partition. Try mounting /dev/sdb**1**.

---

### Post by OllieGab on 2010-04-04
**fdisk -l **gives:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c5ac

**cat: etc/fstab**: No such file or directory

**sudo blkid** gives:
/dev/sda1: UUID="40C4156BC4156506" LABEL="ACER" TYPE="ntfs" 
/dev/sda2: UUID="ac17e10b-0462-4a12-9b81-a71cd9253081" TYPE="swap" 
/dev/sda4: UUID="02c3613a-a0b1-43c0-bc1e-6bf9d4cb4fb0" TYPE="ext4" 
/dev/sda5: UUID="3560740c-6221-477c-8216-d031e6a83d1d" TYPE="ext4" 
/dev/sda6: UUID="3972ebfb-fb2b-478e-92f7-0f3f996a6850" TYPE="ext4" 

**mount:**
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda4 on /boot type ext4 (rw)
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ola/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ola)

After some additional "experimenting" I think I've come to the conlusion that the HD is corrupt. Using Windows' chkdsk says the file system is RAW - whatever that means. Any chance of recovery of data?

---

### Post by s_ø on 2010-04-04
First. You missed a '/'. Its
```
 nano /etc/fstab
```It does sound like your hd is damaged. Depending on whats wrong you can recover from practically nothing to everything.

First dont do anything more with the disk till you got a plan. Then read this [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Then ask about anything you are in doubt about.

It will possibly help if you have an idea what might have caused this. Power surge, water, accidental formatting etc etc.

If you are lucky it is only the partition table that is broken.

Edit:
What file system was/is on the disk?

---

### Post by OllieGab on 2010-04-05
I think I know what the problem might be.
As I was formatting a USB stick I just for a moment thought I'd chosen the wrong volume, ie my HD. So in a panic I pulled the USB lead out without any prior actions....which is probably not a good thing!

I think the fs was FAT32 (that's what is says if I fdisk -l).
Using GParted tells me that the volume is not formatted.

Using chkdsk in DOS (booted up in Windows obviously) says that the file system is RAW.

---

### Post by s_ø on 2010-04-05
Have you read the link about data recovery?
Im no expert on it, but would try to use parted to recreate the partition table first.
If the data is very valuable to you, you should make an image of the drive first and work on that. You will need at least the size of the hd  - 500GB according to your fdisk post- of free space to hold the image.

---

### Post by Rocket2DMn on 2010-04-05
It is not showing a partition on your sdb device, so there is nothing to mount.  If Windows says there are errors on the device, it is probably correct.  You should be able to reformat it at any time.

---

