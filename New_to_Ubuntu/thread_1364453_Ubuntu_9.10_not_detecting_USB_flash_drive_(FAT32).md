---
title: "Ubuntu 9.10 not detecting USB flash drive (FAT32)"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by hul on 2009-12-25
I've been searching the forums for this subject and haven't found a solution.

I have a four gig USB flash drive that a freshly-installed Ubuntu 9.10 won't detect.  It's FAT32 formatted.  fdisk doesn't list it.  What should I do?

EDIT: Also, it works fine on a Windows machine.

---

### Post by sandyd on 2009-12-25
have you tried it anywyere else?
other computer?

---

### Post by hul on 2009-12-25
Sorry, forgot to mention it works fine on a Windows machine.  Will edit that into the first post.

---

### Post by taurus on 2009-12-25
Make sure you safely remove it from windows before you unplug it.

---

### Post by hul on 2009-12-25
Yes, did that, it's still not being detected.

---

### Post by taurus on 2009-12-25
Plug it in and post the output of this command.

```
dmesg | tail
```

---

### Post by admiralspark on 2009-12-25
If you're comfortorable with the terminal: [Manually Mount]("http://www.linuxquestions.org/questions/ubuntu-63/manual-mount-external-usb-hard-drive-in-ubuntu-519463/")
What exactly is the brand you're using/approx. age? I've never heard of a newer USB not working just as plug-and-play.

---

### Post by meindian523 on 2009-12-25
Try formatting it in Windows. I had a Transcend drive which would be detected and mounted on Linux, but arbitrarily unmount itself, or turn read-only during file transfer. Formatting in Windows solved the problem, but don't ask me how.

---

### Post by hul on 2009-12-25
Ran "dmesg | tail":

> [ 3862.473055] scsi 2:0:0:0: Direct-Access     Ut165    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 3862.473649] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 3862.491289] sd 2:0:0:0: [sdb] 7716864 512-byte logical blocks: (3.95 GB/3.67 GiB)
[ 3862.492335] sd 2:0:0:0: [sdb] Write Protect is off
[ 3862.492340] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3862.492343] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3862.496453] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3862.496463]  sdb: sdb1
[ 3862.853023] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3862.853033] sd 2:0:0:0: [sdb] Attached SCSI removable disk

It's [this guy]("http://www3.pny.com/4GB-New-Attacheacute-USB-20-Flash-Drive-P2663C53.aspx"), just out of the box and reformatted to FAT32 in Windows.  I'll check out manually mounting it, but I really wanted to format it to ext3 or ext4 using gparted so would prefer to not have to manually mount it to get it to work (once it's mounted I can't reformat, right?).

---

### Post by taurus on 2009-12-25
If you want to format it to ext3 or ext4 filesystem, you don't want to mount it first.  Just fire up gparted and see if it detects that USB drive.

---

### Post by gunksta on 2009-12-25
When you plug the USB key into the computer - what does happen?

For example - does the light on the USB key glow? Does the computer appear to react at all?

One thing that _can_ cause problems is if you fail to unmount a disk under Linux. It's worse with older ext_2 file systems, but FAT 32 can exhibit this too. I remember I had a USB key that one computer would NOT recognize, because it was removed without unmounting it. I could use it on another computer but I couldn't use it on that computer, until I had reset the computer. I'm sure there was another solution, but I didn't figure out what it was.

I would try resetting the computer, just to make sure that that's not the problem. Annoying - but sometimes helpful with weird file-system errors (someone else may have a better solution).

If that doesn't help, stick the USB stick into the computer and type in the command dmesg and post the last 20 lines or some of the output. Let's see if the computer even sees this USB key.

---

### Post by hul on 2009-12-25
Alas, I've tried that already and it also does not detect the drive.


EDIT: Oh, I meant I tried to open the key in gparted and gparted didn't detect it, either.
\/\/\/\/\/\/\/\/\/

---

### Post by gunksta on 2009-12-25
So I noticed. I opened this thread and then I went to eat some more pie. I didn't see the continued development of this thread due to the fact that I was stuffing my face with apple pie al a mode.

Let me go look at your dmesg output.

---

### Post by gunksta on 2009-12-25
Have you ever edited your fstab or mtab files? Your computer definitely sees the USB key.

Might help to post fstab/mtab to make sure there's not a weird problem there.

---

### Post by hul on 2009-12-25
Er, what are those?  Currently reformatting it to NTFS in Windows for the hell of it.

