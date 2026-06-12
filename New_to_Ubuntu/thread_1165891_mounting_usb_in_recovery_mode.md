---
title: "mounting usb in recovery mode"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by bountonw on 2009-05-21
Installed ubuntu on children's computer a couple of years ago and let them play with the gui.  Now there is a screen resolution issue and can't boot.  Want to reinstall but need to copy some files first.

So esc at boot and chose the first recover mode.

Now I am trying to mount a usb drive.

It is not mounting automatically.  It is a FAT32 drive.

Tried 
```
mount -t fat32 /dev/sdb /mnt/usb
```

get

```
/mnt/usb does not exist
```

If this is a recovery mode problem, how do I disable X at boot OR

how do I mount this usb drive in ubuntu

I am running
```
Ubuntu 8.04.2 \n \1
2.67.24-23-rt
```

Also network is not working so can't apt-get...  Will fix that after reinstalling from CD ubuntu 9.04

---

### Post by nandemonai on 2009-05-21
> **bountonw said:**
> Installed ubuntu on children's computer a couple of years ago and let them play with the gui.  Now there is a screen resolution issue and can't boot.  Want to reinstall but need to copy some files first.

So esc at boot and chose the first recover mode.

Now I am trying to mount a usb drive.

It is not mounting automatically.  It is a FAT32 drive.

Tried 
```
mount -t fat32 /dev/sdb /mnt/usb
```

get

```
/mnt/usb does not exist
```

If this is a recovery mode problem, how do I disable X at boot OR

how do I mount this usb drive in ubuntu

I am running
```
Ubuntu 8.04.2 \n \1
2.67.24-23-rt
```

Also network is not working so can't apt-get...  Will fix that after reinstalling from CD ubuntu 9.04

The mount point doesn't exist. Mount points in the gui are usually dynamilcally created when you insert a usb drive.

All you need to do is first create a mount point then you should be able to mount the usb drive as normal.

```
mkdir /mnt/usb
```

Then mount as normal

```
mount -t fat32 /dev/sdb /mnt/usb
```

---

### Post by bountonw on 2009-05-23
Thank you nandemonai,

I did as you suggested and got

```
unknown filesystem type 'fat32
```

Tried it with all caps and got a similar error message.

Got the gui and network working and was able to transfer files and reinstall.  So the system is working properly.  

I would like to know how to mount and unmount usb using just command line when logged into tty1.

So although my emergency is past, I want to follow through with this in the hopes of benefiting others who may find themselves in a similar jam.

---

### Post by taurus on 2009-05-23
Normally, you would mount it as /dev/sdb1, not /dev/sdb.  Also, it's **vfat** for fat32, not fat32.

What's the output of this command?

```
sudo fdisk -l
```

---

### Post by bountonw on 2009-05-23
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units - cylinders of 16065 * 512 - 8225280 bytes
Disk identifier: 0x0007cff1

Device Boot    Start    End    Blocks    Id    System 
/dev/sda1  *   1     124     995998+   83   Linux
/dev/sda2      1992    10011    64420650   5   Extended
/dev/sda3      125     1991     14996677+  83  Linux
/dev/sda5      1992    2987    8000338+   83   Linux
/dev/sda6     2988    3983    8000338+    83   Linux
/dev/sda7    3984    4605     4996183+    83   Linux
/dev/sda8    4606    6099     12000523+   83   Linux
/dev/sda9    6100    9886     30419046    83   Linux
/dev/sda10   9887   10011    1004031     82    Linux swap  / Solaris

Partition table entries are not in disk order

Disk sdb:  2032  MB, 2032140288 bytes
25 heads, 24 sectors/trak, 6615 cylinders
Units = cylinders of 600 * 512 = 307200 bytes
Disk identifier: 0x00000000

