---
title: "unable to mount drives"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Kinetic1001101 on 2009-10-14
ok....   I am trying to use a flash/thumb drive and cd rom drives on my Sony vaio laptop with ubuntu only. Every time I try to I get the message   "UNABLE TO MOUNT LOCATION"

What does that mean and what do I have to do to solve this?

Thanks in advance!!

I will check back tomorrow morning cause it's getting late.... 9/13/09  23:47 cst US

:)

---

### Post by beastrace91 on 2009-10-14
Huh it should auto mount but do the following to do it manually:

```
sudo mkdir /mnt/flash
sudo mount /dev/<flashdrive> /mnt/flash
```

To find the proper thing to enter for <flashdrive> run ```
sudo fdisk -l
``` and find your proper device.

~Jeff

---

### Post by SendDerek on 2009-10-14
In order to mount your USB Flash drive manually, it should simply be a matter of finding out the device node using "fdisk -l" and then using the mount command:
```
mkdir /media/USB_Drive
mount /dev/sdb1 /media/USB_Drive
```

If that gives you fits about unrecognized super block (or something like that), try telling it what type of filesystem it is:
```
mount -t vfat /dev/sdb1 /media/USB_Drive
```

---

### Post by Mark Phelps on 2009-10-14
> **Kinetic1001101 said:**
> ok....   Every time I try to I get the message   "UNABLE TO MOUNT LOCATION" 

Are you issuing Mount commands manually to do this?

You shouldn't have to do that. When you plugin the USB device, it should popup a folder on your desktop, or if not that, you should be able to see a folder in Places.

Are you getting that error when you try to open that folder in Places?  Or are you seeing no folders for your device?

---

### Post by dunkar70 on 2009-10-14
Make sure you have a partition defined on your flash drive that is accessible to the Linux kernel you are using. The kernel with Ubuntu 8.10 will not read Ext4 partitions and it may not read the latest generation NTFS partitions. If you are using Windows software to encrypt the drive, you may not be able to access the partition at all, which means you cannot mount it.

Try using GParted to see if your system will recognise the presence of the physical drive. If so, GParted will tell you the partition type and will have a warning if you cannot mount the partition as it is currently formatted.

---

