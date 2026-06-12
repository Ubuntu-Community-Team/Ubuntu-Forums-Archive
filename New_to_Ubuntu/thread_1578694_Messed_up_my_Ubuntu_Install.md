---
title: "Messed up my Ubuntu Install"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Mokbi on 2010-09-20
I mess up my ubuntu install on my MacBook because when I was supposed to install the loader to /dev/sda3 I installed it to sda2 because sda3 didn't show up and now when I try to boot it with my dual boot configuration it says in terminal error loadin operating system. Any way to fix this or manually install the loader? Pleas help as I need ubuntu for school tomorrow and it is very important.

---

### Post by aBaldrich on 2010-09-20
If you don't have any important data in your hard drive you can reinstall it in your main partition, or use the whole disk.

---

### Post by Mokbi on 2010-09-20
> **aBaldrich said:**
> If you don't have any important data in your hard drive you can reinstall it in your main partition, or use the whole disk.

I can't because I am dual booting with Mac os 10.6

---

### Post by sandyd on 2010-09-20
> **Mokbi said:**
> I can't because I am dual booting with Mac os 10.6
boot from the ubuntu cd and post the output of
```

sudo fdisk -l
```

---

### Post by Mokbi on 2010-09-20
> **sandyd said:**
> boot from the ubuntu cd and post the output of
```

sudo fdisk -l
```

ok i will tomorrow i have to sleep now cause it's so late :(

---

### Post by sandyd on 2010-09-20
> **Mokbi said:**
> ok i will tomorrow i have to sleep now cause it's so late :(
alright.
since im in a completely different timezone, ill post the rest of the instructions.
```

sudo mkdir /media/ubuntu
sudo fdisk -l
```
that will give an output of something like
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b30d7

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       41172   330714058+  83  Linux
/dev/sda2           41173       49140    64002960    7  HPFS/NTFS
/dev/sda3           49141       60419    90598567+   7  HPFS/NTFS
/dev/sda4           60420       60801     3068384+   5  Extended
/dev/sda5           60420       60801     3068383+  82  Linux swap / Solaris

```

From this, you will need to find the linux partition.
The partition will have "Linux" under the column. and only the word "Linux", nothing else.
The section under the "Device boot" column of that same row that you found "Linux" in it is what you need.
Ive bolded it.

Note that I will be typing the commands with mine, which is **/dev/sda1** Replace it with your own.

```

sudo mount --bind /dev /media/ubuntu/dev
sudo mount --bind /proc /media/ubuntu/proc
sudo mount **/dev/sda1 **/media/ubuntu
sudo chroot /dev/sda1

```
after typing the chroot command, type

```

grub-install /dev/sda
grub-update

```

---

### Post by Mokbi on 2010-09-21
> **sandyd said:**
> alright.
since im in a completely different timezone, ill post the rest of the instructions.
```

sudo mkdir /media/ubuntu
sudo fdisk -l
```that will give an output of something like
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b30d7

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       41172   330714058+  83  Linux
/dev/sda2           41173       49140    64002960    7  HPFS/NTFS
/dev/sda3           49141       60419    90598567+   7  HPFS/NTFS
/dev/sda4           60420       60801     3068384+   5  Extended
/dev/sda5           60420       60801     3068383+  82  Linux swap / Solaris

```From this, you will need to find the linux partition.
The partition will have "Linux" under the column. and only the word "Linux", nothing else.
The section under the "Device boot" column of that same row that you found "Linux" in it is what you need.
Ive bolded it.

Note that I will be typing the commands with mine, which is **/dev/sda1** Replace it with your own.

```

sudo mount --bind /dev /media/ubuntu/dev
sudo mount --bind /proc /media/ubuntu/proc
sudo mount **/dev/sda1 **/media/ubuntu
sudo chroot /dev/sda1

```after typing the chroot command, type

```

grub-install /dev/sda
grub-update

```

```
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39e739e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       18068   144922472   af  HFS / HFS+
/dev/sda3               1       18068   145128447+  ee  GPT
/dev/sda4           18068       29895    94996480   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount --bind /dev /media /ubuntu/dev
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
ubuntu@ubuntu:~$ sudo mount --bind /proc /media/ubuntu/proc
mount: mount point /media/ubuntu/proc does not exist

```

That's everything that happened. Apparently /media/ubuntu/proc does not exist....

---

### Post by srs5694 on 2010-09-21
I'm afraid sandyd's instructions aren't likely to do much good, since they're based on the assumption that you're using a commodity PC, not a Mac.

