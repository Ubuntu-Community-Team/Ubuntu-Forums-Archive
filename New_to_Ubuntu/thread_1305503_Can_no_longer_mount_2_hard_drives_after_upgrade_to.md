---
title: "Can no longer mount 2 hard drives after upgrade to 9.10."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by osc1882 on 2009-10-29
I upgraded to 9.10 today and now it won't see my two 250 gig NTFS drives. I've played around a bunch and I still can't seem to mount it. XP and still view the drives no problem. 
I would like both of them to auto mount again. 3 other NTFS partitions still auto mount no problem. 
Oh and some times when I restart Ubuntu can't see one of the drives at all in Mount Manager and in Gparted. 

Can any one help? I need to be able to use those drives.

---

### Post by collinp on 2009-10-29
The update might have, for some reason, uninstalled ntfs-3g.

Open a terminal and enter the following:
```
sudo apt-get install ntfs-3g
```

That should install it for you, if it removed it.

---

### Post by osc1882 on 2009-10-29
No, that's still installed. ANd I still have some NTFS drives auto mounted. Just not two of them. 
Anyone else? With a pretty please and I"m Begging ya on top.

---

### Post by osc1882 on 2009-10-30
Anyone out there that knows anything about this?

---

### Post by osc1882 on 2009-10-30
Bump.

---

### Post by nothingspecial on 2009-10-30
what does ```
sudo fdisk -l
```

```
lsusb
```

and ```
dmesg | tail
```

tell you

---

