---
title: "GPT Boot Partition set up for Ubuntu only?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by NTL2009 on 2011-04-28
I have searched, but most of the threads lose me in a lot of details on multi-boot. I'm looking for specifics on how to set the correct boot partitions for an EXTERNAL USB GPT drive that will only need to boot Ubuntu, on occasions when I want to try a different system than the one on my internal HDD. My systems are BIOS, not EFI. I would boot into this by selecting the device at boot-up (F12 on my EM725, esc on my PC901), and then GRUB2 should present the available kernels. I do this routinely on another USB external, but I'm confused about the exact boot set-up for GPT.

I have an external 500GB USB drive. I want to use it to experiment with different Ubuntu installations. A while back  I partitioned it as GPT with a series of 8GB and 30GB partitions that I would use as "/" and "/home" for each install. Plus a 5GB swap space that any install could use, and a few larger partitions just for misc data storage. I now forget the exact details of what I chose for any of those boot partitions (if that is even what they are), though I have previously installed some trial systems on this disk and it booted, but I think I've mucked it up with some actions, and I just want be sure I'm starting fresh in the best way.

Using Gparted, I see:

1MB block; file system = "unallocated" at sectors 0-2047, then a
 
100MB block from sectors 2048-16386299; file system = "UNKNOWN", but ID'd as /dev/sdb14

The remaining sdb1~13 are the 8GB & 30GB that I created, some  data partitions and a swap partition I mentioned. All ext4 (except swap, and the these 1MB and 100MB partitions).

I used Gparted to set the bios-grub flag on sdb14.

Here is the output of gdisk (I just installed that), following some instructions from here: 

[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

```
~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 976773167 sectors, 465.8 GiB
Disk identifier (GUID): 4408F7A9-2117-4F03-9391-AF990E47A454
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773133
Total free space is 9080 sectors (4.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          208845        16386299   7.7 GiB     0700  
   2        16386300        77818859   29.3 GiB    0700  
   3        77818860        94205159   7.8 GiB     0700  
   4        94205160       155637719   29.3 GiB    0700  
   5       155637720       172024019   7.8 GiB     0700  
   6       172024020       233456579   29.3 GiB    0700  
   7       233456580       249842879   7.8 GiB     0700  
   8       249842880       311275439   29.3 GiB    0700  
   9       311275440       327661739   7.8 GiB     0700  
  10       327661740       389094299   29.3 GiB    0700  
  11       389094300       399327704   4.9 GiB     8200  
  12       399327705       604124324   97.7 GiB    0700  
  13       604124325       976768064   177.7 GiB   0700  
  14            2048          206847   100.0 MiB   EF02
```

So is this the 'right' way to do it for a simple Ubuntu-only external drive? At this point, I would expect that I would run the 10.04 Lucid installer and select the advanced tab to install the bootloader at 'sdb' (or whatever this shows up as at that time).

I can repartition this too, I don't have too much data on there. or just repartition the boot parts if that is needed?

Some of my confusion is that I don't understand what the 1MB and 100MB blocks represent, and I've read that one of these really should be very small, like 100K? Is the bios-grub flag on the right one? Maybe the 100MB is just something I never formatted? I really don't know. So I'm looking for confirmation or advice before I try to install systems.

TIA - NTL2009

---

### Post by cariboo on 2011-04-28
I've noticed that unless you specify not to, gparted will leave a small section of the hard drive unallocated, before and after any partitions. They don't seem to make any difference as far as operation goes. If you want to leave whats on your internal hard drive alone, and boot from the external drive when it's connected. install grub on the mbr of the external drive. You'll have to use the manual partitioning option during the install process, as that's the only way to specify where to install grub.

---

### Post by NTL2009 on 2011-04-28
OK, thanks. Before I do that, I just want to check - do I leave these two blocks as they are, or should they be formatted differently?  And which (if any) should have the bios-grub flag set?

> 1MB block; file system = "unallocated" at sectors 0-2047, then a

100MB block from sectors 2048-16386299; file system = "UNKNOWN", but ID'd as /dev/sdb14

I set the set the bios-grub flag on sdb14 (the 100MB block) with Gparted, but I have no idea if that is correct or if th grub installer even cares.

NTL2009

---

### Post by oldfred on 2011-04-28
That is correct. The bios-grub partition is left unformated and is just used as space for grub to install part of its boot.

This is my flash drive.

```
fred@fred-MavericDT:~$ sudo parted /dev/sde print
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sde: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name          Flags
 1      1049kB  2097kB  1049kB               KingstonData  bios_grub
 2      2097kB  7552MB  7550MB  ext4
 3      7552MB  16.1GB  8511MB  ext4

```

I formated before I learned about alignment:

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

---

### Post by NTL2009 on 2011-04-28
> **oldfred said:**
> That is correct. The bios-grub partition is left unformated and is just used as space for grub to install part of its boot.


OK, I gotta run, will try an install tomorrow and report back. 

Thanks - NTL2009

---

### Post by srs5694 on 2011-04-28
Your 100MiB partition is a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) 100 MiB is much larger than is required for that (it can be as small as 31 or 32 KiB, IIRC), but given the size of your disk, it's not a big deal to make it that big.

