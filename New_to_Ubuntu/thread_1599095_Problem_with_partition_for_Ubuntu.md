---
title: "Problem with partition for Ubuntu"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Tensdale on 2010-10-17
I'm trying to install Ubuntu 10.10.
I have a harddisk formatted with NTFS with Windows 7, and the Ubuntu Installation just shows the entire disk as free space. I cannot make a new partition.

I then tried making a new partition in WIndows 7 and formatting it with FAT32 in the hopes the the Ubuntu Installation would be able to see it. But that didn't change a thing.

Now Im typing this in Ubuntu Live where I tried using Gparted to see if I could make a partiton for Ubuntu. But all I see is this:

/dev/sda
Partiton:              File system:      Size:
Unallocated        Unallocated       (698.64 GB)


Can anyone help?

---

### Post by linux-hack on 2010-10-17
if you try a 

```
sudo fdisk -l
```

post the output here ...

---

### Post by linux-hack on 2010-10-17
try installing the NTFS-3G may you don't have 'it .. !!!

---

### Post by Tensdale on 2010-10-17
```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x380769f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       90507   726889472    7  HPFS/NTFS
/dev/sda3           90507       91201     5578752    c  W95 FAT32 (LBA)

```



Looks like it CAN see it. The Ubuntu live that is. The installer stil cant

---

### Post by Quackers on 2010-10-17
You have a GUID partition table rather than MBR. It looks like you may need GNU Parted to see the disk details.

---

### Post by Tensdale on 2010-10-17
Yeah, now we are talking about what programs I need to see the correct partitions.
Not really what I need.

I need a way for the installer to make the correct partitons to install Ubuntu WITHOUT deleting my Windows Installation and all its files.

---

### Post by Quackers on 2010-10-17
I'm not sure (because of the GUID partition) but it is possible that there is a problem with the partitioning of the disk.
May I ask how you resized the Windows 7 partition in order to create space for your new fat32 partition?

---

### Post by Tensdale on 2010-10-17
I chose to shrink it in Disk Management.
Then I fired up on the Ubuntu disk and it still saw the entire drive as free.
Then I formatted it to FAT32 aaaand same problem.

---

### Post by Quackers on 2010-10-17
Well that's definitely the safest way to do it.
I'm not experienced enough with GPT so am unable to offer any constructive advice.
There are others on here who are, and hopefully will be along to help you.

---

### Post by oldfred on 2010-10-17
I thought win7 would not boot from gpt disks? You may have hybrid. But it is the only way windows will work on gpt.

Disadvantages of hybrid gpt/MBR
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

You need to create partitions in advance. You can use gparted but also have to change it to gpt type partitions.

You also need to create a small bios_grub partition with gparted. It will be seen as unknown in most places.
grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. 

I converted one of my 160GB drives to gpt just to know a little more .

---

### Post by srs5694 on 2010-10-17
The problem is that the disk contains a valid straight-MBR setup but it *also* contains GPT data. It's sort of a multiple personality disorder disk. Since Windows is apparently booting from the disk, my guess is that the GPT side is old data -- perhaps the disk was used in a Mac or was used as a GPT data (non-boot) disk for a while, but it was then converted for use as an MBR disk, but the conversion was done using Linux fdisk or some other utility that doesn't understand GPT. (Although recent versions of fdisk do warn about GPT data, as in the example fdisk output in post #4.)

*If* my interpretation is correct, the solution is to wipe the GPT data. This can be done with my [GPT fdisk (gdisk or sgdisk)](http://www.rodsbooks.com/gdisk/) utility. Be sure to download the latest version from the [Sourceforge downloads page;](http://sourceforge.net/projects/gptfdisk/files/) although Ubuntu includes a version, that version is woefully out of date. You should be able to install it in your Ubuntu live CD. With the package installed, type the following command:

```

sudo sgdisk --zap /dev/sda

```

Note that this uses sgdisk, not gdisk. That will "zap" (erase) the GPT data. *Do **not** use the --zap-all option, which wipes out the MBR as well as GPT data!* Thereafter the Ubuntu installer should work correctly, assuming no other problems.

If you believe the disk should actually be a GPT disk, perhaps with a hybrid MBR configuration, then the solution is likely to be more complex. If that's the case, please post the output of "sudo gdisk -l /dev/sda" and "sudo fdisk -lu /dev/sda" and I'll try to advise.

---

### Post by srs5694 on 2010-10-17
> **oldfred said:**
> I thought win7 would not boot from gpt disks? You may have hybrid. But it is the only way windows will work on gpt.

Oldfred posted as I was typing my reply. His advice is reasonable for a true GPT or hybrid disk, but as I wrote in my reply, I believe this is old (unused) GPT data that's causing problems. Note that the MBR has no 0xEE partition, which is a required part of a valid GPT setup.

OTOH, if the disk *should* be a GPT or hybrid disk, restoring that 0xEE partition to the MBR will be necessary.

---

### Post by Tensdale on 2010-10-17
You're right.

I should probably have mentioned that I'm on a iMac which I deleted OSX on and installed windows 7 :/

I'll try your advice in a bit.

---

### Post by Tensdale on 2010-10-17
Okay I just tried sudo sgdisk --zap /dev/sda

aaand
```
ubuntu@ubuntu:~$ sudo sgdisk --zap /dev/sda
Invalid partition data!
GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.
ubuntu@ubuntu:~$ sudo sgdisk --zap /dev/sda

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.
```

So if I understood it right I should now be to make different partitions so I can keep my Windows partiton.

Trying it now

---

### Post by Tensdale on 2010-10-17
Thanks that worked. Created a Ext2 and Swap partition and installed Ubuntu.

I just have another problem now. Im typing this from the Live DVD.

After a while I get a popup with Resticted Drivers Available and I can install the driver for my Broadcom Wireless card.
But this only happens on the Live DVD..

When I boot up on my intalled Ubuntu partiton the Wireless is not working. There is now no additonal drivers to install. What the hell?

---

### Post by srs5694 on 2010-10-18
I'm glad your partition table issue is now fixed. Be aware, though: If you ever want to re-install OS X, you'll have to convert the disk back from MBR to GPT with a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) This isn't difficult (with the help of GPT fdisk), but you should keep it in mind if you ever decide to re-install OS X.

As to the wireless card, I personally don't know the answer to that, although if you type "lspci" you'll get a list of PCI devices. If you can spot the wireless hardware in that list, you might be able to track down the driver by Googling it. You could also post another thread on the topic, since it's an entirely unrelated issue to the partitioning problem referenced by this thread's subject; a new thread might pull in somebody with the knowledge you need.

---