### Post by bolucpap on 2009-10-30
Maybe the upgrade reverted your fstab file to its original form. If you post the output of ```
sudo cat /etc/fstab
``` maybe someone will help you along a bit more. (I'm not on expert on editing fstab files)

---

### Post by muteXe on 2009-10-30
What was wrong with your 9.04?

---

### Post by osc1882 on 2009-10-30
nothingspecial, here's the out puts you asked for. Keep in mind that the drives that are not showing up are two NTFS 250 gig drives.


grammatrain@tprb:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1eee1eee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       12870      979965   82  Linux swap / Solaris
/dev/sda3           12871       20165    58597087+  83  Linux
/dev/sda4           20166       60801   326408670    f  W95 Ext'd (LBA)
/dev/sda5           20166       60801   326408638+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019a19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x049e049e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdc5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x725e987b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdd5               2       30401   244187968+   7  HPFS/NTFS


















grammatrain@tprb:~$ lsusb
Bus 001 Device 006: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 005: ID 18e3:9101 Fitipower Integrated Technology Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 06a3:8000 Saitek PLC Gamers' Keyboard
Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 002: ID 03f0:4311 Hewlett-Packard OfficeJet 7400 series
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub









grammatrain@tprb:~$ dmesg | tail
[45208.343033] type=1503 audit(1256927616.907:50): operation="exec" pid=8518 parent=8517 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/tmp/flashgot.f6xndjq9.default/flashgot.fgt"
[45208.998237] type=1503 audit(1256927617.563:51): operation="open" pid=8510 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[45208.998432] type=1503 audit(1256927617.563:52): operation="open" pid=8510 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[45208.999645] type=1503 audit(1256927617.563:53): operation="open" pid=8510 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[45208.999678] type=1503 audit(1256927617.563:54): operation="open" pid=8510 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[46151.343210] type=1503 audit(1256928559.907:55): operation="exec" pid=8584 parent=8583 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/tmp/flashgot.f6xndjq9.default/flashgot.fgt"
[46152.026177] type=1503 audit(1256928560.592:56): operation="open" pid=8576 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[46152.026361] type=1503 audit(1256928560.592:57): operation="open" pid=8576 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[46152.027572] type=1503 audit(1256928560.592:58): operation="open" pid=8576 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
[46152.027605] type=1503 audit(1256928560.592:59): operation="open" pid=8576 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"

---

### Post by osc1882 on 2009-10-31
I be bumpping.

---

### Post by ffffuuuu on 2009-11-01
I had something similiar:
[http://ubuntuforums.org/showpost.php?p=8215587&postcount=41](http://ubuntuforums.org/showpost.php?p=8215587&postcount=41)

---

### Post by osc1882 on 2009-11-01
Ok, that post was a little bit above me. Can anyone dumb that down for me? Is there any other option? 
I really don't want to, have to reinstall everything to the older version of Ubuntu.

---

### Post by egalvan on 2009-11-01
> **osc1882 said:**
> the drives that are not showing up are two NTFS 250 gig drives.

sudo fdisk -l

Disk /dev/sda: 500.1 GB,  bytes
Disk /dev/sdb: 500.1 GB,  bytes

Disk /dev/sdc: 250.1 GB,  bytes
Disk /dev/sdd: 250.1 GB,  bytes


You show four drives currently connected and discovered.

Is this correct?
Or are there more drives physically present?

---

### Post by jefri_of_azure_sea on 2009-11-01
Install pysdm using synaptic

System-Administration-Storage Device Manager
configure your sda-ntfs drive one by one
click assistant button
uncheck the mount system in read only mode
OK

I hope that work ^^

---

### Post by osc1882 on 2009-11-01
Yes egalvan, I have 4 physical drives on this box. Two of them are 250 gig drives, so it seems odd that they are showing up as just barely above 250 gigs.

I installed and used pysdm. It doesn't show any partitions for the two 250 gig drives. 

It should be noted that in Gparted, under the partition for those drives, Gparted says it is unable to read the contents of their file system and has a big "!" in a triangle icon. So this is something that is system wide. I get the same thing if I boot into a 9.10 live cd. But these drives worked no problem in the last version of Ubuntu and still in XP.

---

### Post by osc1882 on 2009-11-02
Bump.

---

### Post by jrrader on 2009-11-02
I had the same problem.  one NTFS partition was visible and the other did not exist according 9.10.  I had a few problems with my first install of 9.10 so I reinstalled and everything was okay.  I'm not sure what went wrong the first time.  Same cd, no errors reported.  Sorry I can't help any more than that.  Reinstalling is no problem for me because of separate partitions and a good start up script.

---

### Post by kansasnoob on 2009-11-02
I'm just looking at this:

> grammatrain@tprb:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1eee1eee

Device Boot Start End Blocks Id System
/dev/sda1 * 1 12748 102398278+ 7 HPFS/NTFS
/dev/sda2 12749 12870 979965 82 Linux swap / Solaris
/dev/sda3 12871 20165 58597087+ 83 Linux
/dev/sda4 20166 60801 326408670 f W95 Ext'd (LBA)
/dev/sda5 20166 60801 326408638+ 7 HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019a19

Device Boot Start End Blocks Id System
/dev/sdb1 1 60801 488384001 7 HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x049e049e

Device Boot Start End Blocks Id System
/dev/sdc2 2 30401 244188000 f W95 Ext'd (LBA)
/dev/sdc5 2 30401 244187968+ 7 HPFS/NTFS

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x725e987b

Device Boot Start End Blocks Id System
/dev/sdd1 2 30401 244188000 f W95 Ext'd (LBA)
/dev/sdd5 2 30401 244187968+ 7 HPFS/NTFS


So fdisk is recognizing all.

Do you have any Windows operating systems that will not boot?

Regardless please install ntfsprogs:

```
sudo apt-get install ntfsprogs
```

Then reboot and report if that changed how gparted sees the drives.

**Note: ntfsprogs is harmless as a read & write "tool" but it also has the ability to edit Windows boot facilities and such**, so don't go "Willy-Nilly" wild with it:

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

### Post by nothingspecial on 2009-11-02
Can you manually mount any of the partitions?

Try this
```

sudo mkdir /media/drive/
```
```

sudo mount -t ntfs /dev/sdc5 /media/drive
```

---

### Post by osc1882 on 2009-11-03
nothingspecial when I try to mount the drive I got this message:

ntfs-3g: Failed to access volume '/dev/sdc5': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
grammatrain@tprb:~$ 









And kansasnoob, now Gparted gives me more info, but still doesn't work.

"
The device /dev/sdc5 doesn't exist

ntfsresize V2.0.0 (libntfs 10:0:0)
ERROS (2): Railed to check '/dev/sdc5' mount state: NO
such file or directory
Probably /etc/mtab is missing. It's too risky to continue.
You might try
an another Linux distro.

Unable to read the contents of this file system!
Because of this, some operations may be unavailable.

---

### Post by osc1882 on 2009-11-08
Bump.

---

### Post by osc1882 on 2009-11-11
:(

---

### Post by oldfred on 2009-11-11
Have you run chkdsk on these drives? I was looking at adding an install of Ubuntu to my portable and it saw the drives but would not ungrey them until I went back and ran chkdsk or error checking under tools.

---

### Post by osc1882 on 2009-11-13
I have. Tried that right away. Wished it did anything.
Anyone else have any ideas?

---

### Post by oldfred on 2009-11-13
Are your BIOS settings all the same and in working order. I changed some settings on my BIOS and all of sudden windows stopped working but Ubuntu was fine. Some users have reported grub not working because a drive was not configured correctly in the BIOS even though it worked in Ubuntu.

When you tried the manual mount did you add a force command - not recommended except when you do have major issues.

---

### Post by cmcanulty on 2009-11-13
This worked for me. Hook HD to a windows machine and remove safely, then try on Ubuntu again

---

### Post by tzanig on 2009-11-14
I have a similar issue with Karmic, but happened after some weeks, probably after a boot-routine disk check.

My ntfs partition is no longer visible, whilst it is perfectly working when I boot Win XP, also tried chkdsk /f without success.

Here are my outputs:

fstab: 
```
[...] 
 /dev/sda4       /media/Dati     ntfs    defaults        0       0 
 [...] 
```
sudo fdisk -l: 
```
Dispositivo Boot      Start         End      Blocks   Id  System 
 [...] 
 /dev/sda4           11097      121601   887631412+   7  HPFS/NTFS 
 [...] 
```
sudo mount -a: 
```
Failed to write lock '/dev/sda4': Risorsa temporaneamente non 
 disponibile 
 Error opening '/dev/sda4': Risorsa temporaneamente non disponibile 
 Failed to mount '/dev/sda4': Risorsa temporaneamente non disponibile 
```
sudo mount -t ntfs-3g /dev/sda4 /media/Dati -o force 
```
Failed to write lock '/dev/sda4': Risorsa temporaneamente non 
 disponibile 
 Error opening '/dev/sda4': Risorsa temporaneamente non disponibile 
 Failed to mount '/dev/sda4': Risorsa temporaneamente non disponibile 
```"Risorsa temporaneamente non disponibile" is the italian for "resource temporary unavailable".

need help as well...

---

### Post by osc1882 on 2009-11-17
Is there anyone that can help us?

---

### Post by nothingspecial on 2009-11-17
```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/sd**
```

---

### Post by osc1882 on 2009-11-17
grammatrain@tprb:~$ sudo ntfsfix /dev/sdc5
Failed to determine whether /dev/sdc5 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.
grammatrain@tprb:~$ 



:(

---

### Post by osc1882 on 2009-11-17
Just tryed chkdsk again on both drives and no luck. :(

---

### Post by oldfred on 2009-11-17
Are or were your 250GB drives in a raid configuration? There are issues with Karmic finding old raid drives and thinking they still are raid.

---

### Post by osc1882 on 2009-11-18
Yeah, I was starting to think that, that might be the case. So last night I went into my Mother board setting and disabled raid ( not that I had any drives set up as raid.). And that didn't fix things. But I know there is another setting on the Mother board where you can edit raids, I just to go find that (after I get back from work) and double check to make sure I don't have them set up as raid at all. Like I said, I haven't been useing them as raid but starting with 9.10 all of a sudden ubuntu doesn't like those drives.

---

### Post by oldfred on 2009-11-18
See comment by Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

---

### Post by VanillaMozilla on 2009-11-18
There seems to be a problem with mount, ntfs-3g, or fstab after the update.  There seem to be quite a few threads about this without a lot of progress, so I started yet another one ;) here:
[http://ubuntuforums.org/showthread.php?p=8341959#post8341959](http://ubuntuforums.org/showthread.php?p=8341959#post8341959)

---

### Post by osc1882 on 2009-11-19
Good news everyone!

The following command worked
sudo dmraid -E -r /dev/name_of_your_disk

It seems a long long time ago I tried to set these drives up as raid and some how there was still some raid info left on the drive. This command removed all raid info and left all of my data intact. Once I did that I just ran NTFS config to get the drives re-added to my auto mount. ( Although, I'm not sure I needed to do that.) 

Oh... and i don't remember if you have to install dmraid to run that command or if that command is already built into ubuntu. If you have to install it i"m sure it's just sudo apt-get install dmraid

Take care everyone and thank you, thank you, thank you for everyone that helped!

---

