---
title: "Need to force mount"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2010-03-08
Hi,

I have an ongoing problem with a drive not mounting.  I believe I need to force mount it.  It absolutely refueses to mount itself.

I don't know what is wrong with it becuase I can see it on my desktop from the live CD eg.  "38G Volume"  (its a 40gig drive)

I have tried the regular mount commands
> Sudo mount /dev/sda1 ~/harddrive 
but it still obstinatly refuses to mount.
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


With This command
>  sudo fdisk -l

I get this output
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


Which, I may be completely stupid, but seems to me that there's SOMETHING there and its reading SOMETHING.

I have a new hard drive on order as well as an unpartioned USB drive with old files on it.  I also have a USB to SATA case/converter on order so I can acess the bad non-mounting drive by USB.

---

### Post by myth1914 on 2010-03-08
List the partition type with: sudo fdisk -l

That should list the partition type for /dev/sda1

Then mount while specifying the partition type: sudo mount /dev/sda1 -t <type> /mount_point

---

### Post by AutumnPhoenix on 2010-03-08
sudo fdisk -1 (as in 1 like one not l as in larry)

> fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


And the second command (I may not have substituted the correct thing where I put harddrive...)

> 
ubuntu@ubuntu:~$ sudo mount dev/sda1 ~harddrive /mount_point
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


---

### Post by bcbc on 2010-03-08
try
```
$ sudo blkid
```

Then it should say */dev/sd**XY**: UUID="xxx" TYPE="**ext4**"* or something like that and then (taking the type) do:
```
$ sudo mount /dev/sdXY -t ext4 /mnt
```

(also substitute XY for the drive and partition you want to mount, e.g. /dev/sda1)

---

### Post by myth1914 on 2010-03-08
fdisk -l    as in larry, but regardless, the next post will provide the same.  You are attempting to get the partition type and then define it when mounting the drive.

---

### Post by AutumnPhoenix on 2010-03-08
thanks for your help.  My computer is rebelling, still.

same...stupid...message....


> ubuntu@ubuntu:~$ sudo mount /dev/sda1 -t ext3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


*bangs head against wall*

---

### Post by AutumnPhoenix on 2010-03-08
mind you, this is a recovery mission, not a reformat mission.

---

### Post by bcbc on 2010-03-08
Have you tried e2fsck? You also didn't mention whether dmesg |tail gave you any useful information.

I'm getting out of my depth here, but you want to be running these file system check and repair tools to see if it can fix your disk - or if it's failing - get it mountable so you can pull off your data.

I pulled this command from another thread (please check the options before running - they should be "force check, assume Yes to prompts, and verbose mode):
```
sudo e2fsck -fyv  /dev/sda1
```

Note you have to unmount /dev/sda1 before running (I know you can't mount it, but just in case someone else reads this).

---

### Post by AutumnPhoenix on 2010-03-08
sudo e2fsck -fyv /dev/sda1

> 
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Filesystem has unsupported feature(s) while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by bcbc on 2010-03-08
You can try testdisk. This link shows how to copy data off a drive using testdisk (assuming you've mounted another drive to copy it too): [How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922")

testdisk might already be on the liveCD, or you can install it: first enable the universe repository in "System->Administration->Software Source".
```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk /dev/sda
```

then follow the steps on the howto about copying data (assuming it finds it ok).

---

### Post by JerichoKru on 2010-03-08
> **AutumnPhoenix said:**
> sudo e2fsck -fyv /dev/sda1


Try just:

```
sudo fsck /dev/sd(whatever this disk is called)
```

The system will automatically choose the right fsck program to run for that filesystem...that's if you have the packages for that specific filesystem.  Ext2,3,4 should be already built in, as for others, search for them in synaptic.

---