Device Boot Start End  Blocks   Id   System
/dev/sdb1  14   6616    1980416   b W95 FAT32
```

---

### Post by taurus on 2009-05-23
```
mount -t vfat /dev/sdb1 /mnt/usb
df -h
```

---

### Post by bountonw on 2009-05-23
Resolved:

```
sudo mkdir /mnt/usb
```

This makes a directory to mount the usb drive to.

```
sudo fdisk -l
```

This tells where the usb is located.

```
sudo mount -t vfat /dev/sdb1 /mnt/usb
```

This tells the computer to mount the usb (that has a fat32 file system) located at /dev/sdb1 to the /mnt/usb directory.

Hope this is helpful for someone. 

Thanks nandemonai and taurus for your help.

---

### Post by taurus on 2009-05-23
Or 

```
sudo mount -t vfat /dev/sdb1 /mnt/usb -o umask=000
```
so you can write to it as a regular user.

---

### Post by bountonw on 2009-05-28
Accidentally double posted and don't know how to delete so I edited the second post to wish everyone a pleasant day.:D

---

### Post by nandemonai on 2009-05-28
Ah yeah my bad, should be **vfat** not fat32. It's been a while since I used fat. :P

---

### Post by Chris11 on 2011-11-08
ok this thread did help me a lot ...

...but I try to mount a USB HD with a HPFS/NTFS/exFAT file system....what must I use insted of **vfat** to mount the USB drive?

---

### Post by audiomick on 2011-11-08
You can look at the man page for the mount command by doing
```
man mount
```
in a terminal, same as for any command

I think the bit you want is here, but have a look yourself.

```
  -t, --types vfstype
              The argument following the -t is used to indicate the filesystem
              type.   The  filesystem  types  which  are  currently  supported
              include: adfs,  affs,  autofs,  cifs,  coda,  coherent,  cramfs,
              debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,
              iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc,  qnx4,
              ramfs,  reiserfs,  romfs,  squashfs,  smbfs, sysv, tmpfs, ubifs,
              udf, ufs, umsdos, usbfs, vfat, xenix,  xfs,  xiafs.   Note  that
              coherent,  sysv  and  xenix  are  equivalent  and that xenix and
              coherent will be removed at some point in the future — use  sysv
              instead.  Since kernel version 2.1.21 the types ext and xiafs do
              not exist anymore. Earlier, usbfs was known as usbdevfs.   Note,
              the  real list of all supported filesystems depends on your ker&#8208;
              nel.

              For most types all the mount program has to do is issue a simple
              mount(2)  system call, and no detailed knowledge of the filesys&#8208;
              tem type is required.  For a few types however (like nfs,  nfs4,
              cifs,  smbfs,  ncpfs)  ad  hoc code is necessary. The nfs, nfs4,
              cifs, smbfs, and ncpfs filesystems have a  separate  mount  pro&#8208;
              gram.  In order to make it possible to treat all types in a uni&#8208;
              form way, mount will execute the  program  /sbin/mount.TYPE  (if
              that exists) when called with type TYPE.  Since various versions
              of the smbmount  program  have  different  calling  conventions,
              /sbin/mount.smbfs may have to be a shell script that sets up the
              desired call.

              If no -t option is given, or if  the  auto  type  is  specified,
              mount  will try to guess the desired type.  Mount uses the blkid
              or volume_id library for guessing the filesystem type;  if  that
              does not turn up anything that looks familiar, mount will try to
              read the file /etc/filesystems, or,  if  that  does  not  exist,
              /proc/filesystems.   All  of  the  filesystem types listed there
              will be tried, except for those that are labeled "nodev"  (e.g.,
              devpts,  proc and nfs).  If /etc/filesystems ends in a line with
              a single * only, mount will read /proc/filesystems afterwards.

              The auto type may be useful for user-mounted floppies.  Creating
              a  file /etc/filesystems can be useful to change the probe order
              (e.g., to try vfat before msdos or ext3 before ext2) or  if  you
              use  a  kernel  module  autoloader.  Warning: the probing uses a
              heuristic (the presence of appropriate `magic'), and could  rec&#8208;
              ognize  the  wrong  filesystem  type, possibly with catastrophic
              consequences. If your data  is  valuable,  don't  ask  mount  to
              guess.

              More  than  one type may be specified in a comma separated list.
              The list of filesystem types can be prefixed with no to  specify
              the  filesystem types on which no action should be taken.  (This
              can be meaningful with the -a option.) For example, the command:

                     mount -a -t nomsdos,ext

```

---

### Post by missiria on 2012-01-12
That's very nice toturial man ;) Thank u very much.

---

