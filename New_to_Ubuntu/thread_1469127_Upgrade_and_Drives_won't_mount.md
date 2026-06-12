---
title: "Upgrade and Drives won't mount"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by bamend on 2010-05-01
I just upgraded to 10.4 and two of my drives won't mount.  Says I have to mount as root.  How do I permanently do this?

---

### Post by Jon Monreal on 2010-05-01
Have you tried simply going to Places>Your Device? I've found that this usually works better.

If this doesn't work, we can try something else.

Also, are these NTFS drives (or partitions)?

Thanks.

---

### Post by -humanaut- on 2010-05-01
sudo fdisk -l please post

---

### Post by bamend on 2010-05-02
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc5c2f943

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sda5               2       14593   117210208+  83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09f2c1d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               2       24792   199133707+   f  W95 Ext'd (LBA)
/dev/sdb5               2       12749   102398278+   7  HPFS/NTFS
/dev/sdb6           12750       14024    10241406    7  HPFS/NTFS
/dev/sdb7           14025       19124    40965718+   7  HPFS/NTFS
/dev/sdb8           19125       23987    39062016    7  HPFS/NTFS
/dev/sdb9           23988       24792     6466131    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa49da49d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sdc2            6376       30515   193904550    f  W95 Ext'd (LBA)
/dev/sdc5            6376       17236    87240951    7  HPFS/NTFS
/dev/sdc6           17237       17873     5116671    7  HPFS/NTFS
/dev/sdc7           17874       19089     9767488+  83  Linux
/dev/sdc8           19090       30274    89843481   83  Linux
/dev/sdc9           30275       30515     1935801   82  Linux swap / Solaris
bamend@server:~$
The error I get when mounting the 120 gb drive is:
Unable to mount 120 GB (ext3) Filesystem
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda5 on /media/Bob

When I try to mount the Data drive (ntfs) I get:
Unable to mount Data
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc5 on /home/bamend/nd

Everything worked on 9.10
Any help would be appreciated

---

### Post by -humanaut- on 2010-05-03
you could try alt+f2 gksu nautilus and physically changing the permissions on the filesystem.

---

### Post by Mike.lifeguard on 2010-05-03
> **bamend said:**
> I just upgraded to 10.4 and two of my drives won't mount.  Says I have to mount as root.  How do I permanently do this?

Do you want these to be automatically mounted when you boot? Or maybe you just want to allow unprivileged users to mount/unmount them on command?

I believe both of these can be accomplished by editing the file /etc/fstab. Would you please paste the current contents of that file, and let us know which of the two options I mentioned above you are trying to achieve?

---

### Post by bamend on 2010-05-03
First, thanks for the help.  I would like these to mount automatically at boot.  

Here's my /etc/fstab contents.  I don't know why there are multiple entries for each partition.  My /home/bamend/nd partition and my Data partition won't mount.  The error messages say

Unable to mount Data
rror mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc5 on /home/bamend/nd

Unable to mount 120 GB Filesystem
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda5 on /media/Bob


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdc7 :
UUID=d5925c63-0910-443c-b554-7a4992f44df8	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc8 :
UUID=65c4a2ef-e152-4118-80ed-7923e2732c8a	/home	ext3	defaults	0	2
#Entry for /dev/sdc5 :
UUID=E8D844EED844BD16	/home/bamend/nd	ext3	defaults	0	0
/dev/sdb7	/media/Alex	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sdb7	/media/Alex_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
/dev/sdc1	/media/B234A18B34A15361	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
#Entry for /dev/sda5 :
UUID=84a290e6-91a9-4725-961b-ff7ea8761a0e	/media/Bob	ntfs	defaults,locale=en_US.UTF-8	0	0
/dev/sdb9	/media/Cathy	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sdb9	/media/Cathy_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
#Entry for /dev/sdb5 :
UUID=EE1CA7881CA74A83	/media/Data	ntfs-3g	defaults,locale=en_US.utf8	0	0
/dev/sdb8	/media/Data1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sdb8	/media/Data1_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
/dev/sdb6	/media/Mojo	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sdb6	/media/Mojo_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
#Entry for /dev/sdc6 :
UUID=247882FF7882CF4C	/media/Trey_	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
/dev/sdc1	/media/Windows	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc9 :
UUID=9f121f33-f3a2-4eef-b617-b126368bde66	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/sda4	/media/Trey	ntfs-3g	defaults,locale=en_US.UTF-8	0	0

---

### Post by Mike.lifeguard on 2010-05-03
> **bamend said:**
> First, thanks for the help.  I would like these to mount automatically at boot.  


You can use the "auto" option for that.

> **bamend said:**
> 
Here's my /etc/fstab contents.  I don't know why there are multiple entries for each partition.  My /home/bamend/nd partition and my Data partition won't mount.  The error messages say

Unable to mount Data
rror mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc5 on /home/bamend/nd

Unable to mount 120 GB Filesystem
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda5 on /media/Bob

You can mount them by adding 'sudo' to the beginning of the command. Sudo is a program that lets you run a command as the root user -- run the command 'man sudo' in a terminal. However, let's get these to mount automatically so you don't have to do that:

