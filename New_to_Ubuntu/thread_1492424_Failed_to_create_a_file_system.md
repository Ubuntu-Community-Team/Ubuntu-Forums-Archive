---
title: "Failed to create a file system"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by rob &lt; on 2010-05-24
I keep getting an error message when attempting to format my hdd completely and install Ubuntu (also tried LunixMint but the exact same error came up, as that's what I have on my CD-RW at the moment). 

"[B]Failed to create a file system

The ext4 file system creation in partition #1 of Serial ATA RAID isw_dgjbgabdh_Volume0 (mirror) failed.[/B]"

I suppose I could try to do it manually but have no clue how. Any help is appreciated. Thanks, take care.

---

### Post by sandyd on 2010-05-24
> **rob < said:**
> I keep getting an error message when attempting to format my hdd completely and install Ubuntu (also tried LunixMint but the exact same error came up, as that's what I have on my CD-RW at the moment). 

"[B]Failed to create a file system

The ext4 file system creation in partition #1 of Serial ATA RAID isw_dgjbgabdh_Volume0 (mirror) failed.[/B]"

I suppose I could try to do it manually but have no clue how. Any help is appreciated. Thanks, take care.
thats because its an RAID array,
Open Gparted (System -> Administration -> Gparted)

select the disk
and click on "devices"

choose "create partition table"

---

### Post by rob &lt; on 2010-05-24
Thanks, I'll see if that works and update here. 

I also read that I could just install 9.10 and upgrade, since it agrees more with RAID. I dunno if that's right or wrong though, just what I saw someone say.

---

### Post by rob &lt; on 2010-05-24
OK so I did that, and now Gparted reads..

Partition - unallocated
File system - unallocated
Size - 465.76 GiB (probably irrelevant) 

(I went with an MS-DOS partition table type as it was the default. Other options were aix, amiga, bsd, dvh, gpt, mac, pc98, sun, and loop)

So I went to install again, and at the screen where I was intending to choose "erase and use the entire disk" and format the whole thing, it asks me to Prepare Partitions and basically do a few things I don't know how to do. 

Under device it says...

/dev/mapper/isw_dgjbgabdh_Volume0
 /dev/mapper/isw_dgjbgabdh_Volume01
 /dev/mapper/isw_dgjbgabdh_Volume05 swap

my options are "New Partition Table" and "Revert" with everything else grayed out.

If I go forward with this it says "No root file system defined, please correct this from the partitioning menu".

---

### Post by rob &lt; on 2010-05-24
Bumpers

---

### Post by lkraemer on 2010-05-24
Either boot the Gparted LiveCD or the Ubuntu LiveCD.
When Gparted opens you should see no partitions that were created.
If there are partitions created and you want to remove them
just make double sure it's the one you are wanting to delete and remove it.

Left Click on the unallocated area in the lower section of the graphic
and tell it to create new.  This will be your first partition.  You
are going to have to decide what you want as far as partitions go.
(I typically make / a 20 Gig Partition and the second partition /home
and it has all but the last partition which is linux-swap, and this
one is sized to be 2 times your RAM.)  But you can just use one partition
and then also use the linux-swap.

After you apply the changes, go back and format the partiton.  Same for
the linux-swap.  linux-swap will always be the last (right most partition on the graphic).
I format ext3 but once again it's your choice of ext3 or ext4 for the primary
ones and linux-swap for the swap partition.

You can only have a MAXIMUM of 4 Primary Partitons on any physical hard drive.
But you can make an Extended (Logical) partition and that Logical
one can contain several partitions.

When you are finished go ahead with the install, and just go to the manual selection
and assign a mount point of / for the first partiton,
and /home for the second partition and continue with the install.
It's all menu/graphical and you will find your way through the process.

When you are done you will have something that looks like the attached png.

lk

---