That said, the output of fdisk that you posted, Mokbi, reveals at least part of the problem: You've got a corrupt [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) In brief, a hybrid MBR is a flaky and dangerous system that Apple uses to enable dual-booting between OS X and Windows. The usual installation instructions for Linux on Intel-based Macs involve creating a hybrid MBR (although I'm not sure if that term is commonly used in the instructions), and yours has been damaged, probably by a buggy utility. I've seen other posts from people with the same problem. There are several ways to fix the bad hybrid MBR. The simplest is probably this:


[list=1]
[*]Boot your Ubuntu installer or some other emergency disc.
[*]Launch a text-mode shell (terminal) program.
[*]Type "sudo fdisk -u /dev/sda" to launch the fdisk utility on the problem disk.
[*]Type "d" to delete a partition. You'll be asked which partition to delete. Type "3" to delete the duplicate type-0xEE partition.
[*]Type "p" to verify that you've got three partitions, that the first is a type-0xEE partition ("ee" in the "Id" column), and that none of them overlap each other (based on their "Start" and "End" column values). If something looks wrong, type "q" to quit without saving your changes and post details back here.
[*]Type "w" to save your changes.
[/list]


This procedure will "fix" the hybrid MBR. (I put "fix" in quotes because hybrid MBRs violate the GPT specification and so can be considered broken by design.) At this point, you should at least be able to boot OS X. It's conceivable that Linux will boot, but maybe not.

Unfortunately, I don't know all that much about Mac boot loaders or getting Linux to boot on a Mac, so I can't give you specific advice on getting Linux to boot after you've fixed the corrupt hybrid MBR; but I do think that fixing this problem is a necessary first step.

FWIW, in theory you shouldn't need a hybrid MBR at all, since Linux is perfectly happy to boot from a GPT disk, even on a BIOS-based system. The popular instructions for dual-booting OS X and Linux all seem to create a hybrid MBR, though, and maybe there's something about the boot loaders that necessitate it. (If somebody wants to give me an Intel-based Mac I'd be happy to investigate further! ;) )

---

### Post by sandyd on 2010-09-21
> **Mokbi said:**
> ```
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39e739e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       18068   144922472   af  HFS / HFS+
/dev/sda3               1       18068   145128447+  ee  GPT
/dev/sda4           18068       29895    94996480   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount --bind /dev /media /ubuntu/dev
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
ubuntu@ubuntu:~$ sudo mount --bind /proc /media/ubuntu/proc
mount: mount point /media/ubuntu/proc does not exist

```

That's everything that happened. Apparently /media/ubuntu/proc does not exist....

oops. commands in wrong order.  3d line should be run

---

### Post by sandyd on 2010-09-21
> **sandyd said:**
> alright.
since im in a completely different timezone, ill post the rest of the instructions.
```

sudo mkdir /media/ubuntu
sudo fdisk -l
```
that will give an output of something like
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b30d7

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       41172   330714058+  83  Linux
/dev/sda2           41173       49140    64002960    7  HPFS/NTFS
/dev/sda3           49141       60419    90598567+   7  HPFS/NTFS
/dev/sda4           60420       60801     3068384+   5  Extended
/dev/sda5           60420       60801     3068383+  82  Linux swap / Solaris

```

From this, you will need to find the linux partition.
The partition will have "Linux" under the column. and only the word "Linux", nothing else.
The section under the "Device boot" column of that same row that you found "Linux" in it is what you need.
Ive bolded it.

Note that I will be typing the commands with mine, which is **/dev/sda1** Replace it with your own.

```

sudo mount --bind /dev /media/ubuntu/dev
sudo mount --bind /proc /media/ubuntu/proc
sudo mount **/dev/sda1 **/media/ubuntu
sudo chroot /dev/sda1

```
after typing the chroot command, type

```

grub-install /dev/sda
grub-update

```

also install grub-efi (I know that package exists but I dont know the exact name. perhaps someone can point it out?)

---

### Post by Mokbi on 2010-09-21
ok thanks for all the help but I think I have gotten myself into more than I can take so is there a way to delete my ubuntu fully and make my whole partition mac os 10.6? don't worry, I'm going to install Ubuntu as a virtual machine, it's much easier.

can someone please explain how i would erase ubuntu and use the space as mac os 10.6?

---

### Post by Mokbi on 2010-09-21
bump

---

### Post by srs5694 on 2010-09-21
Given the current state of your disk, you *must* fix the bad hybrid MBR, as described in my earlier post. You can do it the way I suggested or you can do it some other way.

Once that's done, you can use GParted from a Linux installation or emergency disc or some other tool to delete the Linux partition(s), then use OS X's Disk Utility from an OS X install disc to resize the OS X partition.

---

