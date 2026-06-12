---
title: "Expand Volumegroup"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by TTown on 2008-12-03
This may be easy to 'The Real Server Admin' (and doing it with XP64 took me only about an hour including research), but linux forums leave me stranded with (not step-by-step) guides how to manually (aka byte-wise) manipulate your FAT.

Starting Point:
/boot (/dev/sdb1 - ext3) on a dedicated hdd
/tmp  (/dev/sdb1 -ext3) same hdd as /boot
/ (XFS) on a RAID6 based on 6 750GB HDDs on an ARECA3112ml host controller.

Now I added an hdd to the array, initialized it and grew the volume (raid-wise - not lvm-wise).
But I cant find out how to make the additional space available tio the volume group.
To put it in other words: I did not add another drive to the volume group (I found tutorials about that). The 'one' hdd the volume group lives in just grew some extra bytes.


sudo vgdisplay                                             --- Volume group ---
  VG Name               VolGroup00
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               2.73 TB
  PE Size               64.00 MB
  Total PE              44712
  Alloc PE / Size       44712 / 2.73 TB
  Free  PE / Size       0 / 0
  VG UUID               Jqfec5-tep4-vnLJ-1v5O-uk4O-iRdv-Nx4EE8

stefan@unterhaltung:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                     2925985792 2468813344 457172448  85% /
varrun                 1031536       996   1030540   1% /var/run
varlock                1031536         0   1031536   0% /var/lock
udev                   1031536        44   1031492   1% /dev
devshm                 1031536        12   1031524   1% /dev/shm
lrm                    1031536     44968    986568   5% /lib/modules/2.6.24-21-g  eneric/volatile
/dev/sdb1                93504     64032     29472  69% /boot
/dev/sdb2            102348276      5128 102343148   1% /tmp
gvfs-fuse-daemon     2925985792 2468813344 457172448  85% /home/stefan/.gvfs

How do I go about including the extra 750GB into VolGroup00-LogVol00 and make them available to the / partition?

---

### Post by overdrank on 2008-12-03
Moved to Absolute Beginner Talk and bumped to the top. :)

---

### Post by hyper_ch on 2008-12-03
this is from a not-yet-published howto of mine (not published here as I used Debian Lenny):

* I just copied and pasted it with only a few things to alter...

**Expanding the LVM**

In case your smaller harddisk (in a RAID1) fails and you add a bigger new one, then you want to expand the size to its maximum. I'll tell you very shortly how this can be done with XFS. First, you run:

```
mdadm --grow /dev/md3 --size=max
```
--> change /dev/mdX accordingly

Remember: /dev/md3 is our /data partition. With this command, the raid array will expand to it's maximum. Before the smaller harddrive failed, it was not set to its maximum on the bigger one. After that reboot the system (I know, there are ways without rebooting, but this just makes it a lot simpler).

Once you have rebooted, run this command:

```

pvresize /dev/mapper/md3_crypt

```
--> it's all fully encrypted in my howto, hence that device name

After that you have to find out by how much you can expand the size. Run this command:

```

vgdisplay -A

```

This will output a few things on the LVM. You need to look for this line here:

```

Free PE / Size  xxxxxxx / yyyy GB

```

The value of "xxxxxxx" is important. Run the following command and replace "xxxxxxx" with the actual value. Also be sure to use to correct logical volume name. The one I created is "DATA-DATA_MD3.

```

lvextend -l +xxxxxxx /dev/mapper/DATA-DATA_MD3

```

If you're unsure about your logical volume name, run this command to list all the mapper:

```

ls /dev/mapper

```

Once you run that, the final step is to enlarge the actual filesystem. XFS makes this very easy:

```

xfs_growfs /data

```
--> where /data is the name of the mounted logical device

---

### Post by TTown on 2008-12-03
[INDENT]```
mdadm --grow /dev/md3 --size=max
```
--> change /dev/mdX accordingly[/INDENT]

mdadm is currently not installed -- would I need it? It is a true hardware raid. There is only one disk visible to the OS.

[INDENT]Once you have rebooted, run this command:

```

pvresize /dev/mapper/md3_crypt

```
--> it's all fully encrypted in my howto, hence that device name
[/INDENT]

stefan@unterhaltung:/dev/mapper$ sudo pvresize /dev/mapper/VolGroup00-LogVol00
  No physical volume label read from /dev/mapper/VolGroup00-LogVol00
  Failed to read physical volume "/dev/mapper/VolGroup00-LogVol00"
  0 physical volume(s) resized / 0 physical volume(s) not resized


[INDENT]After that you have to find out by how much you can expand the size. Run this command:

```

vgdisplay -A

```[/INDENT]


stefan@unterhaltung:/dev/mapper$ vgdisplay -A
  No volume groups found


What am I missing?

---

### Post by hyper_ch on 2008-12-03
oh.... all this above is for a software raid... no clue about hardware raid... can't help you there.

---

### Post by hyper_ch on 2008-12-03
actually.... starting from the pvresze it should work... but as this is Ubuntu you will probably need to prepend each command with sudo. Not sure if pvresize just works like that.

---

### Post by TTown on 2008-12-03
Trying to find out things about the 'disk' I asked sfdisk -s /dev/sdb
result: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk does not support GPT. Use GNU Parted.

This I did. It shows me 698GB unpartitioned space at the end of /dev/sda. This is good.
It also shows me 2.73TB as /dev/sda with an unknown file system and the LVM-Flag set. Well, it is an LVM-Volume and the filesystem should be XFS. Is it normal to see 'unknown filesystem' in this situation?

Resizing the existing partition is not an option (greyed-out).
I could just create a new partition (also with XFS) in the unpartitioned space and add it to the logical volume.
Would that make sense?

---

