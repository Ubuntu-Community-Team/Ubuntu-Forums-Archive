---
title: "Blown up Partition Table"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by someonedumb on 2011-07-20
Long story short I used an outdated version of GRUB to try to install GRUB on an ext3fs formatted HDD with the commands "setup (hd0)" and "setup (hd0,0)". This ruined the partition table; gparted shows the drive as un-partitioned. I am wondering if there is an easy way to fix/restore the partition table without losing any data?

---

### Post by Bodsda on 2011-07-20
> **someonedumb said:**
> Long story short I used an outdated version of GRUB to try to install GRUB on an ext3fs formatted HDD with the commands "setup (hd0)" and "setup (hd0,0)". This ruined the partition table; gparted shows the drive as un-partitioned. I am wondering if there is an easy way to fix/restore the partition table without losing any data?
 
From memory, those GRUB commands specify where to install the boot loader. They have nothing to do with the editing of the partition table. If gparted is showing the drive as unpartitioned, then it has no partition table at all, and therefore, no data can be accessed on the drive.
 
It is possible that you may have some limited luck with disaster recovery software to get some data back. But it will be very difficult to identify what the data is and, to be honest, is probably not worth your time... 
 
I would reformat the hard drive, and restore the data from your most recent backup... You do take backups, right?
 
Bodsda

---

### Post by someonedumb on 2011-07-20
> From memory, those GRUB commands specify where to install the boot loader. They have nothing to do with the editing of the partition table.

Yes, that is what I thought too. I was attempting to install the GRUB boot-loader. I was quite surprised when I rebooted and found that my previously healthy ext3fs partition no longer existed. Editing the partition table was the last thing I wanted to do.

> It is possible that you may have some limited luck with disaster recovery software to get some data back. But it will be very difficult to identify what the data is and, to be honest, is probably not worth your time...

I would reformat the hard drive, and restore the data from your most recent backup... You do take backups, right?

I was hoping for an easy solution. I thought maybe the partition table and file allocation tables were separate, and that maybe there was an easy way to restore the partition table without overwriting the file allocation table or the data? (Assuming that only the partition table was damaged.)

But I have another copy of most (but not all) of the data that I can probably use to restore from, so I guess I'll start doing that.

Thanks for the reply.

---

### Post by coffeecat on 2011-07-20
Before you reformat, let's have a look at the partition table data. Some easily-fixed partition table irregularities cause Gparted to show the whole drive as unallocated. This is a known bug. Post the output of:

```
sudo fdisk -lu
```

I agree that those legacy grub commands wouldn't have touched the partition table, but let's have a look at its contents anyway.

---

### Post by someonedumb on 2011-07-20
Things just got weird!

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x778efb80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1  3907029167  1953514583+  ee  GPT
```

So I tried to mount it:

```
ubuntu@ubuntu:~$ sudo mkdir /media/test
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/test
mount: special device /dev/sda1 does not exist
```


Doesn't exist? Really?

```
ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda
```

I do not know what to make of these results.

---

### Post by someonedumb on 2011-07-20
> I agree that those legacy grub commands wouldn't have touched the partition table, but let's have a look at its contents anyway.

First thing I tried to do after running the "setup" commands in grub was to boot the drive. Rather than GRUB running properly it just printed "GRUB" to the screen and then the computer locked. Perhaps the damage was done at this point. If the "setup" commands put garbage in the boot sector then I suppose anything could have happened.

---

### Post by Quackers on 2011-07-20
It seems you have a GUID Partition Table. Is there a particular reason for that - like it's a Mac pc, for instance?

---

### Post by someonedumb on 2011-07-20
> It seems you have a GUID Partition Table. Is there a particular reason for that - like it's a Mac pc, for instance?

I'm pretty sure it was an ext3fs partition pre-corruption. (And there would also have been a small swap partition)

My computer is not a Mac.

The partition was originally created by an Ubuntu 9.04 Live CD during an Ubuntu installation.

---

### Post by coffeecat on 2011-07-20
> **someonedumb said:**
> 
I do not know what to make of these results.

I must admit I'm scratching my head here - I never expected a GUID partition table. Note how your sda1 partition starts at sector 1 - if, indeed that is so, because fdisk doesn't support GPT.

Had you been reinstalling grub 2 and you had a GPT with no BIOS boot partition, grub 2 would have bailed out complaining of the lack of a boot partition. I have no experience of legacy grub and GPTs, but it's conceivable that it wrote its stage 1.5 to where it thought the embedding area should be (which you don't get with GPT) and did indeed blow away some important data. I don't know - I'm just theorising.

---

### Post by btindie on 2011-07-20
As the guy above says you have a GUID partition table. The following is the GPT version of the fdisk command, can you paste the output of
```
gdisk -l /dev/sda
```

---

### Post by westie457 on 2011-07-20
Using a LiveCD to remove and reinstall Grub using this link for guidance. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

For the data recovery there is "coffeecat"'s old stand-by program.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

'coffeecat' knows more about this than I do so am going to leave well alone now.

---

### Post by someonedumb on 2011-07-20
```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
sudo: gdisk: command not found
```

Right now I am using an Ubuntu 9.04 Live CD.

I'm second guessing as to whether I used a 9.04 Live CD to install Ubuntu on the drive originally or 9.10. But it was one of those two.

---

### Post by Bodsda on 2011-07-20
> **someonedumb said:**
> ```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
sudo: gdisk: command not found
```
 
Right now I am using an Ubuntu 9.04 Live CD.
 
I'm second guessing as to whether I used a 9.04 Live CD to install Ubuntu on the drive originally or 9.10. But it was one of those two.
 
Are you sure you meant to use gdisk there? Try this one
```

