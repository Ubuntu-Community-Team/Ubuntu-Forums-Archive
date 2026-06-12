---
title: "How can I get a ZFS drive into ubuntu?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Dee_Ann on 2009-11-09
I installed ubuntu 64bit 9.04 the other day on my new quad core pc.  :)   It rocks!  :KS

I have one problem though, my old pc was running PC-BSD and the drive was using ZFS.

There's about 17gb of files on it I NEED to get into my new pc.

I can't do it through the lan as the lan drivers on that machine were messed up and were running like a 1984 dial up modem.  It would take months to move 17gb through the lan.  :(

The drive is a SATA drive.  It's EASY to plug it into the new pc, it has external SATA cables. :)

I was able to put an old windows drive on the cables and I can see the drive, read and write to and from it.
But how would I do it with the ZFS drive?  I've heard that ZFS doesn't work under Linux..

Thank you!  :)

---

### Post by original_jamingrit on 2009-11-09
ZFS is an awesome filesystem, but unfortunately it won't ever be shipped in a linux distro by default unless the licensing issues are resolved.  You can, however, install it yourself.

Taken from the page [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS), for Ubuntu 9.04:

> Filip Brcic is kindly providing Ubuntu packages for zfs-fuse.

To install zfs-fuse add the Filip Brcic's launchpad repo to a source list.

```
sudo nano /etc/apt/sources.list.d/zfs-fuse.list
```

Add...

```
deb http://ppa.launchpad.net/brcha/ubuntu jaunty main
deb-src http://ppa.launchpad.net/brcha/ubuntu jaunty main
```

Then update apt.

```
sudo apt-get update
```

Now install zfs-fuse.

```
sudo apt-get install zfs-fuse
```


So if that works out for you, that should take care of the ZFS side of the problem. Good luck!

---

### Post by Dee_Ann on 2009-11-09
> **original_jamingrit said:**
> ZFS is an awesome filesystem, but unfortunately it won't ever be shipped in a linux distro by default unless the licensing issues are resolved.  You can, however, install it yourself.

Taken from the page [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS), for Ubuntu 9.04:



So if that works out for you, that should take care of the ZFS side of the problem. Good luck!


OMG!!!  You are so awesome!  I could hug your neck all day!  \\:D/

Thank you a million times over!  

I just need to get my stuff off that drive (it's a 500gb), put it on my new ubuntu 1.5tb drive and reformat the 500gb drive for ext4 and "filler up!"  :KS

Thank you so much!!

):P

Will let you know how it turns out.  :)

---

