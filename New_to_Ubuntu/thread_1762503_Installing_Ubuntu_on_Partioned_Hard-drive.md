---
title: "Installing Ubuntu on Partioned Hard-drive?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-05-19
Hi there

At present I have a hard drive with three primary partitions and one extended (logically split).
I'm runnining win 2k pro in each primary partition.
I'm about to reformat the middle primary partition and would like to  take this opportunity of trying Ubuntu using the middle primary  partition.
I'm using GAG to switch from one partition to another.

Is there any reason why trying Ubuntu in the middle partition would cause problems.
I think I read that Ubuntu can mess up the MBR.
Thaks in advance for your advice!!

McFuzz

---

### Post by philinux on 2011-05-19
> **Mccfuzz said:**
> Hi there

At present I have a hard drive with three primary partitions and one extended (logically split).
I'm runnining win 2k pro in each primary partition.
I'm about to reformat the middle primary partition and would like to  take this opportunity of trying Ubuntu using the middle primary  partition.
I'm using GAG to switch from one partition to another.

Is there any reason why trying Ubuntu in the middle partition would cause problems.
I think I read that Ubuntu can mess up the MBR.
Thaks in advance for your advice!!

McFuzz

When the installer asks you where to install grub choose the partition, e.g sda2, so it installs to the PBR not the MBR.

In previous ubuntu versions this was under the "Advanced" tab during the last phase. Not to be confused with "advanced or manual partitioning". 

You may encounter this error message but I've done this many times without it causing a problem.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]1. it shouldn't cause any trouble at all installing it onto the middle partition. (you have to partition ubuntu yourself --> creating sub partitions, such as /, /home, /boot and swap during the installation process --> it's called advanced installation or sth. like that)

2. Ubuntu is going to install the grub loader, so you will have a different interface, when you're meant to choose the OS you want to use.[/FONT] [FONT=Courier New]

Questions?[/FONT] [FONT=Courier New]

PS: hope this helped [/FONT] [FONT=Courier New]:)[/FONT]

---

### Post by coffeecat on 2011-05-19
Hi, and welcome to the forum.

First question: do you have any Linux experience? The reason I ask is that it is usual to have a dedicated swap partition for Linux and I wondered if you had considered this in your partition layout.

There's no reason why installing Ubuntu to your "middle" partition would cause any problems because Linux doesn't care whether it's on a primary or logical partition - it can boot from either. Unlike a certain other proprietary operating system we won't mention. :)

Ubuntu doesn't mess up the mbr - it installs grub to the mbr which is the boot-loader which comes with most Linux distros and which can boot Windows as well. But if you have your own bootloader on the mbr and wish to keep it, I suppose it would look as though grub has messed it up!

A quick explanation of where grub goes. Some code is installed to the mbr (the first 440 bytes or so) and also some code in the embedding area. This is the part of the hard drive between the partition table and the first sector of the first partition. The remaining grub code responsible for booting, together with the main configuration file, is to be found in the /boot/grub folder of the Ubuntu root partition. I have no experience of GAG but, reading their webpage, it looks as though it uses the embedding area as well. Both grub and GAG are far too complex to fit into the mbr - the Windows mbr code is relatively simple.

If you don't want to use grub and want to keep GAG, when you get to the partitioning stage of the Ubuntu installer, you need to choose the "Manual/Advanced" option in version 10.10 and before. You get a chance to stipulate where grub is installed. I can't remember whether or not you can opt out of installing it at all. In the latest 11.04 release of Ubuntu, the manual option has been renamed to something else. Iirc, it is literally "Something Else".

I have a suggestion. Do you have a live CD? Boot up with the live CD and choose "try Ubuntu" which will take you to the live desktop. Open a terminal and post the output of:

```
sudo fdisk -lu
```This will give us details of your partition layout and we will be able to advise better. In particular it will be easier to see what your middle partition is, how big it is and whether there are likely to be any problems. You can find the terminal under Applications > Accessories in the classic gnome desktop (panels top and bottom) or in the Unity desktop, press the Windows/Super key and start typing "terminal" in the search bar - you'll soon see an icon to click.

---

### Post by Mccfuzz on 2011-05-19
Hi,  
Many thanks for the sppeedy response.

This would be my first venture into Linux.
I had a little play with Ubuntu and it all seemed intuitive  enough  although somewhat slow but I'm assuming that was because I  was running it from the disc.
I was very surprised to find that I could connect to the internet by doing nothing.  Wow!

I think I eventually found the info you requested:-

