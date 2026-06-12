---
title: "Second HD Not Being Used"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Cheemag on 2009-01-17
After re-installing Ibex, I'm now slowly updating my installation.

The first problem is that, although I have two hard discs, Ubuntu
is only using one according to the drive space monitor thing. :(

How do I bring the other drive into use without having to install
the system again?

---

### Post by northern lights on 2009-01-17
Are both disks internal devices?

Can you please post the outputs of ```
sudo fdisk -l
```and```
cat /etc/fstab
```Thank you.

---

### Post by Cheemag on 2009-01-17
> **northern lights said:**
> Are both disks internal devices?

Can you please post the outputs of ```
sudo fdisk -l
```and```
cat /etc/fstab
```Thank you.

Thank you NL.

I wasn't planning to play Linux today, but never mind:

sudo fdisk -l:
-------------

jim@CC:~$ sudo fdisk -l
[sudo] password for jim: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b418

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38347   308022246   83  Linux
/dev/sda2           38348       38913     4546395    5  Extended
/dev/sda5           38348       38913     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc66cc66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14596   117242338+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xa6ab014e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc4   *           1          96       98288    6  FAT16

Disk /dev/sdd: 4127 MB, 4127195136 bytes
127 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?       98824      243796   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(98823, 58, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(243795, 59, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?       21424      267300   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21423, 77, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(267299, 87, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?      237476      483352   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(237475, 53, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(483351, 62, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?      366483      366490       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(366482, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(366489, 36, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
jim@CC:~$ 

===========================================================
cat /etc/fstab:
---------------

jim@CC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=72ffe038-17cf-4f0e-a70c-86a7bec12678 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f2decd7d-b512-4430-a620-40a767b655a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jim@CC:~$ 
========================================================

Hope this makes sense to you, NL. Thanks again.

:)

---

### Post by northern lights on 2009-01-17
mkey.

First off, for you to make sense of the output:
*fdisk* is the standard *nix partition table manipulator. With the *-l* option, it lists all devices mentioned in */proc/partitions/*. */dev/sda* is your first 320gig harddisk with the Ubuntu install. */dev/sdc* appears to be a flashdrive, sdcard or the like. */dev/sdd* is your MP3/media player. */dev/sdb* is the second drive you don't have access to currently. It's a bit trifling why you don't "see" it at all - it should appear under "Places" by default and be mountable as root.

Anyhow, we'll set it up such that you can mount it as a simple user and such that it's mounted at system start automatically. This is where *fstab* comes in. *fstab* is a configuration file that contains information of all the partitions and storage devices in your machine. The file is located under */etc*, so you need root rights to edit it.

Open it in gedit as root:```
gksu gedit /etc/fstab
```
and subsequently add the following line to the end of the file. Leave the rest unaltered.
```
/dev/sdb1	  /media/fat  vfat    auto,user,rw,relatime    0       0

```
Save. Now on the next boot, there should be an entry under "Places" along the lines of "120.0 GB Media". It will be mounted already, clicking it should not result in a password prompt but open a nautilus (filemanager) instance directly.

---

### Post by Cheemag on 2009-01-21
> **northern lights said:**
> mkey.

First off, for you to make sense of the output:
*fdisk* is the standard *nix partition table manipulator. With the *-l* option, it lists all devices mentioned in */proc/partitions/*. */dev/sda* is your first 320gig harddisk with the Ubuntu install. */dev/sdc* appears to be a flashdrive, sdcard or the like. */dev/sdd* is your MP3/media player. */dev/sdb* is the second drive you don't have access to currently. It's a bit trifling why you don't "see" it at all - it should appear under "Places" by default and be mountable as root.

Anyhow, we'll set it up such that you can mount it as a simple user and such that it's mounted at system start automatically. This is where *fstab* comes in. *fstab* is a configuration file that contains information of all the partitions and storage devices in your machine. The file is located under */etc*, so you need root rights to edit it.

Open it in gedit as root:```
gksu gedit /etc/fstab
```
and subsequently add the following line to the end of the file. Leave the rest unaltered.
```
/dev/sdb1	  /media/fat  vfat    auto,user,rw,relatime    0       0

```
Save. Now on the next boot, there should be an entry under "Places" along the lines of "120.0 GB Media". It will be mounted already, clicking it should not result in a password prompt but open a nautilus (filemanager) instance directly.

Only partially successful. It's in "Places" as HD-D (the previous
Windows name for the drive), but I cannot mount it:

 "You are not privileged to mount the volume HD-D"

Changing sdb1 to HD-D in /etc/fstab allowed the drive to be
mounted after authentications. However I have to mount it
explicitly after boot. It isn't automatic.

---

### Post by northern lights on 2009-01-21
> **Cheemag said:**
> However I have to mount it
explicitly after boot. It isn't automatic.

*auto* should make it automount. To avoid having to authenticate yourself though, add the *uid* mountoption. If your user is the one you created at installation, use```
/dev/sdb1	  /media/fat  vfat    auto,user,rw,relatime,uid=1000    0       0
```

---

### Post by Cheemag on 2009-01-21
> **northern lights said:**
> *auto* should make it automount. To avoid having to authenticate yourself though, add the *uid* mountoption. If your user is the one you created at installation, use```
/dev/sdb1	  /media/fat  vfat    auto,user,rw,relatime,uid=1000    0       0
```

Done that, restarted, still have to mount it myself.

There's only one user.

I get an error at the command prompt after saving about it being
unable to write a particular file. I'll post details of the error
if it's important.

---

### Post by northern lights on 2009-01-21
> **Cheemag said:**
> Done that, restarted, still have to mount it myself.Wicked. Not only shouldn't you have to, but with the same parameters, my internal FAT partition automounts and is writeable. This is directly copied from my *fstab*:```
/dev/sda9	/media/music	vfat    user,rw,noatime,uid=1000,auto	0       0
```
and neither the *atime* settings, not the placement of *auto* should make a difference. [Related Reading]("http://www.tuxfiles.org/linuxhelp/fstab.html"), further you can check [man mount]("http://linux.die.net/man/8/mount").

> **Cheemag said:**
> There's only one user.
I get an error at the command prompt after saving about it being
unable to write a particular file. I'll post details of the error
if it's important.
Rather, could you post the output of```
id
```
(or verify the 1000 yourself)

---

### Post by Miljet on 2009-01-21
Northern Lights,
I think it is possible that the changes are not being saved to fstab.
> I get an error at the command prompt after saving about it being
unable to write a particular file. I'll post details of the error
if it's important.

---

### Post by northern lights on 2009-01-21
> **Miljet said:**
> Northern Lights,
I think it is possible that the changes are not being saved to fstab.
mkey. Possible. I figured the OP meant not being able to save a file to his FAT partition. Maybe it's not saving fstab.

@the OP:
Have you openend fstab as root?

Either use "*sudo nano ...*", or exactly what I've written above```
gksu gedit /etc/fstab
```you can invoke this from the Alt+F2 run dialog also.

---

### Post by Cheemag on 2009-01-22
> **northern lights said:**
> Wicked. Not only shouldn't you have to, but with the same parameters, my internal FAT partition automounts and is writeable. This is directly copied from my *fstab*:```
/dev/sda9	/media/music	vfat    user,rw,noatime,uid=1000,auto	0       0
```
and neither the *atime* settings, not the placement of *auto* should make a difference. [Related Reading]("http://www.tuxfiles.org/linuxhelp/fstab.html"), further you can check [man mount]("http://linux.die.net/man/8/mount").


Rather, could you post the output of```
id
```
(or verify the 1000 yourself)

You've lost me now. Code? id?

---

### Post by Cheemag on 2009-01-22
> **Miljet said:**
> Northern Lights,
I think it is possible that the changes are not being saved to fstab.

Highly likely given the error message at the end of the edit.

I'm not playing Linux today, but I'll post the details of the
error message tomorrow.

However, the drive is in Places and can be mounted and used.

What I'm going to use it for is another matter!

---

### Post by phantomgunex on 2009-01-22
Is your jumper settings for both drives correct???

---

### Post by Cheemag on 2009-01-22
> **northern lights said:**
> mkey. Possible. I figured the OP meant not being able to save a file to his FAT partition. Maybe it's not saving fstab.

@the OP:
Have you openend fstab as root?

Either use "*sudo nano ...*", or exactly what I've written above```
gksu gedit /etc/fstab
```you can invoke this from the Alt+F2 run dialog also.

I can edit and save fstab, but get an error message at the command prompt after saving and exiting the editor. The changes to fstab ARE being saved and I can use the FAT drive once I mount it.

Man, you're dealing with a novice here "open as root" ???
"sudo nano" ???  Alt-F2 run dialogue ???? You're up against it here!!

---

### Post by Cheemag on 2009-01-22
> **phantomgunex said:**
> Is your jumper settings for both drives correct???

Well yes, otherwise the drive just would not function.

I have the drive in Places and I can use it - it just doesn't mount automatically.

---

### Post by Cheemag on 2009-01-31
> **northern lights said:**
> Wicked. Not only shouldn't you have to, but with the same parameters, my internal FAT partition automounts and is writeable. This is directly copied from my *fstab*:```
/dev/sda9	/media/music	vfat    user,rw,noatime,uid=1000,auto	0       0
```
and neither the *atime* settings, not the placement of *auto* should make a difference. [Related Reading]("http://www.tuxfiles.org/linuxhelp/fstab.html"), further you can check [man mount]("http://linux.die.net/man/8/mount").


Rather, could you post the output of```
id
```
(or verify the 1000 yourself)

Sorry to have been away so long.

Output of id is:

jim@CC:~$id

uid=1000(jim) gid=1000(jim) groups=4(adm),20(dialout),24(cdrom),
46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(jim)
jim@CC:~$

So the uid=1000 is being recognised.

I'm no longer getting that error when I save the edit of fstab,
but the drive still doesn't mount. I have taken all the updates available today.

It isn't a great problem having to mount the second HD, but I'd like it to mount itself!

---

### Post by Cheemag on 2009-01-31
> **phantomgunex said:**
> Is your jumper settings for both drives correct???

Must be, otherwise the system wouldn't see it. Bios settings are:

Primary Master: Auto
Primary Slave: 120.1 GB blah, blah ...
Secondary Master: DVD-ROM
Secondary Slave: ARMD-HDD:ZIP

---

