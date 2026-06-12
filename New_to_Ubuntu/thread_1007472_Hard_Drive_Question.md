---
title: "Hard Drive Question"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Squizz on 2008-12-10
Hi

I have a Samsung 400gb hard drive, that I used to be able to read in Windows and Ubuntu.  However, since formatting it I can only see it in Ubuntu.  I've tried it as ext2/ext3/fat32/unformatted and Windows can't seem to detect it at all.

I can see it in the BIOS, but I can't see it in Windows Disk Management or on the Windows partition maker on the install CD.

Any idea what's wrong with it?

---

### Post by Michael.Godawski on 2008-12-10
hi Squizz
> 
I have a Samsung 400gb hard drive, that I used to be able to read in Windows and Ubuntu

When the drive was readable by both systems, what was the format type then?

Can you please post the output from this command:

```
sudo fdisk -l
```

---

### Post by Squizz on 2008-12-10
I don't really remember what it was, I didn't think to check to be honest!  It's currently not formatted as anything.  I haven't tried ntfs yet, as gparted doesn't want to do it for some reason.

Here's the output of fdisk

```

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057313

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c7960

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12331    99048726   83  Linux
/dev/sdb2   *       12332       18705    51199155    7  HPFS/NTFS
/dev/sdb3           18706       19457     6040440    5  Extended
/dev/sdb5           18706       19457     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04a104a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30394   244139773+   b  W95 FAT32

Disk /dev/sdd: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ae2f38e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30394   244139773+   b  W95 FAT32

```

---

### Post by tomtom1982 on 2008-12-10
Your 400GB HDD isn´t formatted. 
You should try ntfs.

Please check if ntfs-3g is installed.

If it´s not, you can install it with

```
sudo apt-get install ntfs-3g
```

in a terminal.

---

### Post by tomtom1982 on 2008-12-10
You also can format to ext2/ext3 and install ext2/3-drivers for windows.

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by Squizz on 2008-12-10
ntfs-3g is already installed, so I installed ntfsprogs so I could use gparted to format the drive to ntfs. 

Again it worked fine in Ubuntu but the drive is still not visible in Windows. :(

---

### Post by Keen101 on 2008-12-10
well, just so you know formatting and partitioning are two different things. I've never formatted a drive in linux, but the "fdisk" command in a terminal should work as long as you know what parameters to give it. Try "fdisk --help" to figure out the parameters. Once it's formatted, but not partitioned theoretically it should be detectable by windows disk manager, and you should be able to partition it from there. If not you could try partitioning it with fdisk or gparted again. I've never like ntfs drive myself, and have always preferred FAT32.

---

### Post by Squizz on 2008-12-10
> **Keen101 said:**
> well, just so you know formatting and partitioning are two different things. I've never formatted a drive in linux, but the "fdisk" command in a terminal should work as long as you know what parameters to give it. Try "fdisk --help" to figure out the parameters. Once it's formatted, but not partitioned theoretically it should be detectable by windows disk manager, and you should be able to partition it from there. If not you could try partitioning it with fdisk or gparted again. I've never like ntfs drive myself, and have always preferred FAT32.

Thanks for that, but I can format the disk in fat32/ext2/ext3/ntfs as much as I like - but the problem is that I cannot see the disk in Windows, regardless of which it is.  I don't need any partitions on it, I just need to be able to see that it's there in Windows like I can in Ubuntu or my BIOS.

---

### Post by Squizz on 2008-12-10
I can see it in Device Manager in Windows - any idea if I can do anything with it from there?

If I uninstall it and scan for hardware, it finds and 'installs' it, but still can't use it.

---

### Post by Keen101 on 2008-12-12
Try this from windows if this is your last resort:

>Start

>Control Panel

>Administrative tools

>Computer Management

>Disk Management

(most people who use windows don't know about this tool, but it can be very useful)

If the drive is detectable from windows, then you should be able to format it from here. If not, then i don't know what to tell you. I guess get a new usb hard drive enclosure.

---

### Post by Kellemora on 2008-12-12
HI Squizz

If you plan on using it on WinDOZE, it's best to format it on WinDOZE!
Else it won't have a Gates keeper ;-)
Then connect it to your Ubuntu Box!

TTUL
Gary

---

