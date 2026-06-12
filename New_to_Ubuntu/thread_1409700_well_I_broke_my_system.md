---
title: "well I broke my system"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by genetik on 2010-02-17
I was playing simcity under wine and watching youtube when my computer hard locked.  I hit the reset switch on the case and it hasn't loaded the OS successfully since then.  sometimes I'm able to make it all the way to the desktop when I try to boot it, other times it doesn't even make it to the login screen.  

I have three partitions.  One for the OS, a separate /home partition, and another partition, the largest mounted at /storage

If I have to reinstall the OS it isn't a big problem.  I'd just like to make sure my data is OK on the /home and /storage partitions.

I booted an old livecd I had around.  7.10, lol.  When I try to mount the partitions, I get this error message.  

```

mount: wrong fs type, bad option, bad superblock on./dev/sda4
```

these are ext4 partitions, I assume 7.10 can't mount them for that reason.  but the part that says "bad superblock" alarms me.  what does that mean?  

I'm downloading an iso for 9.10.  if I install it, do you think my /home and /storage partitions will be ok?  or might there be a way to recover the system without reinstalling?

please help.

---

### Post by ubunterooster on 2010-02-17
use knoppix to copy all important files. knoppix is a GREAT system recovey tool for any OS. there is a reason it is called the "king of live CDs"

---

### Post by ubunterooster on 2010-02-17
a reinstall will kill all data on the partitions used for the said reinstall!!

---

### Post by genetik on 2010-02-17
> **ubunterooster said:**
> a reinstall will kill all data on the partitions used for the said reinstall!!

is it possible that the data on the other partitions has been corrupted?

---

### Post by ARhere on 2010-02-17
Be very careful.  Make sure to follow the previous suggestion of copying your data to another dive before fixing your PC with knoppix or Ubuntu Live CD.  To suddenly have this error then be given a bad supper block message sounds like something happened to your hard drive hardware.

What is on /dev/sda4?

-Andrew

---

### Post by genetik on 2010-02-17
> **ARhere said:**
> Be very careful.  Make sure to follow the previous suggestion of copying your data to another dive before fixing your PC with knoppix or Ubuntu Live CD.  To suddenly have this error then be given a bad supper block message sounds like something happened to your hard drive hardware.

What is on /dev/sda4?

-Andrew

I get the same message for all three partitions, /dev/sda2, /dev/sda3, and /dev/sda4..  one has the operating system, another is the /home directory, and the third is for media storage.

---

### Post by ubunterooster on 2010-02-17
> **genetik said:**
> is it possible that the data on the other partitions has been corrupted?

try using knoppix to access the data. (knoppix is such a good rescue CD that I used it as my main OS for a good 6 months)

---

### Post by genetik on 2010-02-17
I looked around my apartment and found an ubuntu 8.04 livecd and am now using that.  the problem is that I need a livecd with ext4 support and I don't have a cd-r to put it on.  I do have a 1 gig usb disk though.  however, ubuntu 8.04 doesn't seem to have the "create usb startup disk" tool.

I need help making my usb disk into a livecd with ext4 support.

---

### Post by warp99 on 2010-02-17
You can create a USB startup disk using unetbootin. It's available here for both Linux and Windows:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by genetik on 2010-02-18
My goal right now is to reinstall ubuntu 9.10 and use my old /home partition and my /storage partition as well.

I created a usb startup disk of ubuntu 9.10 using unetbootin.  Using the livecd I can read the /storage partition, but can not read my old /home partition (I guess I need to provide the password of the old account).  

But the bigger problem is that when I try to reinstall ubuntu it doesn't work.  

The installer hangs at 5% at the step ```
Creating an ext4 file system for / in partition #1 of SCSI3 (0,0,0) (sda)...
```

after a few minutes I get the error message ```
The attempt to mount a file system with type ext4 in SCSI3 (0,0,0), partition #1 (sda) at / failed.
```

I have no idea what to do.

---

### Post by genetik on 2010-02-18
I installed a second hard drive to and installed ubuntu onto that since the other drive wouldn't take it for whatever reason.  now, I'm having a problem reading my home directory from my previous install because it is encrypted.  anyhelp?

---

### Post by samantha_ on 2010-02-18
The files (on the old HD) are at
/home/.ecryptfs/<username>

you might want to try and run fsck to see if you can repair the partition enough for you to mount it.

---

### Post by genetik on 2010-02-18
> **samantha_ said:**
> The files (on the old HD) are at
/home/.ecryptfs/<username>

you might want to try and run fsck to see if you can repair the partition enough for you to mount it.

I can mount the partition, I just don't know how to decrypt the data

---

### Post by RJARRRPCGP on 2010-02-18
Looks like a bad HDD. At the least, looks like some bad sectors.

---

### Post by samantha_ on 2010-02-18
> **genetik said:**
> I can mount the partition, I just don't know how to decrypt the data

if you can mount it, mount it, and chroot into the directory.
You will have to mount (bind) the /dev and the /proc directores of your non-problamatic installation to the one in the old HD.

should be something like
```

sudo mount -t ext4 /dev/sdx /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt

```(replace sdax with your partition
the command line should now be in your old HD.

Its currently running in the root account of the old HD, so
youll have to ```
 su *username*
```
to login to your account.

After you login, backup the files any way you wish.
A simple method would be to move them outside of your encrypted home directory. Then, you can just exit the chroot and access the files through /mnt/whatever/directory/you/moved/them/to

EDIT: you might not need to login to your account to access your username, you can just chroot into it and copy the files (root has higher levels than any other account)

speaking of which, an encrypted home folder is useless if other people have physical access to your computer.

---

### Post by Crafty Kisses on 2010-02-18
> **genetik said:**
> I can mount the partition, I just don't know how to decrypt the data

I'm confused, so you can mount the partition? So that means you got the initial error solved? Now since you can mount the partition, you cant access the data on it Is this correct? Either way, can I please see your partition table, so I can actually see what's going on then maybe I can help you further:
```
fdisk -l
```

---

### Post by genetik on 2010-02-18
> **Crafty Kisses said:**
> I'm confused, so you can mount the partition? So that means you got the initial error solved? Now since you can mount the partition, you cant access the data on it Is this correct? Either way, can I please see your partition table, so I can actually see what's going on then maybe I can help you further:
```
fdisk -l
```

fdisk -l doesn't provide any output.

---

### Post by samantha_ on 2010-02-19
> **genetik said:**
> fdisk -l doesn't provide any output.
add sudo in front.

---

### Post by genetik on 2010-02-19
> **samantha_ said:**
> add sudo in front.

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a98e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3           11551      121601   883984657+  83  Linux
/dev/sda4            9976       11550    12651187+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a501a4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         158     1269103+  82  Linux swap / Solaris
/dev/sdb2   *         159        4943    38435512+  83  Linux
/dev/sdb3            4944        9729    38443545   83  Linux

```

/dev/sda3 is my /storage partition
/dev/sda4 is the /home partition from my old installation.  it is the one that is encrypted and unreadable.

/dev/sdb1 is the swap partition of my new install
/dev/sdb2 is / of the new install
/dev/sdb3 is /home for the new install.

and also samantha, I'm having a hard time following your instructions.  when you say to chroot into a directory, I don't know what that means.

---

### Post by genetik on 2010-02-24
still need help reading the encrypted /home directory from my previous install

---