Disk /dev/sda: 200.0 GB, 200049647616 bytes  
 255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x8a45b80b  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1              63    83955689    41977813+  1c  Hidden W95 FAT32 (LBA)  
 /dev/sda2   *    83955690   167493689    41769000    c  W95 FAT32 (LBA)  
 /dev/sda3       167493690   237135464    34820887+   c  W95 FAT32 (LBA)  
 /dev/sda4       237135465   390716864    76790700    f  W95 Ext'd (LBA)  
 /dev/sda5       237135528   286278299    24571386    b  W95 FAT32  
 /dev/sda6       286278363   390716864    52219251    7  HPFS/NTFS  
 omitting empty partition (5)  
 

 Disk /dev/sdb: 41.1 GB, 41110142976 bytes  
 255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0xee2aee2a  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb2           16065    80292869    40138402+   f  W95 Ext'd (LBA)  
 /dev/sdb5           32193    80292869    40130338+   b  W95 FAT32  
 

 Disk /dev/sdc: 15.4 GB, 15352725504 bytes  
 61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0xc3072e18  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdc1            8064    29985791    14988864    c  W95 FAT32 (LBA)  
 ubuntu@ubuntu:~$ 



Many thanks......MccFuzz

---

### Post by coffeecat on 2011-05-19
I'll just repost your fdisk output in code tags so that it comes out properly formatted and is easier to read, and then I'll post back in a few minutes with a few comments.```

Disk /dev/sda: 200.0 GB, 200049647616 bytes  
 255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x8a45b80b  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1              63    83955689    41977813+  1c  Hidden W95 FAT32 (LBA)  
 /dev/sda2   *    83955690   167493689    41769000    c  W95 FAT32 (LBA)  
 /dev/sda3       167493690   237135464    34820887+   c  W95 FAT32 (LBA)  
 /dev/sda4       237135465   390716864    76790700    f  W95 Ext'd (LBA)  
 /dev/sda5       237135528   286278299    24571386    b  W95 FAT32  
 /dev/sda6       286278363   390716864    52219251    7  HPFS/NTFS  
 omitting empty partition (5)  
 

 Disk /dev/sdb: 41.1 GB, 41110142976 bytes  
 255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0xee2aee2a  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb2           16065    80292869    40138402+   f  W95 Ext'd (LBA)  
 /dev/sdb5           32193    80292869    40130338+   b  W95 FAT32  
 

 Disk /dev/sdc: 15.4 GB, 15352725504 bytes  
 61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0xc3072e18  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdc1            8064    29985791    14988864    c  W95 FAT32 (LBA)  
```

---

### Post by coffeecat on 2011-05-19
> **Mccfuzz said:**
> I had a little play with Ubuntu and it all seemed intuitive  enough  although somewhat slow but I'm assuming that was because I  was running it from the disc.

Yes, it is very slow from the CD. You'll be pleasantly impressed when you run it from a permanent installation.

> **Mccfuzz said:**
> I was very surprised to find that I could connect to the internet by doing nothing.  Wow!

Doesn't surprise me at all. :wink: 

Anyway to your partition layout. I'll ignore your second 41GB/sdb and third 15GB/sdc hard drives as your first post suggests you don't want to use them for Ubuntu.

You have three primary partitions as you say, approximate sizes as follows:

sda1 - 42.9GB
sda2 - 42.8GB
sda3 - 35.7GB

You mention wanting to install to the "middle" partition which I guess would be sda2, but take note that the boot flag is set on that one. If you have Windows installations on the other two primary partitions, you would need to do something about that. Another "wow" for you - you can use the Gparted partitioner in the live CD to set boot flags. Also - your sda1 partition has the hidden flag set. Any reason for that?

The other partitions are your sda4 extended partition which contains the logical partitions sda5 and sda6. Approximate sizes:

sda5 - 25.2GB
sda6 - 53.5GB

By the way, all those "GB" are gigabytes in the strict sense - base 10. Windows' Disk Utility may be showing them in GiB (gibibytes - base 2) in which case the figures will be lower.

I can't see any reason why you cannot install Ubuntu to sda2, taking into account all the comments already made about the bootloader and the need for a swap partition. You could probably shrink one of your logical partitions to make room for a swap partition. A swap partition need only be quite small and can be a logical partition.

You might find this link useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by srs5694 on 2011-05-19
> **coffeecat said:**
> You mention wanting to install to the "middle" partition which I guess would be sda2, but take note that the boot flag is set on that one. If you have Windows installations on the other two primary partitions, you would need to do something about that.