Most partitioning tools today try to align partitions' start points on 1 MiB boundaries. This is done for performance reasons -- Advanced Format hard disks, SSDs, and certain types of RAID configurations can all suffer degraded performance if partitions are not properly aligned. Alignment details differ from one drive or technology to another, but they're all power-of-2 multiples of sectors, and they're mostly in the range of 4 KiB to 256 KiB, so a 1 MiB alignment policy is fairly sensible. Since some sectors at the start of the disk are used by the partition table, that leaves close to 1 MiB unpartitioned at the start of a disk. This is perfectly normal. You could put your BIOS Boot Partition in that space if you wanted to (it's a big enough space, and since it's seldom written the performance penalty would be unnoticeable even if you've got an Advanced Format drive), but there's not much point in repartitioning just for this.

Given your needs, I personally would make a couple of changes. First, instead of creating thirteen partitions (which you'll never be able to keep straight), I'd create about four: the BIOS Boot Partition, a [Logical Volume Manager (LVM)](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) partition, and a couple of /boot partitions. (If I wanted to retain the option of accessing the disk from Windows I'd create two or three LVM partitions; you could then deactivate one of them and turn it into a FAT or NTFS partition in the future. The LVM as a whole would still be one big contiguous space.) I'd then put the Linux installations in the LVM, using one of the /boot partitions to hold the main GRUB installation (from whatever distribution you use for this purpose). I'd hold the second /boot partition in reserve in case you want to change the boot loader configuration; you could experiment with the second configuration while keeping the old one mostly intact. (Most of the distributions' /boot directories would go in their root filesystems in the LVM.) This configuration gives you added flexibility, since it's easier and safer to resize logical volumes in an LVM than it is to resize partitions. Logical volumes are also referred to by name, as in /dev/mylvm/fedora15_root for a root (/) filesystem holding Fedora 15 in the mylvm volume group. (You can give the volume groups and logical volumes any names you like.)

Another thing I'd change is the separate /home partition for each distribution. That will get awkward and confusing very quickly. I'd use a single /home logical volume and put my own personal home directory in a separate subdirectory for each installation -- say, /home/f15_ntl for Fedora 15, /home/u1104_ntl for Ubuntu 11.04, and so on. As it is now, you've got your /home partitions split up six ways, which degrades your ability to store large files or large numbers of mid-sized files. Using a single /home volume will greatly increase your flexibility on that score. Note that you could do this even if you decide that LVM is too much hassle to learn; you'd just create a single /home partition rather than a /home logical volume.

One more minor point: One of GPT's advantages is that you can give each partition its own name. Those are currently not set. You can set the name in gdisk or in parted, but GParted doesn't display the partition name; instead, it displays the filesystem name (which is distinct from the partition name). Setting both names appropriately can help you keep track of the partitions, particularly if you stick with your 14-partition approach. That's not as convenient as using logical volume names, but it's better than nothing. The big drawback is that if you don't keep the names updated when you install new distributions, you could end up with confusing old names that no longer apply.

---

### Post by NTL2009 on 2011-04-29
Thanks to oldfred & srs5694 for confirming that the setup should be workable as is. I wanted that verification before I proceeded.

srs5694 - yes, I'm a bit gun-shy on changing to LVM, I'm just getting the GPT setup working and I need to take it a step at a time, I still have trouble wrapping my head around all the interconnections between MBRs, GRUBs, fstab across partitions and so on.

But I did grasp your comments on not needed all those /home partitions, thanks for that, I didn't really think about it that way,  I just mentally associated an install with its own /home, but I see that there is no reason that several installs couldn't use a single /home (as they do swap). For now though, for the experimenting I'm doing, I'm going to leave it as is. But I will try at least one install on there where I point it to an existing /home (and tell the installer to NOT format that partition) - that should (if I get this right), just let it 'pick it up' as its own /home. I should be able to see that reflected in the UUIDs in that installs etc/fstab.

At any rate, with the confirmation from you that this boot partition looked OK, I did some work to make it bootable again (one of my experiments seemed to have hosed it). I was going to do an install to a partition, and let the installer do the bootloader to the root of that drive, but since I had recently did a fresh install on one of those partition pairs (sdb5&6 on the system below), and I hadn't messed with that, I just did this:

kenc@EM725UB:~$ sudo mount /dev/sdb5 /mnt 
kenc@EM725UB:~$ sudo grub-install --root-directory=/mnt /dev/sdb 
Installation finished. No error reported. 
kenc@EM725UB:~$ sudo umount /mnt 

That seemed to clean everything up, and all my normally installed systems boot fine now.

I guess I'm not clear if mounting sdb5 was needed. I don't know if the grub-install uses the info that the sdb5 gathered when it was installed, or if grub-install goes out to the disk and looks for kernels and UUIDs on its own? 

I am interested now in the separate /boot partition you mentioned. I've avoided that as it seemed a bit more complex, but it might actually simplify things for the experimenting I'm doing.

Thanks - NTL2009

---

### Post by srs5694 on 2011-04-29
> **NTL2009 said:**
> I am interested now in the separate /boot partition you mentioned. I've avoided that as it seemed a bit more complex, but it might actually simplify things for the experimenting I'm doing.

Ordinarily, a separate /boot partition isn't required. The advantages in the setup I recommended are two-fold, though:


[list]
[*]GRUB Legacy can't read files from an LVM, so if you installed a distribution that used GRUB Legacy and then used GRUB Legacy as part of the boot process, you might need a /boot partition (or some other non-LVM partition) to store the kernel, initial RAM disk, and GRUB configuration files. If you're not using an LVM, or if you use GRUB 2 exclusively, this reason doesn't apply.
[*]In multi-boot configurations with multiple Linux distributions, I find that it's easy to lose track of which distribution's GRUB is in charge. Putting the "master" GRUB on its own separate /boot partition helps make that more obvious, and can also preserve that GRUB installation should you decide to wipe that particular installation. If you don't re-use or wipe that /boot partition, you'd then have an "orphaned," but still functional, GRUB configuration, so your system will still boot the installations you didn't wipe. You could continue using this setup, but with manual GRUB updates, or reconfigure another installation to use that /boot partition or the spare one, as you see fit. This reason still applies to your configuration even if you don't use LVMs.
[/list]


Oh, and a good size for a /boot partition is about 200 MiB. My currently-booted systems use between 34 MiB and 59 MiB on /boot, but I've had the value exceed 100 MiB in the past (with several kernels installed).

---

### Post by NTL2009 on 2011-04-29
Very interesting...> **srs5694 said:**
> Ordinarily, a separate /boot partition isn't required. The advantages in the setup I recommended are two-fold, though:

... or if you use GRUB 2 exclusively, this reason doesn't apply.

OK, I'm totally on GRUB2...


> In multi-boot configurations with multiple Linux distributions, I find that it's easy to lose track of which distribution's GRUB is in charge. 

It's not just me (heh-heh)?  This is driving me in circles, I guess I need to understand just who is 'in charge' when I do a grub-update or install when there are multiple system on the disk. Which one is providing the info, and afterwards, how would you know?

> Putting the "master" GRUB on its own separate /boot partition helps make that more obvious, and can also preserve that GRUB installation should you decide to wipe that particular installation. If you don't re-use or wipe that /boot partition, you'd then have an "orphaned," but still functional, GRUB configuration, so your system will still boot the installations you didn't wipe. 

This is what I was starting to get, and why I thought that a separate /boot might make sense for me in this case. 

Well, I took the first step, and created a partition to use as /boot , then I did a fresh install, but not formatting the  /home that was already there, but telling it to use that /boot mount. I told the installer to put the bootloader on the root of that external drive, and it seems o boot properly, mounting the /boot partition.  And the old installs still boot using their /boot folder.


Next step is to do another install and see two installs 'share' this /boot partition.

-NTL2009

---

### Post by srs5694 on 2011-04-29
The boot process on BIOS-based computers can vary quite a bit and can become quite tangled, so it's hard to lay out an absolute set of rules; however, in a typical single-drive Linux installation, it goes something like this:


[list=1]
[*]The BIOS runs and does various self-checks.
[*]The BIOS checks the MBR of the hard disk for boot code and runs that code. This is where GRUB's first stage resides (/dev/sda).
[*]GRUB loads secondary boot code stored in unallocated space after the MBR or, in the case of GPT disks, in the BIOS Boot Partition.
[*]GRUB locates its boot files in a Linux root (/) or /boot partition and loads them, including both GRUB modules (in the case of GRUB 2) and the GRUB configuration file.
[*]The GRUB configuration file, in conjunction with the user's choice, directs GRUB to load a Linux kernel and initial RAM disk (or another OS, typically by chain-loading another boot loader located elsewhere).
[/list]


When you install GRUB (either in an OS installer or by using grub-install), you give it a location. If you tell it to install in the MBR of the disk (by specifying /dev/sda as the location), GRUB overwrites the MBR code and the post-MBR/BIOS Boot Partition code, which has the effect of having *that* GRUB installation "take over" the computer. If, OTOH, you tell GRUB to install in the boot sector of a partition (by specifying, say, /dev/sda5 as the location), GRUB installs there, where it can act as a secondary boot loader -- another GRUB or some non-GRUB boot loader can be installed in the MBR and chain-load to GRUB in the Linux partition.

When multi-booting two or more Linux installations, *only one* can install GRUB to the MBR. (If you install one there and then install another there, the second one overwrites the first.) Thus, the last GRUB you install to the MBR takes over as the primary boot loader. You can either rely on that GRUB to boot everything directly or you can have the primary GRUB installation chain-load secondary GRUB installations in Linux root (/) or /boot partitions.

My suggestion of having a separate /boot partition is partly just a mnemonic device; by setting it aside, you make it easier to remember that it's *that* installation's GRUB that's the primary one. It also, though, can help to protect it; if you have no /boot partitions and re-use the root (/) partition that happens to be associated with the primary GRUB installation, the new installation will have to take over those duties. Having it do so correctly may take some fiddling, since GRUB's auto-detection scripts don't always work correctly. If you use a separate /boot partition, OTOH, then the system will always boot at least the OSes you *don't* replace so long as you tell the new installation to put its boot loader in the Linux root (/) partition (or to not install a boot loader at all).

---