sudo fdisk -l /dev/sda

```
 
HTH,
Bodsda

---

### Post by coffeecat on 2011-07-20
> **Bodsda said:**
> Are you sure you meant to use gdisk there? Try this one
```

sudo fdisk -l /dev/sda

```

Unfortunately, that won't work. It's already been done. See:

> **someonedumb said:**
> Things just got weird!

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! [COLOR="Red"]The util fdisk doesn't support GPT.[/COLOR] Use GNU Parted.


Disk /dev/sda: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x778efb80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1  3907029167  1953514583+  ee  GPT
```


---

### Post by coffeecat on 2011-07-20
> **someonedumb said:**
> ```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
sudo: gdisk: command not found
```

Right now I am using an Ubuntu 9.04 Live CD.

I'm second guessing as to whether I used a 9.04 Live CD to install Ubuntu on the drive originally or 9.10. But it was one of those two.

The suggestion to use gdisk is a good one, but you won't be able to in 9.04 or 9.10 because these are now upsupported and gdisk will have to be installed to the live session. 

Download and run the 10.04 or 11.04 ISO, burn a CD, boot up, connect to the internet and install gdisk and see if you can run it.

---

### Post by srs5694 on 2011-07-20
The disk is a 2 TB model. On such disks, recent versions of Ubuntu tend to use GPT rather than the older and more common MBR, so that explains why the disk is GPT.

The original post specified that an "outdated version of GRUB" was being installed. If this version was old enough that it included no GPT support, then it might well have written its boot code to the MBR, with additional code written *to the sectors immediately after the MBR*. This point is critical because that's where the main GPT data are stored. Thus, this operation might well have wiped out the main GPT data. I can't be sure that this is what caused the problem, but it's my leading hypothesis at this point.

Fortunately, GPT includes backup data at the end of the disk, and those data may still be intact. You'll need to use a GPT partitioning tool that's capable of data recovery for this. I'm not sure how good parted would be, but GPT fdisk (gdisk) will do the job. You can obtain a build of the latest version for Ubuntu 9.04 from the OpenSUSE Build Service (OBS); see the links [here.](http://www.rodsbooks.com/gdisk/download.html#obs) You'd need to install this in your Ubuntu "live CD," which I've not tried; or you could download an Ubuntu 11.04 CD and do an "apt-get install gdisk"; or you could download an emergency system like [System Rescue CD](http://www.sysresccd.org/Main_Page) or [Parted Magic,](http://partedmagic.com/doku.php) which include gdisk.

If you use gdisk, it should scan the disk for GPT data and either fix the problem automatically or offer you recovery options. See my ["Repairing GPT Disks"](http://www.rodsbooks.com/gdisk/repairing.html) page for details. Note that you must use the "w" option to write your changed data back to disk; but *do not* use that option if gdisk doesn't seem to have found your partitions! There's a slim chance that you'll be able to recover the partitions using manual options even if the automatic recovery features don't find anything, but *not* if you use "w" to write a blank or partially-recovered set of partitions!

If you need more guidance, post back with whatever output you can get out of gdisk.

---

### Post by someonedumb on 2011-07-27
Thank you all so much for the replies.

I used an Ubuntu 11.04 CD and ran gdisk. Gdisk automatically repaired the partition table when I ran it and all I had to do was press 'w' to write its changes to disk.

The partition table is fine and everything is working great!

Thanks :D

---

