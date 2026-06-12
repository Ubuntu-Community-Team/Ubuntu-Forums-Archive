---
title: "Problems With USB Drive.."
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Riku Reed on 2011-05-28
Whenever I plug in my 4 Gigabyte USB flash drive. This message appears on my screen.
> Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm trying to format my USB drive as either FAT32 or FAT16, whenever I open up gparted it crashes when it detects my USB drive. But when it's not plugged in it works fine?
I also tried to test it out with my other USB flash drive. It detected it flawlessly.

So because I was stumped. I tried to put the Fedora 15 LXDE ISO onto the other flash drive. The ISO is 492.0 MB (515899392 bytes). My flash drive can hold up to 512 Migabytes. But whenever I use Unetbootin to apply that ISO to that flash drive it's keeps telling me theirs not enough space left on the device. How reliable even after I formatted it it still keeps saying that. So after looking through my flash drive I noticed through Gparted it said that their out of 495 or so it said 17 Megabytes was of something was on their. I looked through and saw the .trash file and found that as the problem. Now my only question is how do I delete it? Or the files within it? It says it read only. I tried to pull up nautilus as root and delete the files but nautilus running in root can't detect my USB drive? -_- jeez after just trying to download a ISO do I have to go through all these problems.

---

### Post by Riku Reed on 2011-05-28
When I tried looking into my 4 Gigabyte USB flash drive. I tried:
> fdisk -l /dev/sdb

Disk /dev/sdb: 3985 MB, 3985637376 bytes
64 heads, 32 sectors/track, 3801 cylinders, total 7784448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2dcabc60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7784447     3891200    6  FAT16So then,
> fsck /dev/sdb1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Tried these out see if it'd show anything. Still back to my main problem, anyone know what I should do?
If it's saying bad "superblocks" should I get a new USB drive or is their a way to fix this one.

On the other hand I still have no luck with my 512 Megabyte, I tried to view back again to see what files were in the .trash, now that won't show??

---

### Post by garvinrick4 on 2011-05-28
Do not believe you can run fsck on fat format.
Is a 4 gig flash drive with one partition with a boot flag so you installed something
on it. If using a USB creator with persistence up to 4 gig will be in fat.

---

