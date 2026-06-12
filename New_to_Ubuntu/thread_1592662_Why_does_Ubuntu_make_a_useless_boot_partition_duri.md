---
title: "Why does Ubuntu make a useless boot partition during install?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by cath0dez on 2010-10-10
I'm on my 5th install in the past month and feel like I am 90% done with being a complete beginner.

One thing that I wonder is why Ubuntu makes a useless boot partition on my dual boot system.

A rundown of my question:
- I use rEFIt to duel boot between OS X and Ubuntu 10.04
- During an install I choose to install to largest continuous free space.
- The installer then creates three partitions in the free space - an empty boot partition, ext4 (includes grub), and the swap.

Why does it create the dummy boot partition?  Having it there creates overlapping partitions and I need to delete it for rEFIt to work.  It took me a LONG time to figure this out during my first install and I am trying to figure out if I can force the installer to not create this partition...

---

### Post by jtarin on 2010-10-10
Can you provide a Gparted screenshot or run the BootInfo script in my signature?
Ubuntu does not create a Dummy partition.....thr is something else going on. You might be looking at an extended partition with your Linux partitions inside.

---

### Post by srs5694 on 2010-10-10
I'm not positive, but I think this may be a bug that causes many Mac users grief. The bug I'm thinking of creates two MBR type-0xEE partitions in the hybrid MBR, one filling most of the disk and the other not. The disk-filling 0xEE partition must be deleted, or the hybrid MBR regenerated completely, to fix the problem. I don't know what program has the bug that creates this problem, but it's presumably whatever creates the hybrid MBR. If I'm right about this problem being the source of your difficulties, this is *not* by design; it's a very major bug in some pretty important (to Mac users) software.

