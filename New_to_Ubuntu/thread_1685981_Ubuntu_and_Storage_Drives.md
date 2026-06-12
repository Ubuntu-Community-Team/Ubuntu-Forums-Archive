---
title: "Ubuntu and Storage Drives"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by Futumpsh on 2011-02-11
I am brand new to Ubuntu and I set up my PC for dual boot with Windows7.  I run both OS's off of an SSD and I use a mechanical drive for storage.  The storage drive shows up in Windows but I can't locate it in Ubuntu.  I'm probably not looking in the right place.  How do I track it down so I can access my music and documents?

Thanks in advance for any tips!

---

### Post by The Cog on 2011-02-11
I would normally expect the drive to show up in the Places menu, probably named as something like "500 GB Drive".

Orgo.

---

### Post by lukeiamyourfather on 2011-02-11
It might show up in the places menu, but if it doesn't you'll have to manually mount it. Can you post the output of "fdisk -l"? You'll have to run that as root (with sudo), it'll list all the disks and partitions in your system. So the whole command looks like this.

```
sudo fdisk -l
```

---

### Post by quadproc on 2011-02-11
> **Futumpsh said:**
> I am brand new to Ubuntu and I set up my PC for dual boot with Windows7.  I run both OS's off of an SSD and I use a mechanical drive for storage.  The storage drive shows up in Windows but I can't locate it in Ubuntu.  I'm probably not looking in the right place.  How do I track it down so I can access my music and documents?

Here are a few things to check:

1. Do a sudo blkid and look in the list for your desired partition; note its device identifier and/or UUID.  You can then use that identifier or UUID to mount it.

2. Run gparted and look in the little box in the upper right corner.  All the drives that gparted can find will appear there as you scroll up or down in the list.  Again, this will tell you the device ID (e.g., /dev/sda).

3. Display the tail of your /etc/fstab file - if you wish the relevant partition to be automatically mounted at boot time then this file will have to include that partition.  If it is not there then you can edit this file to add it.

A general note regarding partitions: it is **much** safer to specify a partition by its UUID than by its device identifier - this is because device identifiers can change!

quadproc

---

### Post by Futumpsh on 2011-02-11
I don't have the computer with me so I will check out these solutions when I get home.  I appreciate the help!

And cheers, Orgo! :D

---

### Post by bryanl on 2011-02-11
Under the system administration menu is a disk utility. It will show you the attached storage and the partitions on your drive and other information.

If the drive is not mounted, you can click on the mount volume button and use the mount point listed to know where to go find it.

---

