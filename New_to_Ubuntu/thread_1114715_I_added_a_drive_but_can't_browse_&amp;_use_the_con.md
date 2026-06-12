---
title: "I added a drive but can't browse &amp; use the contents"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Net_Resident on 2009-04-03
This is actually on Linuxmint which is a sub variant of Ubuntu. I've been trying different distro's on different computers. When using GParted I have no problem accessing and changing the drive I added in terms of partitions. I deleted two logical FAT32 partitions actually. That operation completed (no problem) and I am able to boot the Win98 drive if I change the boot order in the CMOS.

Linuxmint is on one drive and Win98 on the other. I want to copy all the contents from the Win98 drive, then wipe it and reinstall, but in Nautilus I can't see the Win98 partitions at all. Reading a tip here I tried gksu nautilus in terminal. That brought up Nautilus in root mode but I still can't see those partitions. I know linux can see them because GParted does.

This is especially annoying because if I stick in a Knoppix 5.0 boot CD, boot to that, it sees all partitions and can read them no problem however it won't allow me to do the copy operation.

I can build computers and install OS's no problem but apparently I'm not very good with controlling Linux. I've searched for help on this and I never find the exact help I need. What do I need to do to overcome this? The drive partitions appear to be mounted, just not accessible.

---

### Post by hyper_ch on 2009-04-03
you need to mount that partition. Have a look at the "mount" command and the fstab file.

---

### Post by Net_Resident on 2009-04-03
I thought there was supposed to be a auto-mounter and why would GParted tell me it's mounted? Or does GParted mount and unmount when launched/closed? Is there a manual GUI based mount tool I can install?

---

### Post by Praxicoide on 2009-04-03
I think you want to look at what's inside the /etc/fstab file to see how your drives are being mounted.

I don't know how it work in Mint, but in Ubuntu you could write the following in a terminal:

gksudo gedit /etc/fstab

with "gedit" being the text editor to be used, you can use another one if you don't have that one.

EDIT: I remommend doing this and pasting the file so that people here in the forum get accurate information and know how to help you out.

---

### Post by tarps87 on 2009-04-03
Can you post the output of
```
sudo fdisk -l
```
This will list all your detected drives and partitions, and will show what device name to use in the with the mount command.

---

### Post by Net_Resident on 2009-04-03
OK, this is the fstab contents.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde1
UUID=72c4b337-8d1b-4342-9d21-bbf161405361 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hde5
UUID=7d56f7cc-6401-45f2-98ba-8232f7749b45 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
And this is the output of the fdisk listing.```
Disk /dev/hde: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3db012b3

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3937    31623921   83  Linux
/dev/hde2            3938        4111     1397655    5  Extended
/dev/hde5            3938        4111     1397623+  82  Linux swap / Solaris

Disk /dev/hdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afe15

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1         976     7839688+   b  W95 FAT32
/dev/hdf2             977        9729    70308472+   f  W95 Ext'd (LBA)
/dev/hdf5             977        1952     7839688+   b  W95 FAT32
/dev/hdf6            1953        2928     7839688+   b  W95 FAT32
/dev/hdf7            2929        3904     7839688+   b  W95 FAT32

```So apparently I did need to build the fstab file for the added drive and I am now assuming that when I launch GParted that it mounts and **unmounts** automatically which explains my confusion. I'm curious, is there a scripted way to add a HDD partitions? I'm not complaining at editing in the file at all, I look forward to better understanding this process but I'm curious if there is also a scripted way for doing the same thing.

What do I need to edit in please?

---

### Post by tarps87 on 2009-04-03
In most cases you shouldn't need to edit fstab to mount a new device, fstab is used for mounting devices on boot.

can you try
```

sudo mkdir /media/win95
sudo mount /dev/hdf1 /media/win95
or
sudo mount -t vfat /dev/hdf1 /media/win95

```

Here is some documentation on fstab, although it would be worth trying the commands above first
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Net_Resident on 2009-04-03
That did the trick, thank you Tarps for the additional info & link and thank you to everyone else as well for the help & pointers. :)

---

### Post by tarps87 on 2009-04-06
That's ok if you need help with editing the fstab just post back

hint:
it should look a bit like this
/dev/hdf1 /win95 vfat defaults,user,dmask=027,fmask=137 0 0

or

UUID=***output of "sudo vol_id -u"*** /dev/hdf1 /win95 vfat defaults,user,dmask=027,fmask=137 0 0

---

