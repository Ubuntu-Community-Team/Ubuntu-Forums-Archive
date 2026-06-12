---
title: "Problem installing"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by PodgeD on 2010-05-22
I've downloaded ubuntu and installed it within windows 7 but when i restart my laptop and try start up ubuntu it wont work. It just says,
"(initramfs)ntfs_attr_pread failed:input/output error Failed to read NTFS $Bitmap: Input/output error.

SoftRAID/FakeRAID hardware

Cannot mount /dev/sda2 on /isodevice"

I'm a complete novice to this so have no idea what it means. I hard burnt it using magicdisc but when it didn't work tried burning it onto a disc which didn't work so tried installing it directly to run with windows which didnt work at all. When i click to reboot it just reboots like normal.

---

### Post by bodhi.zazen on 2010-05-22
OK, so you installed Ubuntu within Windows , this is called "wubi"

It sounds from the error message as if you are using RAID ?

I am not sure if you can use wubi with RAID, probably can in you rebuild your initrd, but probably easier to perform a standard installation.

You may need to use the alternate CD for RAID support, I am not positive.

---

### Post by sandyd on 2010-05-22
> **bodhi.zazen said:**
> OK, so you installed Ubuntu within Windows , this is called "wubi"

It sounds from the error message as if you are using RAID ?

I am not sure if you can use wubi with RAID, probably can in you rebuild your initrd, but probably easier to perform a standard installation.

You may need to use the alternate CD for RAID support, I am not positive.

 I already tried it once, previously on another computer, and it doesnt work with RAID. however, since I bet hes using RAID 0, he can just remove one of the disks from the RAID setup, and install ubuntu on there, or he can resize the RAID disk so that the RAID uses the partition, not the disk. however, the first one is more easier, and less risks since he doesnt know about RAID.

---

### Post by PodgeD on 2010-05-22
Thanks for the replys :)
Still have no idea what to do though! I was looking through some links and there seems to be different copies for RIAD but couldn't find one for the current version of ubuntu?

---

### Post by sandyd on 2010-05-22
> **PodgeD said:**
> Thanks for the replys :)
Still have no idea what to do though! I was looking through some links and there seems to be different copies for RIAD but couldn't find one for the current version of ubuntu?
Can you boot from the Ubuntu CD, and when you get to the menu, choose "try ubuntu"

Go to System -> Admnistration -> GParted.

At the right of the window, there is a drop down box listing your hard drives.

Go to each drive, and write down the drive number (1-10, in the order of the menu) and write down the free space / total space for each partition.

---

### Post by PodgeD on 2010-05-23
When i try boot from the CD and the laptop restarts it just goes straight to windows?
The hard drives I have are,
1: 1.46GB total 1.46 free
2: 184.84GB total 104.65 free

---

