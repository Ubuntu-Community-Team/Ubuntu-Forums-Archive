---
title: "Can't Mount External Hard Drive"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by ptklip on 2009-04-07
Hi. I'm writing because I have a Western Digital USB external drive that I can no longer mount. I am not very bright when it comes to Unix, so I apologize for my ignorance.

In Ubuntu 8.10, I formatted the drive as ext3 and put some data on it. It seemed to work fine, except that if I tried to boot with it attached I'd always get a message about a non-system disk or something so I'd unplug it, then be able to boot, then plug it in and use it.

But now, when I boot and then plug it in, and then go to Places > Removable Media > 1000.2 GB Media, I get this message

Unable to mount 1000.2 GB Media

So I started reading stuff in forums and trying various commands, but with no luck, and several of the suggested commands make the terminal hang. I'm a lost noob, unfortunately.

I ran this:

peter@maui:/media/external$ lsusb
Bus 003 Device 002: ID 04eb:e030 Northstar Systems, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 005: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk
Bus 008 Device 004: ID 05ac:1209 Apple, Inc. iPod Video
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 043d:0072 Lexmark International, Inc. X6170 Printer
Bus 005 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0bda:0152 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 041e:30d1 Creative Technology, Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And the device shows up:

Bus 008 Device 005: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk

And this:

peter@maui:/$ fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37790   303548143+  83  Linux
/dev/sda2           37791       38913     9020497+   5  Extended
/dev/sda5           37791       38913     9020466   82  Linux swap / Solaris

Disk /dev/sdf: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders
Units = cylinders of 15810 * 512 = 8094720 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1          11       80293+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdf2              11        3707    29222234+   b  W95 FAT32


And when I run that, the terminal does not return to the command prompt.

Anyway, could one of you please give me a hand? I would sure appreciate it.

Thanks,

Peter

---

### Post by joeashcraft on 2009-04-07
You can use the command  dmesg  to view info about attached drives. Once you find the right device name (such as sda) you can try to mount the drive from the command line and hopefully get more useful information than just "unable to mount".  So, run the command  dmesg  and look for something like 
```

$ dmesg | grep sdb
Mar 31 19:06:24 buntubook kernel: [182661.182392]  sdb: sdb1 sdb2 

```That lets you know it's actually finding the drive. Then you can do  ```
$ fdisk -l /dev/sdb
```  (where sdb is the external drive). Once we find the partition you want to mount  (such as /dev/sdb) you can use the mount command from a terminal like this...
```
$ mount -t ext3 /dev/sdb1 /somewhere

