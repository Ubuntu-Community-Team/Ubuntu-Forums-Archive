---
title: "floppy drive"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by patrik k on 2010-10-21
Trying to mount floppy drive.
Came across this Ubuntu forum post from '05-

zechy--Because I don't know how where you are now with mounting the  floppy, I'll go through all the steps. First, format the floppy with the  terminal (shell) command "fdformat /dev/fd0" (without the quotes). Then  add the Linux filesystem to it with the command "mke2fs /dev/fd0"  (mke2fs is the filesystem, fd0 is the floppy file in the directory  /dev). Then you ready to mount the floppy. One mounts the floppy (which  Linux treats as a file) in a directory--any empty directory, in fact.  But it's most convenient to mount it in a directory listed in  /etc/fstab. So, I'd change to the directory /etc in your terminal and at  this directory enter the command "gedit fstab" to open the fstab file  in the editor (gedit). Then you can change (edit) the /dev/fd0 line to  "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0". The /media/floppy0 is  the directory where you will mount the floppy (this is just a  convenience). Make sure that you have the floppy0 directory in the  /media directory--it should be there by default in Ubuntu. After editing  fstab as above, you can then mount the floppy with the command (as  root--"sudo -s") "mount /media/floppy0" (again, without the quotes).  When finished storing stuff on the floppy, unmount as root with the  command "umount /media floppy0' (it is "umount", not "unmount"). Of  course, once you've edited fstab and have the floppy formatted, with the  filesystem on it, mounting is quick with "mount /media/floppy0".

After doing this, when using mount command, recieve this message-```
mount: you must specify the filesystem type
```
It did format and it did install file system in terminal.
I know I will probably feel like a 5 year old child after this.

---

### Post by patrik k on 2010-10-21
This is terminal commands used-
```
patrik@patrik-desktop:~$ cd /etc
patrik@patrik-desktop:/etc$ fdformat /dev/fd0
/dev/fd0: Permission denied
patrik@patrik-desktop:/etc$ sudo fdformat /dev/fd0
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... done
Verifying ... done
patrik@patrik-desktop:/etc$ sudo mke2fs /dev/fd0
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=1572864
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 34 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
patrik@patrik-desktop:/etc$ 

```And here is modified fstab file-

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3fd2efb0-397f-4cd6-aa90-ce4d96fa3864 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c9b0c97e-9713-4b06-b916-da293e971815 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,  0       0
```This info may help.

---

### Post by ArgusVision on 2010-10-21
I believe the immediate command is 

sudo mount -t vfat /dev/fd0 /media/floppy0

There maybe another option or two you may want.
Another tip. Any time you want to see the syntax and/or options for a command, use the 'man' command followed by the command name you want to research.

In this case it would be 'man mount'. (Try not to laugh.)
You may also want to edit the fstab to replace 'auto' with 'vfat'

Hope this helps.

---

### Post by patrik k on 2010-10-21
After trying your mods Argus, this is the output- 

```
patrik@patrik-desktop:/etc$ sudo mount -t vfat /dev/fd0/media/floppy0
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
patrik@patrik-desktop:/etc$ 

```

Looks like a man statement

---

### Post by plucky on 2010-10-22
> sudo mount -t vfat /dev/fd0/media/floppy0


You missed the space between /dev/fd0 and /media/floppy0 so it should be ```
sudo mount -t vfat /dev/fd0 /media/floppy0
```


Also you could try ```
udisks --mount /dev/fd0
```

Good Luck

---

### Post by patrik k on 2010-10-22
Outputs-
```
patrik@patrik-desktop:/etc$ sudo mount -t vfat /dev/fd0 /media/floppy0
mount: /dev/fd0 is not a valid block device
patrik@patrik-desktop:/etc$ 
```

And- 
```
patrik@patrik-desktop:/etc$ sudo udisks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: /dev/fd0 is not a valid block device

```

Fortunately, the use of a floppy drive is not that important these days but would still like to have it operational.

---

### Post by plucky on 2010-10-22
Are you sure the floppy itself is good?
Do you know it is formatted in Fat32?

Do you have fdutils installed?


If not then install it using synaptic package manager or from a terminal ```
sudo apt-get install fdutils
```

Then use these commands ```
sudo fdformat /dev/fd0
```

That should format the floppy,now you need to put a file system on it with ```
sudo mkfs.vfat /dev/fd0
``` for fat32 file system or ```
sudo mkfs.msdos /dev/fd0
``` for msdos file system.

Then to mount use without sudo ```
udisks --mount /dev/fd0
```

If that doesn't work,I am out of ideas.

Good Luck

---

### Post by patrik k on 2010-10-22
Plucky, after installing fdutils, formatting with fdformat, installing mkfs.vfat file system, 
output when mounting-
```
patrik@patrik-desktop:/etc$ sudo udisks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Is the syntax correct here for the fstab file?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3fd2efb0-397f-4cd6-aa90-ce4d96fa3864 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c9b0c97e-9713-4b06-b916-da293e971815 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,vfat,noauto,  0       0
```

In any event, thank you for all your help Plucky.

---

### Post by patrik k on 2010-10-22
And this is the output with disk out of drive-
```
patrik@patrik-desktop:/etc$ sudo udisks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: /dev/fd0 is not a valid block device

```

I'm sure it is a user error on my part.
Fortunately, I have plenty of other external media to work with.
Sun is shining and storms due in tonight so off to get in a short bike ride.

---

### Post by plucky on 2010-10-22
This is my line for the floppy in /etc/fstab ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

and I don't have to use "sudo" when I use the udisks command.


> udisks --mount /dev/fd0
Mounted /org/freedesktop/UDisks/devices/fd0 at /media/floppy0


Good Luck

---

### Post by ArgusVision on 2010-10-22
> **plucky said:**
> Are you sure the floppy itself is good?
Do you know it is formatted in Fat32?



I'm pretty sure it's actually FAT12. Not trying to split hairs, but it might make a difference.

---