---

### Post by gunksta on 2009-12-25
fstab -- /etc/fstab
mtab -- /etc/mtab

These files control how your computer mounts drives.

You can open them with any text editor, although you will need root privileges to edit them.

From a terminal:

less /etc/fstab
less /etc/mtab

or use Kate, Gedit, etc. to open them in read-only mode.

---

### Post by hul on 2009-12-25
fstab:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8b915693-7780-405d-af0c-f70f429c18c7 /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=3ced6af7-a3cf-4a04-91ff-58c232e9fe2c /data           ext4    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=caf24be1-4344-4506-b5ac-37d515b6b7b6 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ad6df1f0-d689-40df-a288-4247570bd977 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



mstab:
> /dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw 0 0
/dev/sda3 /home ext4 rw 0 0
/dev/sda4 /data ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/hul/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hul 0 0
/dev/sdb /media/4A601D3E601D31E5 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

---

### Post by hul on 2009-12-25
And now it has magically begun to detect the USB drive?

Christmas gnomes?

Thank you all for your help--gunksta, do those outputs above look OK?

---

### Post by gunksta on 2009-12-25
I don't see any obvious problems, no.

So you say it's working now?

---

### Post by Frédéric Maria on 2009-12-29
Hi,
the following solved my issue regarding USB not working any more with 9.10 (9.4 was OK):

[http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)

Season greetings

---

### Post by meindian523 on 2009-12-30
Well, please mark the thread as solved.

---

### Post by sergius248 on 2010-04-11
I have been having trouble with usb drives not been recognized.
Until recently they opened on insertion but suddenly, as far as I can tell, they do not show at all. Not in the Nautilus computer pane but I know (see below) that the system detects them (during some experiments I even managed to access the content as a superuser but I was unable to modify it).
The usb drives are fine in WinXP64, same rig, and on XP32, different computer.
I have done a number of cold reboots and tried to research the problem, with no avail.
The weird thing is that when I take them out (hot unplug because the eject “removable media” show nothing) a generic icon for the drive is display on the desktop that gives when selected the familiar “You are not the owner you cannot change these permissions”.

