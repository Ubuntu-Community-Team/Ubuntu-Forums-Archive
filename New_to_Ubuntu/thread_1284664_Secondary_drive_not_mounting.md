---
title: "Secondary drive not mounting"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by rs_man on 2009-10-06
I tried to configure a secondary drive to 'auto mount' upon login resulting in a little problem.

As a windows user I decided that the best way to configure this would be to find out if any options existed user the **properties** menu of the drive. From there I continued to modify the **mount point** which I added to that line "/myhdd". Then I saved the change and unmounted the drive (from the GUI) and now I cannot open/mount the drive anymore: receiving a message as such...

Cannot mount volume
Error.org.freedesktop.Hal.Device.UnknownError.
Details>
libhal.c 1399 : wrong reply from hald. Expecting an array.
org.freedesktop.Hal.Device.Volume.InvalidMountOption

I didn't do what "I thought" I did. :confused:

---

### Post by Cheezespread on 2009-10-06
Hi rs_man

Can you do a 
```
sudo fdisk -l
```
and give us the details of the drive you are trying to mount.

Access the terminal from **Applications > Accessories > Terminal**

You can always add an entry to fstab so as to have this automounted always
If you need to add it to your fstab please follow the steps below:
**Assuming the drive to mount is /dev/sdb1.** 

1. **Edit your fstab file**
```
sudo gedit /etc/fstab
```

2. **Add the following to your fstab **
```
/dev/sdb1 /media/myHDD ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
```

3.**Creating the mount point** 
```
sudo mkdir /media/myHDD
```

4.**Unmount the drives and mount it again**

```
sudo umount -a
sudo mount -a
```

This should suffice . You would be able to access your harddrive by this. Else give us a shout.

---

### Post by rs_man on 2009-10-06
Thank you for the quick reply Cheezespread,

The contents of the code you supplied is as follows:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95ac95ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sda2            6529       16206    77738535    f  W95 Ext'd (LBA)
/dev/sda5            6529        8487    15735636    7  HPFS/NTFS
/dev/sda6            8488       15957    60002743+  83  Linux
/dev/sda7           15958       16206     2000061   82  Linux swap / Solaris

```

After following the instructions you provided me I was able to yeild this result:
```
rschmitz@rschmitz-desktop:~$ sudo umount -a
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
rschmitz@rschmitz-desktop:~$ sudo mount -a
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
rschmitz@rschmitz-desktop:~$ 
```

---

### Post by Cheezespread on 2009-10-07
sdb1 is what I assumed your secondary HDD to be.

Have you connected your secondary drive ?. The fdisk only shows one harddrive as I understand.

Please correct me if I am wrong.

---

### Post by rs_man on 2009-10-07
Yes, Im sorry. Its a second (logical) drive.

---

### Post by Cheezespread on 2009-10-07
Is it a secondary slave drive that you are trying to access ? 

If it were , there should be an entry like this for example .

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 19079 153252036 83 Linux
/dev/hda2 19080 19457 3036285 5 Extended
/dev/hda5 19080 19457 3036253+ 82 Linux swap / Solaris

**Disk /dev/hdb**: 20.8 GB, 20847697920 bytes
64 heads, 63 sectors/track, 10098 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 2 10098 20355552 f W95 Ext'd (LBA)
**/dev/hdb5 **2 10098 20355520+ b W95 FAT32
```

I am not able to see the second drive in your "fdisk -l " output. Or may be I am not understanding it correctly.

---

### Post by rs_man on 2009-10-07
After looking at the code you supplied and the logical drive choices I had available I made a few changes.

First of which being in the /etc/fstab file, I changed the /dev/sdb1 to /dev/sda5.
```
/dev/sda5 /media/myhdd ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask137 0 0
```

From there I figured that a directory would need to be created under /mnt for the drive to mount to:
```
sudo mkdir /mnt/myhdd
```