```You'll likely get an error, please post that here.

---

### Post by ptklip on 2009-04-07
Thank you very much for your help, joeashcraft.

Because of the number of errors resulting from the first command, I thought I'd just answer with this to begin with. Should I still run the other commands you suggested, or try something else next?:

peter@maui:~$ dmesg | grep sdb
[   22.094701] sd 11:0:0:0: [sdb] 1464091424 512-byte hardware sectors (749615 MB)
[   22.095580] sd 11:0:0:0: [sdb] Write Protect is off
[   22.095582] sd 11:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   22.095584] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[   22.096329] sd 11:0:0:0: [sdb] 1464091424 512-byte hardware sectors (749615 MB)
[   22.097189] sd 11:0:0:0: [sdb] Write Protect is off
[   22.097192] sd 11:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   22.097194] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[   22.097199]  sdb:<5>scsi 10:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   29.443480]  sdb1
[   29.443489] sdb: p1 exceeds device capacity
[   29.445064] sd 11:0:0:0: [sdb] Attached SCSI disk
[   29.516365] sdb: rw=0, want=1953519937, limit=1464091424
[   29.516368] Buffer I/O error on device sdb1, logical block 976759936
[   29.516374] sdb: rw=0, want=1953519939, limit=1464091424
[   29.516377] Buffer I/O error on device sdb1, logical block 976759937
[   29.516382] sdb: rw=0, want=1953519941, limit=1464091424
[   29.516384] Buffer I/O error on device sdb1, logical block 976759938
[   29.516389] sdb: rw=0, want=1953519943, limit=1464091424
[   29.516391] Buffer I/O error on device sdb1, logical block 976759939
[   29.516397] sdb: rw=0, want=1953519937, limit=1464091424
[   29.516400] Buffer I/O error on device sdb1, logical block 976759936
[   29.516404] sdb: rw=0, want=1953519939, limit=1464091424
[   29.516407] Buffer I/O error on device sdb1, logical block 976759937
[   29.516411] sdb: rw=0, want=1953519941, limit=1464091424
[   29.516414] Buffer I/O error on device sdb1, logical block 976759938
[   29.516419] sdb: rw=0, want=1953519943, limit=1464091424
[   29.516421] Buffer I/O error on device sdb1, logical block 976759939
[   29.516434] sdb: rw=0, want=1953520049, limit=1464091424
[   29.516436] Buffer I/O error on device sdb1, logical block 976759992
[   29.516441] sdb: rw=0, want=1953520051, limit=1464091424
[   29.516444] Buffer I/O error on device sdb1, logical block 976759993
[   29.516449] sdb: rw=0, want=1953520053, limit=1464091424
[   29.516453] sdb: rw=0, want=1953520055, limit=1464091424
[   29.516459] sdb: rw=0, want=1953520049, limit=1464091424
[   29.516463] sdb: rw=0, want=1953520051, limit=1464091424
[   29.516468] sdb: rw=0, want=1953520053, limit=1464091424
[   29.516473] sdb: rw=0, want=1953520055, limit=1464091424
[   29.516515] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516520] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516529] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516537] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516545] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516553] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516561] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516572] sdb: rw=0, want=1953520001, limit=1464091424
[   29.516577] sdb: rw=0, want=1953520003, limit=1464091424
[   29.516581] sdb: rw=0, want=1953520005, limit=1464091424
[   29.516586] sdb: rw=0, want=1953520007, limit=1464091424
[   29.516594] sdb: rw=0, want=1953520049, limit=1464091424
[   29.516599] sdb: rw=0, want=1953520051, limit=1464091424
[   29.516603] sdb: rw=0, want=1953520053, limit=1464091424
[   29.516608] sdb: rw=0, want=1953520055, limit=1464091424
[   29.516616] sdb: rw=0, want=1953520065, limit=1464091424
[   29.516624] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884652] sdb: rw=0, want=1953519937, limit=1464091424
[   32.884658] sdb: rw=0, want=1953519939, limit=1464091424
[   32.884663] sdb: rw=0, want=1953519941, limit=1464091424
[   32.884667] sdb: rw=0, want=1953519943, limit=1464091424
[   32.884673] sdb: rw=0, want=1953519937, limit=1464091424
[   32.884677] sdb: rw=0, want=1953519939, limit=1464091424
[   32.884681] sdb: rw=0, want=1953519941, limit=1464091424
[   32.884686] sdb: rw=0, want=1953519943, limit=1464091424
[   32.884702] sdb: rw=0, want=1953520049, limit=1464091424
[   32.884707] sdb: rw=0, want=1953520051, limit=1464091424
[   32.884711] sdb: rw=0, want=1953520053, limit=1464091424
[   32.884716] sdb: rw=0, want=1953520055, limit=1464091424
[   32.884721] sdb: rw=0, want=1953520049, limit=1464091424
[   32.884725] sdb: rw=0, want=1953520051, limit=1464091424
[   32.884730] sdb: rw=0, want=1953520053, limit=1464091424
[   32.884734] sdb: rw=0, want=1953520055, limit=1464091424
[   32.884791] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884797] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884808] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884816] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884823] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884831] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884839] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884851] sdb: rw=0, want=1953520001, limit=1464091424
[   32.884856] sdb: rw=0, want=1953520003, limit=1464091424
[   32.884860] sdb: rw=0, want=1953520005, limit=1464091424
[   32.884865] sdb: rw=0, want=1953520007, limit=1464091424
[   32.884873] sdb: rw=0, want=1953520049, limit=1464091424
[   32.884877] sdb: rw=0, want=1953520051, limit=1464091424
[   32.884882] sdb: rw=0, want=1953520053, limit=1464091424
[   32.884886] sdb: rw=0, want=1953520055, limit=1464091424
[   32.884894] sdb: rw=0, want=1953520065, limit=1464091424
[   32.884901] sdb: rw=0, want=1953520065, limit=1464091424

---

### Post by ptklip on 2009-04-07
Ran the other commands:

peter@maui:~$ fdisk -l /dev/sdb

Disk /dev/sdb: 749.6 GB, 749614809088 bytes
255 heads, 63 sectors/track, 91135 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x469d60df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001   83  Linux



peter@maui:~$ sudo mount -t ext3 /dev/sdb1 /external
[sudo] password for peter: 
mount: mount point /external does not exist
peter@maui:~$ sudo mount -t ext3 /dev/sdb1 /disk
mount: mount point /disk does not exist
peter@maui:~$ sudo mount -t ext3 /dev/sdb1 /home/peter/Desktop
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by joeashcraft on 2009-04-08
I guess the external drive in question is ~750GB? Just want to be sure we're dealing with the correct device.

When you use the mount command, you need to know the filesystem type (in this case, ext3), the device name (/dev/sd* where * is a letter), and the mount point (could be any directory on your system, and it should be empty. often /media/disk or /mnt/disk .  I like /home/joe/usb).

Try the mount command again and use a newly created empty directory like /media/WD750 .  If you get the same errors, post them. And if it tells you to try dmesg | tail you can post that, too.

ADDED:
the errors you got "mount point does not exist" were because the mount point you were trying to use (/external and /disk) don't exist. If you want to use /external just create it first ```
$ mkdir /external
```

---

### Post by halitech on 2009-04-08
[color="red"]Device Boot Start End Blocks Id System
/dev/sdb1 * 1 121601 976760001 83 Linux[/color]

this to me looks like the drive that is set as bootable and is a linux formated drive

---

### Post by cmcanulty on 2009-09-30
I am having same problem have downloaded ntfs config tool, storage device manager,set permissions in authorizations and no luck at all. Using above directions I got this from the terminal. Please help I have no backup as I lost all trying to make Ubuntu recognize this drive. I have tried ext3, ntfs(current), and fat32. I have 81 GB I can't lose. Have also tried 2 ext HDs and both work fine in windows.

mcanulty@Gateway:~$ sudo mount -t ntfs /dev/sdb1/WD120
[sudo] password for cmcanulty: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
cmcanulty@Gateway:~$

---

### Post by cmcanulty on 2009-09-30
Maybe this will clarify, it is the details tab of the can't mount error and I have not a clue as to how to do what they ask.I am using a 120GB NTFS ext HD trying to backup.Thank you!I am afraid I have tried so many tweaks to get this going that I have thoroughly messed up my system.

---

### Post by cmcanulty on 2009-09-30
I think I found something but the fix is beyond me.
[http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged](http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged)
if anyone can help on this please respond.
Here is another reference
[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52993.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52993.html)

---

### Post by Mark Phelps on 2009-10-01
> **cmcanulty said:**
>  ... sudo mount -t ntfs /dev/sdb1/WD120


Your mount command is invalid.  You need both a device and a mount point.  You have specified only a device.

So, do the following:
sudo mkdir /media/WD120

sudo mount -t ntfs-3g /dev/sdb1 /media/WD120

Notice I specified "ntfs-3g". This is a package that provides excellent NTFS filesystem support. It should be installed automatically if you're running 9.04.  If it's not installed, get it through Synpatic.

---

### Post by cmcanulty on 2009-10-01
I do have ntfs-3g installed.One detil do I plug in the device before or after I type the make dir? Thanks.

---

### Post by LewRockwell on 2009-10-01
> **cmcanulty said:**
> I am having same problem have downloaded ntfs config tool, storage device manager,set permissions in authorizations and no luck at all. Using above directions I got this from the terminal. Please help I have no backup as I lost all trying to make Ubuntu recognize this drive. I have tried ext3, ntfs(current), and fat32. I have 81 GB I can't lose. Have also tried 2 ext HDs and both work fine in windows.

mcanulty@Gateway:~$ sudo mount -t ntfs /dev/sdb1/WD120
[sudo] password for cmcanulty: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
cmcanulty@Gateway:~$

One trouble-call per thread please

perhaps one of the moderators can move these to one of your multiple previous threads concerning your trouble-call

.

---

