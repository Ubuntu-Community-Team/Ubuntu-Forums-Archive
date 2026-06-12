---
title: "Additional drive is mounted to /"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-09-23
Whenever I boot up, Ubuntu automatically grabs one of my additional storage HDDs and mount's it to /

I cannot get this HDD to appear for access in GDM. How can I prevent this automounting to / from happening?

Thanks,
Kurt

EDIT:
I switched some drives around. It appears that it is always the drive /sda that is being mounted to /
EDIT2:
I cannot umount it from terminal. It says that the drive is busy

---

### Post by formaldehyde_spoon on 2010-09-23
Post the output from "sudo fdisk -l" and the contents of /etc/fstab

---

### Post by jkurtisr32 on 2010-09-23
> **formaldehyde_spoon said:**
> Post the output from "sudo fdisk -l" and the contents of /etc/fstab

This is the fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5271f09e-2d4e-4a68-a75f-8ef505d872d4 none            swap    sw              0       0
```

And here is the fdisk -l:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cd5a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000281ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux

Disk /dev/sdd: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004c001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        4866    39086113+  83  Linux

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004fd5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       29323   235528192   83  Linux
/dev/sde2           29323       30402     8668161    5  Extended
/dev/sde5           29323       30402     8668160   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000427a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007bdf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30401   244196001   83  Linux

```

Thanks for the help,
Kurt

---

### Post by Elfy on 2010-09-23
sda1 is the drive that you have installed on.

Yes it will be mounted at boot - no you won't be able to unmount it.

---

### Post by jkurtisr32 on 2010-09-23
> **forestpiskie said:**
> sda1 is the drive that you have installed on.

Yes it will be mounted at boot - no you won't be able to unmount it.

I have installed on sde1. When I change around the disks in the machine, different drives are detected as sda. But it doesn't matter which drive is designated as sda, it is always mounted to /

---

### Post by Elfy on 2010-09-23
so when you changed disks about and rebooted it didn't always start?

I'd wonder what is going on if with sda1 mounting to / and it not booting.

I also wonder why fstab does not refer to UUID as that has been default for some time afaik.

---

### Post by jkurtisr32 on 2010-09-23
> **forestpiskie said:**
> so when you changed disks about and rebooted it didn't always start?

I'd wonder what is going on if with sda1 mounting to / and it not booting.

I also wonder why fstab does not refer to UUID as that has been default for some time afaik.

There has never been a booting issue. The mobo will always find the disk with the operating system on it and boot. However, the disk with the operating system is not always designated as sda, and whichever disk is designated as sda is mounted to /

If, for example, I unplugged the disk that is currently assigned to sda and is mounted at /, then booted back up, the system would grab another one of my disks and call it sda and mount it to /.

---

### Post by Elfy on 2010-09-23
Can you go here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) run the tool and post the information here please.

It will give us more information about you are setup.

To answer this though > I switched some drives around. It appears that it is always the drive /sda that is being mounted to / sda1 will always be mounted to / as fstab tells it to do that.

---

### Post by CharlesA on 2010-09-23
It should be listed by the UUID by default.

Which drive is the one with Ubuntu installed on it?

---

### Post by LowSky on 2010-09-23
I can confirm a similar issue.

I had a spare drive hooked up by usb and it was listed as sde1 in gparted, but it somehow was mounted as root..

I only know because I was trying to reformat the drive at the time

---

### Post by drs305 on 2010-09-23
This has been an interesting puzzle. I can explain a bit of it and can offer a partial solution.

**[COLOR="DarkRed"]Caution Added:[/COLOR]** [COLOR="DarkRed"]In search for answers, I often do things to my computer that can, and often do, break it. Although my computer continued to boot after making these changes, I would not advise duplicating them unless you are familiar with how to restore your fstab if the computer doesn't boot.[/COLOR]