### Post by Dee_Ann on 2009-11-09
oh no......  :(

I'm lost again.  I don't know how to mount the drive now.  I can see that ubuntu sees the drive and knows it's a BSD drive.  But after that, I'm lost.

```
root@Xena:/# fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bff3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648      182401  1435841505    5  Extended
/dev/sda5            3648        4863     9767488+  82  Linux swap / Solaris
/dev/sda6            4864      182401  1426073953+  83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020302

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010473

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3917    31463271   83  Linux
/dev/sdc2            3918        4962     8393962+  82  Linux swap / Solaris
/dev/sdc3            4963       60801   448526767+  83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001   a5  FreeBSD
root@Xena:/# 

```

and dmesg tells me,

```
[   24.092151] eth2: link up, 100Mbps, full-duplex
[   24.092563] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   35.005004] eth2: no IPv6 routers present
[  770.545865] ufs was compiled with read-only support, can't be mounted as read-write
[  779.823185] ufs was compiled with read-only support, can't be mounted as read-write
[  797.905632] ufs was compiled with read-only support, can't be mounted as read-write
[  862.652478] ufs was compiled with read-only support, can't be mounted as read-write
[  929.956587] ufs was compiled with read-only support, can't be mounted as read-write
[  949.997807] ufs was compiled with read-only support, can't be mounted as read-write
[ 1040.652234] ufs was compiled with read-only support, can't be mounted as read-write
root@Xena:/# fdisk -l

```


sda is my ubuntu drive.
sdb and sdc are old Suse Linux drives from long ago that are *full* of stuff.

sdd is the PC-BSD 7.01 ZFS drive that I need to copy files from.
I just want to get my data out of the home directory ( /home/Dee ) and then reformat it.
I'm done with BSD, Solaris, ZFS and all the other off the wall stuff.  Bye bye to the stone age.

So how would I get to the home dir on the ZFS drive?  I *think* it was set up as a single drive, no partitions, just one big zfs drive.  :(

Thank you!  :)

---

### Post by original_jamingrit on 2009-11-09
Looking around, it looks like using a ZFS volume will take more than a simple mount command.  I am by no means an expert on ZFS, and whatever I write here is just stuff I'm looking up, and unfortunately, the first thing to pop up in a forum search is this thread :???:

It also sounds like the zfs-fuse daemon should be running, and this article may be of some help: [http://www.linuxforu.com/how-to/tried-zfs-on-linux/2/](http://www.linuxforu.com/how-to/tried-zfs-on-linux/2/)

A couple of potentially useful commands could be ```
zpool list
``` and ```
zpool status
```

Part of the cool things about ZFS is that it does away with partitioning and replaces them with "pools", that can be resized and restricted easily.  Hopefully, if you run one of the above commands, it should give you some useful information, like the name(s) of the available pool(s), and you can set a mount point for it.

---

### Post by Dee_Ann on 2009-11-09
> **original_jamingrit said:**
> Looking around, it looks like using a ZFS volume will take more than a simple mount command.  I am by no means an expert on ZFS, and whatever I write here is just stuff I'm looking up, and unfortunately, the first thing to pop up in a forum search is this thread :???:

It also sounds like the zfs-fuse daemon should be running, and this article may be of some help: [http://www.linuxforu.com/how-to/tried-zfs-on-linux/2/](http://www.linuxforu.com/how-to/tried-zfs-on-linux/2/)

A couple of potentially useful commands could be ```
zpool list
``` and ```
zpool status
```Part of the cool things about ZFS is that it does away with partitioning and replaces them with "pools", that can be resized and restricted easily.  Hopefully, if you run one of the above commands, it should give you some useful information, like the name(s) of the available pool(s), and you can set a mount point for it.


root@Xena:/# zpool list
no pools available
root@Xena:/# zpool status
no pools available
root@Xena:/# 


more log files,

```
Nov  9 13:21:47 Xena kernel: [  770.545865] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:21:56 Xena kernel: [  779.823185] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:22:14 Xena kernel: [  797.905632] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:23:19 Xena kernel: [  862.652478] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:24:26 Xena kernel: [  929.956587] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:24:46 Xena kernel: [  949.997807] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:26:17 Xena kernel: [ 1040.652234] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 13:41:53 Xena kernel: [ 1976.388108] You didn't specify the type of your ufs filesystem
Nov  9 13:41:53 Xena kernel: [ 1976.388109] 
Nov  9 13:41:53 Xena kernel: [ 1976.388110] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Nov  9 13:41:53 Xena kernel: [ 1976.388110] 
Nov  9 13:41:53 Xena kernel: [ 1976.388111] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Nov  9 13:41:53 Xena kernel: [ 1976.399173] ufs_read_super: bad magic number
Nov  9 13:42:15 Xena kernel: [ 1998.948304] You didn't specify the type of your ufs filesystem
Nov  9 13:42:15 Xena kernel: [ 1998.948305] 
Nov  9 13:42:15 Xena kernel: [ 1998.948305] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Nov  9 13:42:15 Xena kernel: [ 1998.948306] 
Nov  9 13:42:15 Xena kernel: [ 1998.948306] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Nov  9 13:42:15 Xena kernel: [ 1998.964369] ufs_read_super: bad magic number
Nov  9 13:46:18 Xena kernel: [ 2241.183094] UDF-fs: No VRS found
Nov  9 13:49:09 Xena kernel: [ 2412.722524] UDF-fs: No VRS found
Nov  9 13:49:15 Xena kernel: [ 2418.265675] ufs was compiled with read-only support, can't be mounted as read-write
Nov  9 14:09:13 Xena -- MARK --
Nov  9 14:29:13 Xena -- MARK --
Nov  9 14:49:13 Xena -- MARK --
Nov  9 15:09:13 Xena -- MARK --

```

I don't know how to figure out if the zfs service is running..  ??

---

### Post by original_jamingrit on 2009-11-09
If it's not already running, you'll need to start the service with the ```
zfs-fuse
``` command.  I'm not sure if there's a 'proper' way of doing this under Ubuntu, but if you're intending this to be a one-time thing while you retrieve your data, just running that command as root will let you use the zpool commands (hopefully).

---

### Post by Dee_Ann on 2009-11-09
> **original_jamingrit said:**
> If it's not already running, you'll need to start the service with the ```
zfs-fuse
``` command.  I'm not sure if there's a 'proper' way of doing this under Ubuntu, but if you're intending this to be a one-time thing while you retrieve your data, just running that command as root will let you use the zpool commands (hopefully).


```
root@Xena:/# zfs -fuse
unrecognized command '-fuse'
usage: zfs command args ...
where 'command' is one of the following:

    create [-p] [-o property=value] ... <filesystem>
    create [-ps] [-b blocksize] [-o property=value] ... -V <size> <volume>
    destroy [-rRf] <filesystem|volume|snapshot>

    snapshot [-r] [-o property=value] ... <filesystem@snapname|volume@snapname>
    rollback [-rRf] <snapshot>
    clone [-p] [-o property=value] ... <snapshot> <filesystem|volume>
    promote <clone-filesystem>
    rename <filesystem|volume|snapshot> <filesystem|volume|snapshot>
    rename -p <filesystem|volume> <filesystem|volume>
    rename -r <snapshot> <snapshot>
    list [-rH] [-o property[,...]] [-t type[,...]] [-s property] ...
        [-S property] ... [filesystem|volume|snapshot] ...

    set <property=value> <filesystem|volume|snapshot> ...
    get [-rHp] [-o field[,...]] [-s source[,...]]
        <"all" | property[,...]> [filesystem|volume|snapshot] ...
    inherit [-r] <property> <filesystem|volume|snapshot> ...
    upgrade [-v]
    upgrade [-r] [-V version] <-a | filesystem ...>

    mount
    mount [-vO] [-o opts] <-a | filesystem>
    unmount [-f] <-a | filesystem|mountpoint>
    share <-a | filesystem>
    unshare [-f] <-a | filesystem|mountpoint>

    send [-R] [-[iI] snapshot] <snapshot>
    receive [-vnF] <filesystem|volume|snapshot>
    receive [-vnF] -d <filesystem>

    allow [-ldug] <"everyone"|user|group>[,...] <perm|@setname>[,...]
        <filesystem|volume>
    allow [-ld] -e <perm|@setname>[,...] <filesystem|volume>
    allow -c <perm|@setname>[,...] <filesystem|volume>
    allow -s @setname <perm|@setname>[,...] <filesystem|volume>

    unallow [-rldug] <"everyone"|user|group>[,...]
        [<perm|@setname>[,...]] <filesystem|volume>
    unallow [-rld] -e [<perm|@setname>[,...]] <filesystem|volume>
    unallow [-r] -c [<perm|@setname>[,...]] <filesystem|volume>
    unallow [-r] -s @setname [<perm|@setname>[,...]] <filesystem|volume>

Each dataset is of the form: pool/[dataset/]*dataset[@name]

For the property list, run: zfs set|get

For the delegated permission list, run: zfs allow|unallow
root@Xena:/# 


-----------------


root@Xena:/# zfs-fuse
root@Xena:/# 


```

---

### Post by jlotspeich34 on 2010-11-22
I know this thread is very old, but I just had to search everywhere to find the solution to the same problem and thought I would document it:

To figure out the name of your zfs pool (volume - not quite analogous, but sorta) type:


```
zpool import
```If your drive is detected you will see a description of the drive along with the name of the pool (Sorry, I didn't copy/paste it and now that the drive is attached, the command works differently).

From here you can type

```
zpool import $POOLNAME
```Where $POOLNAME is the name of the pool from the first call to zpool import.

That should do it.

---

### Post by GrammatonCleric on 2010-11-29
I wonder if the rumors I'm hearing coming from Debian that ZFS will be in the next release "Squeeze" will trickle down to Ubuntu.  That is since Ubuntu is a down steam distro from Debian.  The ZFS modules are already available for "Sid."

[http://packages.debian.org/sid/zfs-modules](http://packages.debian.org/sid/zfs-modules)

-GC

---

