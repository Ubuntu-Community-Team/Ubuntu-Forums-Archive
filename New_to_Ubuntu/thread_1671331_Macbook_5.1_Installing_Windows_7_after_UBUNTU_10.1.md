---
title: "Macbook 5.1 Installing Windows 7 after UBUNTU 10.10 (refit) Guide"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by alifun on 2011-01-19
Hello. 

Does anyone know if there is straightforward guide to install Windows 7 after Ubuntu 10.10?

My issue is following I have 40gb free unallocated space for windows which I think is ex3.
My ubuntu is installed on ex5 using refit (comprehensive guide used for that). 
I went through forums, read about grub, but didn't find any good tutorial. Because I don't want to mess with ubuntu.
I tried bootcamp but message appears there:" the startup disk cannot be partitioned or restored to a single partition. The startup disk must be reformatted as single mac os extended journaled volume or already be partitioned by bootcamp assistant".
So, I tried to reformat that unallocated space in disk utility as "fat" but windows doesn't recognize it when trying to install.

Please point me the right direction.. 

Thank you!

---

### Post by srs5694 on 2011-01-20
Please post the output of the following two commands, typed in Ubuntu at a shell prompt:

```

sudo fdisk -lu /dev/sda
sudo parted /dev/sda print

```

Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve the formatting. These commands will give us some idea of what sort of partition setup you've got now.

Also, you say that you've got 40 GB of "unallocated" space, but then you say it's "ex3" (ext3?). Unallocated space doesn't normally have filesystems in it. If it's just an unused partition, please identify which one it is from the output of those two commands, if you can.

Another thing: Are you currently using rEFIt to select which OS to boot? If not, what are you using?

Finally, what do you intend to do with your Windows installation? It's conceivable that installing it in a virtual machine will do all you need it to do, so you might consider that; but some people need to give Windows direct access to the hardware (say for gaming).

---

### Post by alifun on 2011-01-21
Thanks a lot for response. I am really enjoying ubuntu experience, though it took some time to get drivers to work...
Back to issue. Windows will be installed for games like Rome total war, and gps navigation.
Yes, my unallocated space doesn't have any file system on it, thats right. 
On Mac EFI I use refit. Basically when I turn on my computer I see "Apple" and "Linux"
When holding "ALT" on startup I see "refit" and "windows".
Here is the result of terminal commands: (I wanted to have windows on one which is 43gb

" ali@Ali-Linux:~$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16fd16fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2          409640   821395807   410493084   af  HFS / HFS+
/dev/sda3   *   821659648   886765567    32552960   83  Linux
/dev/sda4       886765568   889692159     1463296   82  Linux swap / Solaris
ali@Ali-Linux:~$ 
ali@Ali-Linux:~$ sudo parted /dev/sda print
Model: ATA WDC WD5000BEVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI System Partition  boot
 2      210MB   421GB  420GB   hfs+            Untitled
 3      421GB   454GB  33.3GB  ext4            Untitled
 4      454GB   456GB  1498MB  linux-swap(v1)  Untitled
 5      457GB   500GB  43.6GB  fat32           Untitled

ali@Ali-Linux:~$ 


> **srs5694 said:**
> Please post the output of the following two commands, typed in Ubuntu at a shell prompt:

```

sudo fdisk -lu /dev/sda
sudo parted /dev/sda print

```Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve the formatting. These commands will give us some idea of what sort of partition setup you've got now.

Also, you say that you've got 40 GB of "unallocated" space, but then you say it's "ex3" (ext3?). Unallocated space doesn't normally have filesystems in it. If it's just an unused partition, please identify which one it is from the output of those two commands, if you can.

Another thing: Are you currently using rEFIt to select which OS to boot? If not, what are you using?

Finally, what do you intend to do with your Windows installation? It's conceivable that installing it in a virtual machine will do all you need it to do, so you might consider that; but some people need to give Windows direct access to the hardware (say for gaming).

---

### Post by srs5694 on 2011-01-21
> **alifun said:**
> Thanks a lot for response. I am really enjoying ubuntu experience, though it took some time to get drivers to work...
Back to issue. Windows will be installed for games like Rome total war, and gps navigation.
Yes, my unallocated space doesn't have any file system on it, thats right. 
On Mac EFI I use refit. Basically when I turn on my computer I see "Apple" and "Linux"
When holding "ALT" on startup I see "refit" and "windows".
Here is the result of terminal commands: (I wanted to have windows on one which is 43gb

Given your gaming desires, it sounds like installing Windows in a virtual machine may not be optimal. Be aware that there are risks to proceeding further; you may end up losing the ability to boot an OS, or even trashed data because of misbehaving utilities or installers. (You're dealing with a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is flaky and unreliable at the best of times, but necessary to dual-boot OS X and Windows on a Mac.)

Also, in the future, please follow directions. I explicitly asked you to post the fdisk and parted output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This would have made reading your output easier. I'm adding these tags to the below quote, but I'm not sure they'll recover the lost formatting....

> ```
ali@Ali-Linux:~$ sudo parted /dev/sda print
Model: ATA WDC WD5000BEVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI System Partition  boot
 2      210MB   421GB  420GB   hfs+            Untitled
 3      421GB   454GB  33.3GB  ext4            Untitled
 4      454GB   456GB  1498MB  linux-swap(v1)  Untitled
 5      457GB   500GB  43.6GB  fat32           Untitled
```

There's no unallocated space on this disk that I can see; everything's tied up, from 20.5kB to 500GB. (There may be some small gaps, but nothing worth mentioning.)

If you intend to install windows in partition #5 (the "Untitled" FAT32 partition), that's do-able. If you're using that as a data exchange partition, though, you'll need to add another disk or resize one or more existing partitions to make room for Windows. If the latter, the procedure will be similar to the former, but you'll need to do your resizing first. That's inherently risky, but so is installing Windows on this system, so back up first no matter what you do.

Basically, you're going to need to redo your hybrid MBR. You can do this with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program. Download it from [its Sourceforge page;](http://sourceforge.net/projects/gptfdisk/files/) *don't* install the version that's in Ubuntu's repositories, since that version is out of date and has known bugs. Follow the instructions on [my hybrid MBR Web page](http://www.rodsbooks.com/gdisk/hybrid.html) and include the partition(s) that Windows should be able to access in the hybrid MBR. This will be the Windows boot partition and, if you want one, a data exchange partition. Don't bother including the OS X or Ubuntu partitions in the hybrid MBR. You may also want to create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) in gdisk. It can be as small as about 32 KiB (yes, *K*, not *M*), so there may be a gap between partitions in which it will fit without repartitioning anything. Give it a type code of EF02 in gdisk. Alternatively, you can replace the Ubuntu grub-pc package with grub-efi; but this may require some additional work to get it working.

When you're done creating the new hybrid MBR, you should be able to install Windows without dealing with Boot Camp; just treat your Mac like you would a PC. (That said, the Windows drivers that come with Boot Camp may still be useful.)

When you're done, it's possible that Linux will no longer boot. If so, download [Super GRUB 2 Disk](http://www.supergrubdisk.org/) (note that's Super GRUB 2 Disk, not Super GRUB Disk) and use it to boot Ubuntu. Once Ubuntu's booted, typing "sudo grub-install /dev/sda" will probably restore Ubuntu to bootability.

---

