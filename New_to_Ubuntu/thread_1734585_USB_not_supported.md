---
title: "USB not supported"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by adamparr1987 on 2011-04-20
Hi all,

Have just recently started to use Ubuntu and put a usb stick into my pc for the first time since install and got a message in the disk utility area saying it wasnt supported - see screenshot.

Is it possible to re-format the usb so that it can be read in both windows and Ubuntu machines?

Thank you,

Adam

---

### Post by rosencrantz on 2011-04-20
FAT32 is readable by both Linux and Windows.

---

### Post by adamparr1987 on 2011-04-20
Thank you, how would i go about formatting in the FAT 32 format using Ubuntu?

---

### Post by bob-linux-user on 2011-04-20
Use gparted to format to FAT32 or NTFS-make sure you select the right drive unless you want to format your local hard drive by mistake!

---

### Post by Fraoch on 2011-04-20
> **adamparr1987 said:**
> Hi all,

Have just recently started to use Ubuntu and put a usb stick into my pc for the first time since install and got a message in the disk utility area saying it wasnt supported - see screenshot.

Is it possible to re-format the usb so that it can be read in both windows and Ubuntu machines?

Thank you,

Adam

Where do you see it's not supported?

In that screenshot, I see that SMART is not supported - which is to be expected as it's a USB flash drive, they don't use SMART, see [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T). SMART is only used on hard drives.

I do see that the drive is not mounted, which is an issue - most USB drives should mount automatically.  However the drive is formatted ext4, a Linux file system (the latest and the default for Ubuntu), so it has been mounted and formatted on your Ubuntu system sometime in the past.

Oh and yeah, format it FAT32.  You can even format it NTFS if you install the package "ntfs-3g" and/or "ntfsprogs".

---

### Post by adamparr1987 on 2011-04-20
Yes Fraoch, I did try to re-format the usb drive earlier but to no joy.  Having reformatted the drive as a FAT and pressed mount drive I then get the attached screenshot.

---

### Post by Fraoch on 2011-04-20
> **adamparr1987 said:**
> Yes Fraoch, I did try to re-format the usb drive earlier but to no joy.  Having reformatted the drive as a FAT and pressed mount drive I then get the attached screenshot.

Could you re-post the error image with the "Details" section clicked?

---

### Post by adamparr1987 on 2011-04-20
of course, please find attached, many thanks for looking into this :)

---

### Post by Fraoch on 2011-04-20
> **adamparr1987 said:**
> of course, please find attached, many thanks for looking into this :)

Ehh - hope someone else jumps in here, to be honest USB automounting is something I struggled with for a little while, then several Ubuntu versions ago it fixed itself without any intervention on my part.

I would say look into /etc/fstab but you really shouldn't have to in Maverick (10.10).  /etc/fstab defines where your drives get mounted, but you should also be able to automount drives that are not defined in fstab.

The error message says that it's trying to mount the drive as /dev/sda1 but that /dev/sda1 is already mounted on root ("/"). On my system /dev/sda1 is the first partition of the first hard drive.  On yours this could very well be where Ubuntu is installed so there's some sort of conflict here.

Do you have any other USB drives you could try, and do they give the same error?

Hoping someone else jumps in!

To show how your drives are mounted, could you start a terminal and post the output of:

```
sudo fdisk -l
```

This will tell us how and where your drives are mounted.

---

### Post by adamparr1987 on 2011-04-20
> **Fraoch said:**
> Ehh - hope someone else jumps in here, to be honest USB automounting is something I struggled with for a little while, then several Ubuntu versions ago it fixed itself without any intervention on my part.

I would say look into /etc/fstab but you really shouldn't have to in Maverick (10.10).  /etc/fstab defines where your drives get mounted, but you should also be able to automount drives that are not defined in fstab.

The error message says that it's trying to mount the drive as /dev/sda1 but that /dev/sda1 is already mounted on root ("/"). On my system /dev/sda1 is the first partition of the first hard drive.  On yours this could very well be where Ubuntu is installed so there's some sort of conflict here.

Do you have any other USB drives you could try, and do they give the same error?

Hoping someone else jumps in!

To show how your drives are mounted, could you start a terminal and post the output of:

```
sudo fdisk -l
```

This will tell us how and where your drives are mounted.
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f214

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18708   150265856   83  Linux
/dev/sda2           18708       19458     6022145    5  Extended
/dev/sda5           18708       19458     6022144   82  Linux swap / Solaris

Disk /dev/sdb: 4070 MB, 4070572032 bytes
126 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008e71d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1017     3972371    c  W95 FAT32 (LBA)

---

### Post by Fraoch on 2011-04-20
> **adamparr1987 said:**
> Disk /dev/sdb: 4070 MB, 4070572032 bytes
126 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008e71d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1017     3972371    c  W95 FAT32 (LBA)

Y'know - this drive looks a lot like your 4.1 GB USB drive!  It's even formatted FAT32.

It looks like it's already mounted and the system is trying to mount it again.

Do you have a USB drive icon on your desktop?  By default, once it automounts a drive it will put an icon on your desktop and open a window in your file manager containing its contents.

---