Some further background and advice: Intel-based Macs use the GUID Partition Table (GPT) partitioning system, but to enable Macs to dual-boot with Windows, Apple began using [hybrid MBRs,](http://www.rodsbooks.com/gdisk/hybrid.html) which are ugly and dangerous mixtures of GPT with the older Master Boot Record (MBR) partitioning system used on most PCs.

It's *imperative* that when you discuss partitions on a system that uses a hybrid MBR, you be very explicit about which of the two partitioning systems you mean -- the GPT or the MBR. Unfortunately, most people don't seem to understand hybrid MBRs well enough to know how to handle them, which of course leads to trouble.

Jtarin's suggestion of posting a GParted screen shot and/or the Boot Info Script output is a good one, but in light of the hybrid MBR situation, that information is not sufficient. I recommend posting the output of "sudo fdisk -lu /dev/sda" and "sudo gdisk -l /dev/sda" to show the MBR and GPT partitions, respectively. (The gdisk program isn't installed by default; you'll need to download it from [its Sourceforge page](http://sourceforge.net/projects/gptfdisk/files/) and install it.)

FWIW, although I know a fair amount about GPT and hybrid MBRs (I'm the author of gdisk), I don't know all that much about how Linux boots on Intel-based Macs. I do know that Linux itself is perfectly happy to reside on a conventional GPT disk, so hybrid MBRs are *not* necessary from a Linux perspective. (I've got several Linux systems that boot from GPT on BIOS-based computers.) What I don't know is whether the other tools in the Mac boot chain are happy to boot Linux from a conventional GPT disk. If it can be done, I strongly advise replacing hybrid MBRs with conventional GPT setups to avoid problems. Unfortunately, I can't offer suggestions on how to boot a Mac in this way, and the Web pages I've seen about installing Ubuntu on Macs all seem to assume the use of hybrid MBRs. My suspicion is that the hybrid MBRs aren't really necessary, but perhaps rEFIt relies on them....

---

### Post by jtarin on 2010-10-11
Definitely food for thought and investigation.....thanks for the heads up on that Mac and Gedit usage.

---

### Post by cath0dez on 2010-10-11
> **srs5694 said:**
> 
Jtarin's suggestion of posting a GParted screen shot and/or the Boot Info Script output is a good one, but in light of the hybrid MBR situation, that information is not sufficient. I recommend posting the output of "sudo fdisk -lu /dev/sda" and "sudo gdisk -l /dev/sda" to show the MBR and GPT partitions, respectively. (The gdisk program isn't installed by default; you'll need to download it from [its Sourceforge page](http://sourceforge.net/projects/gptfdisk/files/) and install it.)


Thanks for taking a look at this guys... although I figured out a workaround, I am sure a lot of future mac ubuntu users will run into the same problem.

fdisk output:

```

sblasco@sblasco-ubuntu64:~$ sudo fdisk -lu /dev/sda
[sudo] password for sblasco: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000061a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   910573607   455081984   af  HFS / HFS+
/dev/sda3       910577664   973959167    31690752   83  Linux
/dev/sda4       973959168   976773119     1406976   82  Linux swap / Solaris


```

Gdisk Output:
*The partition numbers reflect the deleted boot partition on 3.
```


sblasco@sblasco-ubuntu64:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Disk identifier (GUID): 00007524-2FCB-0000-F803-00004B5D0000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       910573607   434.0 GiB   AF00  Customer
   4       910577664       973959167   30.2 GiB    0700  
   5       973959168       976773119   1.3 GiB     8200  

```

---

### Post by srs5694 on 2010-10-11
> **cath0dez said:**
> Thanks for taking a look at this guys... although I figured out a workaround, I am sure a lot of future mac ubuntu users will run into the same problem.

I don't which of the partitions shown in the output is the "useless partition" to which you refer. To comment, I'm going to rearrange your output, since the GPT is the master; the MBR mostly just mirrors some of what's in the GPT.

> Gdisk Output:

```

sblasco@sblasco-ubuntu64:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Disk identifier (GUID): 00007524-2FCB-0000-F803-00004B5D0000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       910573607   434.0 GiB   AF00  Customer
   4       910577664       973959167   30.2 GiB    0700  
   5       973959168       976773119   1.3 GiB     8200  

```Partition 1, the EFI System Partition, is more-or-less required on EFI-based systems. (I'm not sure offhand if a Mac would boot without one, but both the EFI specs and Apple say the partition should exist.) Thus, this partition is not useless, and it almost certainly was created by Apple or its software, not by Ubuntu.

Partition 2, named "Customer," is your OS X boot partition.

Partition 3, unamed but with a Code of 0700, is your Linux boot partition.

Partition 4, also unnamed but with a Code of 8200, is a Linux swap partition.

None of these partitions is useless.

> fdisk output:

```

sblasco@sblasco-ubuntu64:~$ sudo fdisk -lu /dev/sda
[sudo] password for sblasco: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000061a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   910573607   455081984   af  HFS / HFS+
/dev/sda3       910577664   973959167    31690752   83  Linux
/dev/sda4       973959168   976773119     1406976   82  Linux swap / Solaris

```Partition 1, of type "ee" (0xEE), is the GPT protective partition. On a plain GPT disk, this partition will span the entire disk (except for the MBR), from sector 1 to the last sector of the disk (or up to the 32-bit limit, on disks over 2 TiB in size). On hybrid MBR disks, like this, this partition is shrunk to make room for the duplicated partitions. Note that you should *never* attempt to use this partition; it exists as a flag that the disk is a GPT disk and to protect these sectors from damage by GPT-unaware utilities, not as a way to access the disk's contents, like other partitions. It's neither a boot partition nor useless; in fact, it's arguably the most important GPT entry, since deleting it will turn the disk from a hybrid MBR disk into a conventional MBR disk with stray GPT data -- a confusing and inconsistent state.

Partitions 2, 3, and 4 are the exact counterparts of partitions 2, 3, and 4 in the GPT. (In principle, the numbers need not align in this way -- MBR partition 2 could point to GPT partition 4, for instance. In your case they do align like this, though.) These partitions exist to enable MBR-only OSes, such as Windows, to access (some of) a GPT disk's data.

Note that Linux, if it has GPT support in the kernel (as Ubuntu does by default, if I'm not mistaken), will see only the GPT partitions, in terms of creating device filename entries like /dev/sda1, etc. This means that in your specific case, /dev/sda1 refers to the *GPT* partition #1; MBR partition #1 is inaccessible from Linux, except as the relevant sectors of the main disk, /dev/sda.

Edit: I mis-read the partition numbers, so some of my comments above are incorrect. See my later post....

---

### Post by cath0dez on 2010-10-11
Okay - I'm not sure that I explained the problem clearly enough.

I found another thread with the exact same situation that I went through.  There was not a definitive answer to why the partition was created, just consensus that it was confusing.

[http://ubuntuforums.org/showthread.php?t=1556993](http://ubuntuforums.org/showthread.php?t=1556993)

That thread included the following pic with an example of the overlapping partition "/dev/sda3".  If you look at the number column in the gdisk output I provided earlier, you can see the partitions are numbered - 1,2,4,5.  In order to get rEFIt to boot into grub I had to delete that partition w/ gparted and use rEFIt's sync tool to get rEFIt working.  I'm not an expert on this, but it seems like rEFIt was pointing to the empty /dev/sda3 partition - deleting and re-syncing points it over to grub installed on /dev/sda4/.

Thanks - I really appreciate the insights.  It seems like this is repeated across mac installs and I would like to file a bug report if needed.


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167080&d=1282356410[/IMG]

---

### Post by srs5694 on 2010-10-11
Sorry; I completely missed that there was a gap in the partition numbering in the gdisk output. [homersimpson]D'oh![/homersimpson]

The partition in question is a BIOS Boot Partition, which is recommended when booting using GPT disks and GRUB 2 on a BIOS-based computer. When GRUB 2 sees such a partition, it places its second-stage boot code in the BIOS Boot Partition. If that partition isn't present, it has to resort to sector block lists, which aren't as reliable. See [this page](http://grub.enbug.org/BIOS_Boot_Partition) for more information.

AFAIK, a BIOS Boot Partition is not required when booting an EFI-based computer using GRUB 2; however, I don't know how the Mac's BIOS emulation enters into the equation. Of course, if you're not using GRUB 2, you don't need a BIOS Boot Partition at all.

The installer probably creates it because it really is recommended on BIOS-based computers. Either the part of the installer that's responsible for this doesn't have ready access to the system type (BIOS vs. EFI) or whoever coded it didn't think to check this detail and adjust it appropriately. In theory and in an ideal world, the worst that happens because its present but unnecessary is that you lose a little disk space and clutter the partition list with one unnecessary partition. Unfortunately, hybrid MBRs muddy the waters.

It seems, that you're confusing *your GPT* /dev/sda3 (a BIOS Boot Partition) with the *other user's MBR* /dev/sda3 (a duplicate of the 0xEE protective partition). You've deleted it, so I can't be sure, but your BIOS Boot Partition probably did *not* overlap with anything. If deleting it and re-syncing your GPT and hybrid MBR fixed some problems, then I'm not sure why this helped. Either way, your hybrid MBR *should* have contained all the entries needed to boot, even if some tool along the way needed to use MBR partitions rather than GPT partitions. My suspicion is therefore that your former hybrid MBR was broken, but that you either re-synced the GPT and MBR with a tool that wasn't broken, or that the bug in whatever tool is creating severely broken hybrid MBRs left and right interacts with the presence of a /dev/sda3 partition in the GPT, such that the bug doesn't manifest when this partition is missing. If my suspicion is correct, the BIOS Boot Partition per se was unrelated to your problems; it was an entirely different hybrid MBR issue.

---

### Post by cath0dez on 2010-10-13
Thanks - I will have to keep a watch on this and post what the tables look like right after I finish an install.

I'm positive that rEFIt puts on an overlapping partition error if I try to sync the table after an install.  Not sure if it is actually overlapping or not.

Thanks for the help. I am going to called this solved until I do another install (hopefully awhile off).

---