Probably not. Contrary to popular opinion, modern versions of Windows do *not* require the boot/active flag to be set on their boot partitions. (Windows 9x/Me did require this, though.) The standard Windows boot loader uses this flag to determine what to boot, but if some other boot loader is doing the first stage of the boot loader operation, that may not be required. I have no idea what the GAG boot loader does or needs in this respect, though, since I've never used it. Presumably whatever it's doing is working now, though, so I suspect it would be best to just leave this detail alone.

---

### Post by coffeecat on 2011-05-20
> **srs5694 said:**
> Probably not. Contrary to popular opinion, modern versions of Windows do *not* require the boot/active flag to be set on their boot partitions. (Windows 9x/Me did require this, though.) The standard Windows boot loader uses this flag to determine what to boot, but if some other boot loader is doing the first stage of the boot loader operation, that may not be required. I have no idea what the GAG boot loader does or needs in this respect, though, since I've never used it. Presumably whatever it's doing is working now, though, so I suspect it would be best to just leave this detail alone.

Thanks for the correction. I'd noticed that I could boot newer versions of Windows without the boot flag using grub but, like yourself, I have no idea what GAG needs. I was flagging (sorry! :() this point because I assumed that the boot flag was telling us that the OP's currently working Windows is on sda2.

---

### Post by Mccfuzz on 2011-05-20
Hi all,

Before I go ahead just a couple more questions.
With regards to the 2nd partition I will be installing Ubuntu into:
Would it be best to reformat this partition and if so which file system.  It is fat 32 at present.  Using Partition Magic I have various linux options to choose from.
Also the swap partition!  
Is this extended or logical.
Does it matter where on the hard drive I make it?
Any file system for this?
Once again Partition Magic offers the option of  a linux swap partition.

Once again thanks for your advice

Yours MccFuzz

---

### Post by Paqman on 2011-05-20
> **Mccfuzz said:**
> 
Would it be best to reformat this partition and if so which file system.  It is fat 32 at present.  Using Partition Magic I have various linux options to choose from.


The Ubuntu installer will reformat it to EXT4 by default.

> 
Also the swap partition!  
Is this extended or logical.


It would be easiest to create it as a logical partition inside your extended partition. It only needs to be a maximum of the same size as your RAM (and this only if you intend to hibernate the machine)

> Does it matter where on the hard drive I make it?

Nope.

> Any file system for this?

No filesystem as such. A Linux swap space is just a Linux swap space. Again, the installer can do this for you, although you may need to specify "advanced partitioning" if you want to have full control over where things go on the disk.

---

### Post by Mccfuzz on 2011-05-20
Thnx

Think I'm ready to roll now!!

MccFuzz

---

### Post by srs5694 on 2011-05-20
> **Mccfuzz said:**
> With regards to the 2nd partition I will be installing Ubuntu into:
Would it be best to reformat this partition and if so which file system.  It is fat 32 at present.  Using Partition Magic I have various linux options to choose from.

Don't use a non-Linux tool to create a Linux filesystem. If it gives Linux options, it will probably work, but it might create an outmoded version of a filesystem. Instead, do this in the Ubuntu installer. Ext4fs is the default and works fine for most purposes.

> Also the swap partition!  
Is this extended or logical.

I believe you mean "primary or logical." Extended partitions are special primary partitions that serve as placeholders for logical partitions; extended partitions don't hold filesystems or swap space directly.

Linux isn't fussy about primary vs. logical partitions, unlike Windows; you can use either primary or logical for any Linux partition. Given your setup, you won't be able to use a primary partition for swap without juggling some other partitions, since there's a limit of four primary partitions per disk, and you've already got four primaries (including your extended partition), at least on /dev/sda. You could put swap on /dev/sdb, though, as either primary or logical.

> Does it matter where on the hard drive I make it?

Ideally, you should cluster partitions for the same OS together, in order to minimize head movements, which degrade performance. Given your needs, that may not be practical; but if you plan to resize and move partitions as part of this operation, it might be worth considering juggling things around so that Linux resides on two logical partitions at the very end of the disk rather than on the current /dev/sda2 and a logical partition that's well separated from it. OTOH, if you have more than 1 GiB of RAM, you probably won't be using swap space much, so it might not make much difference. Certainly the time, effort, and risk involved in moving partitions around is a point against doing this just to keep the Linux root (/) and swap partitions together. Putting root (/) and swap on two different disks can be equally good, if not better, for performance, assuming the disks are of similar speed.

Another option is to omit the swap partition and use a swap file created on the Linux partition. You'll need to configure that after installing, though; AFAIK, Ubuntu doesn't let you configure a swap file during installation.

---