```

# /etc/fstab: static file system information.
#
# <file system>                             <mount point>       <type>      <options>                               <dump>  <pass>

/proc                                        /proc               proc       defaults                                0       0

### /dev/sda
/dev/sda4                                   /media/Trey         ntfs-3g     defaults                                0       0
/dev/sda5                                   /media/Bob          ntfs-3g     defaults,auto                           0       0

### /dev/sdb
/dev/sdb5                                   /media/Data         ntfs-3g     defaults                                0       0
/dev/sdb6                                   /media/Mojo         ntfs-3g     defaults                                0       0
/dev/sdb7                                   /media/Alex         ntfs-3g     defaults                                0       0
/dev/sdb8                                   /media/Data1        ntfs-3g     defaults                                0       0
/dev/sdb9                                   /media/Cathy        ntfs-3g     defaults                                0       0

### /dev/sdc
/dev/sdc1                                   /media/Windows      ntfs-3g     defaults                                0       0
/dev/sdc5                                   /home/bamend/nd     ext3        defaults,auto                           0       0
/dev/sdc6                                   /media/Trey_        ntfs-3g     defaults,nosuid,nodev,locale=en_US.utf8 0       0
/dev/sdc7                                   /                   ext4        defaults,errors=remount-ro              0       1
/dev/sdc8                                   /home               ext3        defaults                                0       2

/dev/sdc9                                   none                swap        sw                                      0       0

/dev/scd0                                   /media/cdrom0       udf,iso9660 user,noauto,exec,utf8                   0       0

```

I removed:
 * double entries
 * All references to UUID. It was too confusing for me to work with without being able to check the UUIDs. You should replace /dev/... with the UUID for hard drive partitions at some point. I left enough whitespace to fit UUIDs while keeping everything lined up nicely for easy reading.
 * Probably-unnecessary locale options
 * An entry which mounted at /media/UUID, because it is covered by the entry to /media/Windows, which is a better place to mount it.
I added:
 * 'auto' to the two partitions you wanted to have auto-mounted.

I hope this does what you want. If not, you can ask again here for help, or try looking at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) (for example) for guidance in making changes yourself.

---

### Post by widda on 2010-05-24
hello, I have same thing, Upgrade to Lucid, and now no mounting of formerly automounted 120GbExtDrive, although at least now it is 'seen'.

I read a few posts, but still can't interpret my fstab, and supply it here (clunkily, sorry) in hope that MikeLifeguard or another can give me some directions before I go messing with it

---

### Post by Mike.lifeguard on 2010-05-24
> **widda said:**
> 120GbExtDrive
Which UUID is that? You can check UUIDs with ```
sudo blkid
``` for example.

---

### Post by widda on 2010-05-24
[HTML]/dev/sda1: UUID="c5c9dc97-97f3-4060-ae30-693ef92f6686" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="185ba256-370d-40c0-9c52-1d184ed6b6d8" TYPE="swap" [/HTML]
I'm confused here because sda5,(and here that's a "swap" type) and sdc? have seemed to refer to Drive (it's also referred to as D2 sometimes, my name for it

---

### Post by Mike.lifeguard on 2010-05-24
Could you also do
```
sudo fdisk -l
```
please?

---

### Post by bth73 on 2010-05-25
I think my problem is related. My 1tb hd is nowhere in sight and I was going to copy a cd with linux on it and I get the same error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sr0 on /media/cdrom0

But only on cdrom0 drive the other dvd drive, cdrom1 mounts the ISO image

this happened after the update a few days ago, grabbed some more updates today after noticing the problem but it's still there. Nothing fixed itself.

Reversed the cd's and now the cdrom0 mounts with blank media - BUT - now I see that " burn ISO image" is not  possible with a right click.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009bc72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032617

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      120849   970719561   83  Linux
/dev/sdb2          120850      121601     6040440    5  Extended
/dev/sdb5          120850      121601     6040408+  82  Linux swap / Solaris

---

### Post by widda on 2010-05-25
Mike.lifeguard here is sudofdisk, 

d@d-laptop:~$ sudo fdisk -l
[sudo] password for d: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75d475d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19272   154802308+  83  Linux
/dev/sda2           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris

That is with extdrive not connected

---

### Post by widda on 2010-05-25
And here it is with ExtDrive connected:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75d475d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19272   154802308+  83  Linux
/dev/sda2           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde8a5fee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdc5               2       14593   117210208+   7  HPFS/NTFS

[FONT="Book Antiqua"]It is 120Gb[/FONT]

---

### Post by widda on 2010-05-25
and here is sudoblkid WITH ExtDrive connected

:~$ sudo blkid
/dev/sda1: UUID="c5c9dc97-97f3-4060-ae30-693ef92f6686" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="185ba256-370d-40c0-9c52-1d184ed6b6d8" TYPE="swap" 
/dev/sdc5: LABEL="D2" UUID="F2A00EE9A00EB45F" TYPE="ntfs"

---

### Post by bth73 on 2010-05-25
just burnt a dvd and then got the same error message about the burnt dvd and it has locked up - message won't close. auto fdisk ran last night and burn to disk option came back but error stays.

---

### Post by widda on 2010-05-26
fstab, fdisk, blkid, come on I know you guys can point me somewhwere here, now that I've done it right:)

---

### Post by widda on 2010-06-02
ok talk to me, or the fstab gets it

---