After this I was immediately able to access the files on that drive from the /mnt/myhdd directory. However when performing the *sudo umount -a* and *sudo mount -a* the following code appears:
```
rschmitz@rschmitz-desktop:~$ sudo umount -a
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
rschmitz@rschmitz-desktop:~$ sudo mount -a
fuse: failed to access mountpoint /media/myhdd: No such file or directory
rschmitz@rschmitz-desktop:~$ 
```
- Im not sure what happened here as I created the directory myself. :confused:

Though I can access the files by locating the /mnt/myhdd dir yet that doesn't exactly provide the best of results: the drive is properly displayed under **Places** when I select the myhdd drive I receive the following message:
```
**Unable to mount myhdd**
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.
```

---

### Post by rs_man on 2009-10-07
> **Cheezespread said:**
> Is it a secondary slave drive that you are trying to access ? 


I have several partitions on one HDD (physical): one for Ubuntu, file storage, and Windows. Sorry to add to the confusion. :|

---

### Post by Cheezespread on 2009-10-07
> **rs_man said:**
> After looking at the code you supplied and the logical drive choices I had available I made a few changes.

First of which being in the /etc/fstab file, I changed the /dev/sdb1 to /dev/sda5.
```
/dev/sda5 **/media/myhdd** ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask137 0 0
```

From there I figured that a directory would need to be created under /mnt for the drive to mount to:
```
sudo mkdir **/mnt/myhdd**
```

After this I was immediately able to access the files on that drive from the /mnt/myhdd directory. However when performing the *sudo umount -a* and *sudo mount -a* the following code appears:
```
rschmitz@rschmitz-desktop:~$ sudo umount -a
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
rschmitz@rschmitz-desktop:~$ sudo mount -a
fuse: failed to access mountpoint /media/myhdd: No such file or directory
rschmitz@rschmitz-desktop:~$ 
```
- Im not sure what happened here as I created the directory myself. :confused:

Though I can access the files by locating the /mnt/myhdd dir yet that doesn't exactly provide the best of results: the drive is properly displayed under **Places** when I select the myhdd drive I receive the following message:
```
**Unable to mount myhdd**
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.
```


You have created a mountpoint at **/mnt/myhdd** and you are mounting it in **/media/myhdd**( which doesn't exist) as per fstab. Change fstab entry to /mnt/myhdd and give it a try. 

Apologies . I thought it was a second physical drive you have added recently.

---

### Post by rs_man on 2009-10-07
Thanks for pointing that out. Consistency would be key in this sort of situation(sarcasm). 

Ill give it a try.

---

### Post by rs_man on 2009-10-08
I corrected the inconsistency issue. I can now access the file and its contents but have to navigate to the /mnt/myhdd location to view the files. Is there something more that I will have to do for it to display like my other mounted drives?

---

### Post by rs_man on 2009-10-18
I have solved the issue. After connecting to the other partition again I found the changes that caused this mess and reverted them back to default. All is copacetic.

Thanks for all your help Cheeze. :)

---

### Post by Baelus on 2009-10-18
> **rs_man said:**
> I tried to configure a secondary drive to 'auto mount' upon login resulting in a little problem.

As a windows user I decided that the best way to configure this would be to find out if any options existed user the **properties** menu of the drive. From there I continued to modify the **mount point** which I added to that line "/myhdd". Then I saved the change and unmounted the drive (from the GUI) and now I cannot open/mount the drive anymore: receiving a message as such...

Cannot mount volume
Error.org.freedesktop.Hal.Device.UnknownError.
Details>
libhal.c 1399 : wrong reply from hald. Expecting an array.
org.freedesktop.Hal.Device.Volume.InvalidMountOption

I didn't do what "I thought" I did. :confused:


I think it would've worked if you had used "myhdd" instead of "/myhdd".

I believe the preceding slash makes the mount point appear to be "/media//myhdd", which ubuntu would have a problem with.

---

### Post by rs_man on 2009-10-18
Baelus,

Now that you mention, that makes perfect sense. I appreciate the input. Ill have to remember that next time I mess with anything under those settings.

Cheers,

---