I played with my own fstab and found that I could replace the device (partition) listed on the **/** line with any other partition and the system would still boot. 
> 
Boots:  UUID=c5163c70-4f77-4034-a218-5dae03b07eed /               ext4    errors=remount-ro 0       1
Boots, non-system partition:  /dev/sda3 /               ext4    errors=remount-ro 0       1
Boots: <nothing>


Next I completely removed the / reference line and the system still booted normally.

I'd expected it to fail, but apparently Grub2's instructions provide the information Ubuntu uses to boot and the entry in fstab is not necessary. Whether this is a bug or not I don't know, but I can say I've never seen an fstab entry which doesn't contain the / partition designation.

When I added a data partition to the / line in fstab, that partition was mounted on / once booted. Interestingly, my terminal commands (ls /, mount, etc) wouldn't show the data partition but it did show the data partition as mounted on / in gparted. Trying to umount the data partition could not be done, as I got the same 'busy' message as the OP.

So ... it could be a bug or it could be by design and just not documented.

In any case ... the OP can avoid this from happening by using the UUID of his Ubuntu partition in fstab. That will prevent whatever is listed as "sda1" from mounting on / via an fstab instruction, unless of course sda1 is the Ubuntu install partition with the correct UUID.

---

### Post by CharlesA on 2010-09-23
Interesting observation there. I do notice that GRUB2 uses the UUID to point to the root file system if you look at the menu entry.

Very interesting indeed.

---

### Post by QLee on 2010-09-23
[QUOTE=drs305]...
I played with my own fstab and found that I could replace the device (partition) listed on the **/** line with any other partition and the system would still boot. 
...[/QUOTE]
It seems to me that by the time the system gets around to parsing fstab for the static mounts, / has to be already mounted or else the system wouldn't be able to find fstab. I expect it would drop an error if the volume in that line did not exist, but with sda1, well, most systems are going to have an sda1, eh?

---

### Post by drs305 on 2010-09-23
> **QLee said:**
> It seems to me that by the time the system gets around to parsing fstab for the static mounts, / has to be already mounted or else the system wouldn't be able to find fstab. I expect it would drop an error if the volume in that line did not exist, but with sda1, well, most systems are going to have an sda1, eh?

Yes, makes perfect sense. I've just never seen an fstab without a / line and wonder why it's never been brought up. Well, that's a stretch; more accurately, why I've never seen it mentioned.

---

### Post by QLee on 2010-09-23
Err, well, I never mentioned it because I "discovered" it by forgetting to change that line in fstab on a partition that I had mirrored from my main install to act as a test partition. I try to avoid mentioning my mistakes, others keep good track of them for me. ;-) You, on the other hand did it as a test and even remembered to add a caution.

---

### Post by formaldehyde_spoon on 2010-09-23
> **drs305 said:**
> ...
In any case ... the OP can avoid this from happening by using the UUID of his Ubuntu partition in fstab. That will prevent whatever is listed as &quot;sda1&quot; from mounting on / via an fstab instruction, unless of course sda1 is the Ubuntu install partition with the correct UUID.

Yes, to rephrase: OP your fstab is wrong.  Change the / line from sda1 to sde1 (assuming that's the correct partition), or even better use the UUID of sde1.

---

### Post by jkurtisr32 on 2010-09-23
> **CharlesA said:**
> It should be listed by the UUID by default.

Which drive is the one with Ubuntu installed on it?

It was sde1 with Ubuntu on it. I think I really ****ed something up at the time of install.

I understand that your time is valuable, so I went with my own solution. I nuked my Ubuntu drive and reinstalled. Luckily the installation was new, so it was not a real loss.

Well, it works now.

Thanks guys,
Kurt

---

### Post by formaldehyde_spoon on 2010-09-23
> **jkurtisr32 said:**
> It was sde1 with Ubuntu on it. I think I really ****ed something up at the time of install.

I understand that your time is valuable, so I went with my own solution. I nuked my Ubuntu drive and reinstalled. Luckily the installation was new, so it was not a real loss.

Well, it works now.

Thanks guys,
Kurt

Looks like I was a minute or two late...;)
No, you could have fixed this problem with the small fstab edit I mentioned above.

---

### Post by CharlesA on 2010-09-23
> **formaldehyde_spoon said:**
> Looks like I was a minute or two late...;)
No, you could have fixed this problem with the small fstab edit I mentioned above.

Indeed. At least it's working now. ;)

---

