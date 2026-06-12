---
title: "How to automount a USB Hard Drive at bootup?"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by gwagchunks on 2009-07-31
Hi everyone

Sorry to post this one up, but I've have googled and still don't quite understand fstab and I really don't want to trash my system! I have an external usb hard drive I want to mount on bootup / startup. Not 100% of the best / safest way: here is some info on my drives

```

rich@htpc:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35073506

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       14207    11719417+  83  Linux
/dev/sda3           14208       60801   374266305    5  Extended
/dev/sda5           14208       14331      995998+  82  Linux swap / Solaris
/dev/sda6           14332       60801   373270243+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xddfe77c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS


rich@htpc:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             11535376   1929492   9019916  18% /
tmpfs                  1030344         0   1030344   0% /lib/init/rw
varrun                 1030344       328   1030016   1% /var/run
varlock                1030344         0   1030344   0% /var/lock
udev                   1030344       176   1030168   1% /dev
tmpfs                  1030344         0   1030344   0% /dev/shm
lrm                    1030344      2392   1027952   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6            373139168   1175216 371963952   1% /var/lib

*** ONCE MOUNTED THROUGH FILE MANAGER AND RUNNING DF AGAIN HERE IS THE DRIVE ***

/dev/sdb1            976760000  11307200 965452800   2% /media/Mybook

Here is my fstab file

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=af994ff2-a9b8-4977-b0ca-734b7ea56d93 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=01cad37d-b1d5-4ec5-b107-e5af973da68c /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=537acc4a-eaf5-4d5f-bfa7-8af67666d63f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

So the drive is a NTFS drive (I know :roll: !!!) and it's /dev/sdb1 and label is /media/Mybook

Thanks every so much.

---

### Post by afeasfaerw23231233 on 2009-07-31
Add the following line to your /etc/fstab and I think it will be auto mounted next time. 
```
/dev/sdb1 /media/Mybook ntfs-3g defaults,locale=en_US.utf8 0 0
```
You can change /media/Mybook to any path you like. For example /media/my_big_disk .
If it doesn't work just delete the line. It won't crash your drive in any sense. :KS

---

### Post by bodhi.zazen on 2009-07-31
You should mount with uuid or disk label for removable devices as the /dev/sdxy numbers may change.

Show your uuid with :

```
sudo blkid
```

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by gwagchunks on 2009-07-31
> **afeasfaerw23231233 said:**
> Add the following line to your /etc/fstab and I think it will be auto mounted next time. 
```
/dev/sdb1 /media/Mybook ntfs-3g defaults,locale=en_US.utf8 0 0
```
You can change /media/Mybook to any path you like. For example /media/my_big_disk .
If it doesn't work just delete the line. It won't crash your drive in any sense. :KS
Thank you thank you thank you afeasfaerw23231233!!!! It works! Don't understand what all the parameters are but it works! Thank you again! :D

---

### Post by gwagchunks on 2009-07-31
> **bodhi.zazen said:**
> You should mount with uuid or disk label for removable devices as the /dev/sdxy numbers may change.

Show your uuid with :

```
sudo blkid
```

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")
Ah... good point, I think I read about that somewhere but did not understand it at the time. I'll bear that in mind. Thanks! :D

---

### Post by cmcanulty on 2009-09-21
I am having trouble mounting my 500GB external drive it is USB connection and NTFS file system. Can someone please post exactly how to automount it, ie do you connect before or after entering in the command line, etc. I want it to be write and readable, thank you

---

### Post by bodhi.zazen on 2009-09-21
> **cmcanulty said:**
> I am having trouble mounting my 500GB external drive it is USB connection and NTFS file system. Can someone please post exactly how to automount it, ie do you connect before or after entering in the command line, etc. I want it to be write and readable, thank you

This is a somewhat old thread.

Your hard drive should mount automatically when you plug it into the usb port.

Opening a terminal and entering commands is not auto-mounting.

With NTFS it can be tricky, especially if the drive was not un-mounted properly.

What happens when you plug in the drive ?
Do you get any error messages when you manually mount the drive ?
In order to auto mount you need to remove any reference to the drive in fstab.
Did you try ntfs-config ?

---