I provide som tech info below but I do not pretend do understand most of it :-(
I love Ubunto but it is driving me nut with a series of problem like this.
Please help.


System:
Ubuntu 9.10 (karmic)
GNOME: 2.28.1
Kernel: 2.6.31-21-generic

Hardware:
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
4 Gig RAM
Two hard Disks 500Gig divided in 4 partition (one
USB controller : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
Graphic ard: GeForce 7300 SE/7200 GS
Two optical drives



Device Manager gives:

3.8 GB FAT Volume
Format: Microsoft FAT (32-bit version)
Capacity: 3.8 GB (4,111,450,112 bytes)
Available: 1.4 GB (1,521,610,752 bytes)
Device File: /dev/sdd1
Mount Point: /media/sdd1
Partition Number: 1
Partition Type: -
Volume Label: UDISK 2.0
Volume UUID: BA5D-1ACB

Relevant output from dsmeg:

[   43.099415] UDF-fs: No VRS found
[   43.099418] UDF-fs: No partition found (1)
[   43.201157] ISO 9660 Extensions: Microsoft Joliet Level 3
[   43.294168] ISOFS: Interleaved files not (yet) supported.
[   43.294170] ISOFS: File unit size != 0 for ISO file (1856).
[   43.294173] ISOFS: changing to secondary root
[   45.680011] eth0: no IPv6 routers present
[  180.982512] usb 1-2: new full speed USB device using ohci_hcd and address 10
[  181.210972] usb 1-2: configuration #1 chosen from 1 choice
[  181.214149] scsi11 : SCSI emulation for USB Mass Storage devices
[  181.214406] usb-storage: device found at 10
[  181.214408] usb-storage: waiting for device to settle before scanning
[  186.214483] usb-storage: device scan complete
[  186.221458] scsi 11:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[  186.221846] sd 11:0:0:0: Attached scsi generic sg5 type 0
[  187.276927] sd 11:0:0:0: [sdd] 8030208 512-byte logical blocks: (4.11 GB/3.82 GiB)
[  187.283920] sd 11:0:0:0: [sdd] Write Protect is off
[  187.283923] sd 11:0:0:0: [sdd] Mode Sense: 23 00 00 00
[  187.283925] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[  187.316903] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[  187.316907]  sdd: sdd1
[  187.358887] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[  187.358891] sd 11:0:0:0: [sdd] Attached SCSI removable disk

Output from lsusb:

Bus 001 Device 010: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 001 Device 009: ID 03f0:4117 Hewlett-Packard Printing Support
Bus 001 Device 007: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 001 Device 008: ID 04d9:1155 Holtek Semiconductor, Inc. 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 005: ID 08ca:0020 Aiptek International, Inc. APT-6000U Tablet
Bus 001 Device 006: ID 055f:0001 Mustek Systems, Inc. ScanExpress 1200 CU
Bus 001 Device 004: ID 13fe:1c00 Kingston Technology Company Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


mtab:

/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda3 /media/sda3 fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdc1 /media/sdc1 vfat rw,noexec,nosuid,nodev,dmask=027,fmask=137 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sr0 /media/sr0 iso9660 ro,noexec,nosuid,nodev,uid=126,gid=46 0 0
gvfs-fuse-daemon /home/sergius/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=sergius 0 0
/dev/sdd1 /media/sdd1 vfat rw,noexec,nosuid,nodev,dmask=027,fmask=137 0 0

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                            0  0  
# /dev/sda6
UUID=cfcf236f-e848-4f7b-b657-b62a6f41aa8e  /               ext3         defaults,errors=remount-ro,relatime                 0  1  
# /dev/sda1
UUID=82B0FF2FB0FF2875                      /media/sda1     ntfs         defaults,nls=utf8,umask=007,gid=46                  0  0  
# /dev/sda5
UUID=AC58283F58280B22                      /media/sda5     ntfs         defaults,nls=utf8,umask=007,gid=46                  0  0  
# /dev/sda3
UUID=44F46975F46969DE                      /media/sda3     ntfs         defaults,nls=utf8,umask=007,gid=46                  0  0  
# /dev/sdb1
UUID=1EF869BFF8699635                      /media/sdb1     ntfs         defaults,nls=utf8,umask=007,gid=46                  0  0  
# /dev/sda7
UUID=1f15e2ae-750e-4818-ac9a-6c607253ecd9  none            swap         sw                                                  0  0  
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto                                         0  0  
/dev/hdb                                   /media/cdrom1   udf,iso9660  user,noauto                                         0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto                                      0  0  

/dev/sda3                                  /media/sda3     ntfs         nls=iso8859-1,users,umask=000                       0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,umask=000                             0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,umask=000,user,uid=root               0  0  
/dev/sdc1                                  /media/sdc1     auto         rw,user,noauto,dmask=027,fmask=137                  0  0  
/dev/sda5                                  /media/sda5     auto         nls=iso8859-1,umask=000                             0  0  
/dev/sda6                                  /media/sda6     ext3         errors=remount-ro,noauto,relatime                   0  0  
/dev/sda7                                  /media/sda7     swap         sw                                                  0  0  
/dev/sdc5                                  /media/sdc5     ntfs         nls=iso8859-1,umask=000,gid=users,user,uid=sergius  0  0  
/dev/sdd1                                  /media/sdd1     auto         rw,user,noauto,dmask=027,fmask=137                  0  0  
/dev/sdf1                                  /media/sdf1     auto         rw,user,noauto,dmask=027,fmask=137                  0  0  
/dev/sde1                                  /media/sde1     auto         rw,user,noauto,dmask=027,fmask=137                  0  0  

Output from Mount:

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/sda3 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/sdc1 type vfat (rw,noexec,nosuid,nodev,dmask=027,fmask=137)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/sr0 type iso9660 (ro,noexec,nosuid,nodev,uid=126,gid=46)
gvfs-fuse-daemon on /home/sergius/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sergius)
/dev/sdd1 on /media/sdd1 type vfat (rw,noexec,nosuid,nodev,dmask=027,fmask=137)


Option "Mount removable drives when hot-plugged" enabled in "Removable Drives and Media" app from System/preference menu.
Option "Browse media when inserted" enabled in "File Management Preferences" app from System/preference menu.

---

### Post by sergius248 on 2010-04-11
Sorry, add to my previous post.
I forgot to say taht the output above is obtained after inserting a 4 gig USB drive I know is working.

---

### Post by meindian523 on 2010-04-12
@sergius
Please create your own thread. Strangely enough, I have had quite a few cases of flash drives having unallocated space (fresh out of the box) of a few megs before the first partition which when included into the partition become unusable with Windows, complaining of missing drivers. Said drives work fine with all *nix tho'.

---

