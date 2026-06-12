---
title: "Need help fixing my hard drive"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by windex on 2009-10-04
I was trying to install ubuntu on a second harddrive and ended up screwing up my harddrive.  Anyway here is where I am stuck:

I tried to just reinstall and the install fails and says it is unable to unmount /cdrom

gparted says:
Partition FS   MountPT Size      Used      Unused    Flags
/dev/sdb1 ext3 /cdrom  146.18GiB 145.92Gib 272.73MiB boot

Then I tried:
ubuntu@ubuntu:~$ sudo umount -f /cdrom
umount: /cdrom: device is busy.

Then I tried:
ubuntu@ubuntu:~$ fdisk /dev/sdb

Unable to open /dev/sdb

At this point all I want to do is reformat the drive and reinstall. 
Any ideas how to fix this?

Thanks in advance!

---

### Post by falconindy on 2009-10-04
You likely cannot unmount the cd because its in use, assuming you're trying to do this from the install program with the CD still in the drive (and running your interface). The fdisk fails because you need to be root to do anything with that command.

---

### Post by LewRockwell on 2009-10-04
> **windex said:**
> I was trying to install ubuntu on a second hard-drive and ended up screwing up my hard-drive.  Anyway here is where I am stuck:

I tried to just reinstall and the install fails and says it is unable to unmount /cdrom

why are you attempting to unmount your CD drive?

isn't that where your Ubuntu LiveCD disk is?

> **windex said:**
> gparted says:
Partition FS   MountPT Size      Used      Unused    Flags
/dev/sdb1 ext3 /cdrom  146.18GiB 145.92Gib 272.73MiB boot

looks like something just isn't working properly here

your sdb1 shouldn't show a mount point of "/cdrom"

> **windex said:**
> Then I tried:
ubuntu@ubuntu:~$ sudo umount -f /cdrom
umount: /cdrom: device is busy.

Again, you're running from the Ubuntu LiveCD in your CD drive so it cannot unmount the drive Ubuntu is operating from

> **windex said:**
> Then I tried:
ubuntu@ubuntu:~$ fdisk /dev/sdb

Unable to open /dev/sdb```
sudo fdisk -l(small L)
```

> **windex said:**
> At this point all I want to do is reformat the drive and reinstall. 
Any ideas how to fix this?

let's wait until we see the results of your fdisk -l command before making any additional assumptions

also, make sure we have all your specific hardware and operating system(s) data

.

---

### Post by windex on 2009-10-04
Oh yeah, sorry about that.

I'm using a Ubuntu 9.04 on a USB drive on the computer now.  It's at /dev/sdc  I have no CD in the CD drive and have no idea why it is pointing there anyway.

---

### Post by windex on 2009-10-04
Here's more info:

/dev/sda - original harddrive with windows (SATA0 on motherboard)
/dev/sdb - harddrive I am trying to fix (SATA1 on motherboard)
/dev/sdc - usb drive I am using to try to fix this

I have never been able to get a live CD to boot in this machine.  Tried all the settings in the BIOS with no luck.  That's why I am using the USB drive.

ubuntu@ubuntu:~$ fdisk -l /dev/sdb1
Cannot open /dev/sdb1
ubuntu@ubuntu:~$ fdisk -l /dev/sdb
Cannot open /dev/sdb

---

### Post by falconindy on 2009-10-04
> **windex said:**
> ubuntu@ubuntu:~$ fdisk -l /dev/sdb1
Cannot open /dev/sdb1
ubuntu@ubuntu:~$ fdisk -l /dev/sdb
Cannot open /dev/sdb
Still doesn't matter what you boot off of. You're not going to get anywhere with fdisk if you're not running with sudo or as root.
```
[03:54 PM][user@host:~] $ fdisk -l /dev/sda
Cannot open /dev/sda
[03:54 PM][user@host:~] $ sudo fdisk -l /dev/sda
[sudo] password for user: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55f255f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux
[03:54 PM][user@host:~] $ 

```

---

### Post by windex on 2009-10-04
Thank you for catching my stupidity.  I'll try that.

---

### Post by windex on 2009-10-08
Well, fdisk sort of worked it said it couldn't write to the drive but will try on reboot.  I rebooted and now I can't use a LiveCD or the USB drive.  Tried upgrading my bios and the behavior is the same.

---

### Post by CharlesA on 2009-10-08
Are you able to boot off of a gparted live cd, or does the machine not boot off of cds period?

---

### Post by windex on 2009-10-11
Ok, I finally got it working.  Here's what I did:

1. I ran a diagnostic (F12 at power-up #6 option in menu) and found the DVD-ROM drive and DVD R/W-CD-R/RW drives were not working correctly. 

2. Went to Dell web site and installed new firmware for both devices

3. Tried again and still no boot on LiveCD

4. Found on Dell support page that some Dells have to have one of the drives disconnected to boot CDs.

5. After several tried found this to work:
   a. In BIOS setup turn off secondary master
   b. Turn on secondary slave as CD ROM device (which for some reason shows the wrong unit)
   c. OS Install mode is Off

Now I can boot the LiveCD

I have not tried the USB drive again since I got the LiveCD to work

---

