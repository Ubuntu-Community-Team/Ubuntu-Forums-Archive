---
title: "Installing on multiple hard drives"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by japhyr on 2009-04-18
Hello everyone,

I posted this earlier, but it was at the end of a two-page thread I started back in January.  I am reposting just the question that is still unanswered.


I am trying to install HH 8.04 on an older computer, and I am not sure which option to choose on the screen "Prepare disk space".

There are 3 hard drives in the computer - a 20G, 80G, and 80G.

I tried the first option - "Guided - resize SCSI2 (0,0,0), partition #1 (sdc) and use freed space". Then it said "partition too small", and I realized that option is used to keep Windows on one part of the disk. I want to erase Windows (Windows 98!) on this machine and do a full Ubuntu install.

The second option is "Guided - use entire disk." But there are three radio buttons, and I'm not sure which to choose. There is "SCSI1 (0,0,0)(sda) - 20.0 GB ATA ST320414A", "SCSI1 (0,1,0)(sdb) - 82.0 GB ATA Maxtor 6YO80L0", "SCSI2 (0,0,0)(sdc) - 82.0 GB ATA Maxtor 6YO80L0".

The third option is "Guided - use the largest contiguous free space".

The fourth option is "Manual".


Which of these options should I select, and if it is "Guided - use entire disk", which radio button should I choose?

Thank you.

---

### Post by Svensk023 on 2009-04-18
Well are you planning on using all three HDD's for solely Ubuntu?

Because if so, you should use the "Manual" option. 

And if you are planning on using this computer for only Ubuntu, I (or whoever else gets here before me) can walk you through the formating/partitioning process.

---

### Post by japhyr on 2009-04-18
Yes, this will be used only for ubuntu.

I took a look at the manual screen, but I did not know which options to choose.

---

### Post by Svensk023 on 2009-04-18
Ok well lets get you set-up here.

First what you need to do is delete all the partition tables for each HDD. This will clear them up into free space.

Lets start with the SCSI1 (0,0,0)(sda) - 20.0 GB ATA ST320414A drive first.

Since this is the smallest, we will use it for swap and extra space.

so just create a 2GB swap partition, then with the rest of the space make it a primary ext3 partition.

With the "SCSI1 (0,1,0)(sdb) - 82.0 GB ATA Maxtor 6YO80L0"

Make the entire drive a primary ext3 partition and set it's mount point to "/"
this means that the entire drive is devoted to your root filesystem only.

for the last drive make the entire thing a primary ext3 but set this mountpoint to "/home"
This whole drive will be devoted to all your personal settings, videos, music ect. 
The plus side to making a separate partition that is mounted to /home is that you can keep all your personal settings and files safe during a re-installation. 

I hope I was semi-clear and didn't just look like a babbling fool

---

### Post by .nedberg on 2009-04-18
Just to make sure you know:
What Svensk023 is telling you will remove any file on that computer. Make sure you have backups if there is something you want to keep!

There isn't any other way to do it, so I am not saying anything wrong about Svensk023's way of doing it! Just wanted to make sure you knew!

---

### Post by sadaruwan12 on 2009-04-18
> **Svensk023 said:**
> 

so just create a 2GB swap partition,

Yes Svensk023 is right but it's better not to give too much swap file space the best way is to multiply your RAM capacity by 2 and make the a SWAP partition thats equal to that size for example if you have 512mb of ram then multiply it by 2 (512 x 2) will be equal to 1024 so make your SWAP partition a 1024Gb's and continue the rest of the partitioning as Sevensk023 says and if you can make a 5Gb /tmp mount point or a partition as well so that will hold all your temporary data.

---

### Post by Sir Jasper on 2009-04-18
Hi,

Do you have some idea how much space you might now need for your programs and data and have you considered regular cloning of your complete system to a spare drive in case of irrecoverable error or failure of a principal hard drive?

What you decide now could be alterered later with the judicious use of GParted to resize any partitions. I have two hard drives and I moved from dual boot with the aid of GParted, and now have a triple boot set up with Xubuntu, Ubuntu and W98SE. I also have an External Drive with 8 partitions which I use for cloning and backups.

My regards

---

### Post by heyyou_21 on 2009-04-18
this is perfect, I've been looking same info for a little while now.
When Ubuntu 9.04 comes out I'm doing a reinstall over 3 hard drives (1-160gb and 2-500gb drives).

---

### Post by Marko723 on 2009-04-18
If I wanted to make a small file server using 2 additional drives, where's the best point to mount these drives?

Thanks

Mark

---

### Post by japhyr on 2009-04-19
> so just create a 2GB swap partition, then with the rest of the space make it a primary ext3 partition.


I have made the swap area on the 20G hard drive.  When I try to partition the rest of the drive, I am not sure what to choose.  The choices are:
[LIST]
[*]Ext3 journaling file system
[*]Ext2 file system
[*]ReiserFS journaling file system
[*]JFS journaling file system
[*]XFS journaling file system
[*]FAT16 filing system
[*]FAT32 filing system
[*]swap area
[*]do not partition
[/LIST]

Is the first one what is meant by a "primary ext3 partition"?

---

### Post by sadaruwan12 on 2009-04-19
Here is my Ubuntu partitioning table so you can get some idea out of it. And for all your partitions select the first choice as the file system 'cos it's very stable.

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc263c263

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          30      240943+  83  Linux
/dev/hda2              31         777     6000277+  82  Linux swap / Solaris
/dev/hda3             778        4865    32836860    5  Extended
/dev/hda5             778        1750     7815591   83  Linux
/dev/hda6            1751        4303    20506941   83  Linux
/dev/hda7            4304        4865     4514233+  83  Linux

---

### Post by longtom on 2009-04-19
> **japhyr said:**
> I have made the swap area on the 20G hard drive.  When I try to partition the rest of the drive, I am not sure what to choose.  The choices are:
[LIST]
[*]Ext3 journaling file system
[*]Ext2 file system
[*]ReiserFS journaling file system
[*]JFS journaling file system
[*]XFS journaling file system
[*]FAT16 filing system
[*]FAT32 filing system
[*]swap area
[*]do not partition
[/LIST]

Is the first one what is meant by a "primary ext3 partition"?

[sorry for chipping in...] it is the first one.  Above in the same window is where you set this parttiton as primary (if it is not primary by default - can't remember).

---

### Post by japhyr on 2009-04-19
What should the mount point be for the swap area, and for the ext3 partition on the rest of that 20G drive?

---

### Post by RuleMaker on 2009-04-19
Swap space has no mount point, just leave it like that and your system will automatically detect it as a swap.
Set the mount point of your ext3 partition to "/" and of your another ext3 to "/home".

---

### Post by japhyr on 2009-04-19
I tried that, and it said "Two file systems are assigned the same mount point...Please correct this by changing mount points."

???

---

### Post by HeirPixel on 2009-04-19
> **sadaruwan12 said:**
> and if you can make a 5Gb /tmp mount point or a partition as well so that will hold all your temporary data.
Good point. A more technical question pops up in my mind here though: Would the **/tmp** partition be more efficient on the same drive as the swap space, or on one of the other drives?

My initial thought was toward simplicity: 
[LIST]
[*]1 drive for **/**
[*]1 drive for **/home**
[*]1 drive for "other" (including swap space & **/tmp**)
[/LIST]

But then I thought that it may be more efficient (especially on an older system) to have **/tmp** on a drive apart from the swap space to minimise constant, concurrent writes to the same disc. Any thoughts on this?

---

### Post by sadaruwan12 on 2009-04-19
> **japhyr said:**
> What should the mount point be for the swap area, and for the ext3 partition on the rest of that 20G drive?

To create an SWAP area just select the file system as SWAP and leave it like that 'cos for SWAP theres no mounting point 'cos it's been used by the system for virtual memory and you can't use that.

Here read this : [http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10")

---

### Post by japhyr on 2009-04-19
The swap area is fine, but that is 2G out of a 20G drive.  I am trying to make the other 18G of this drive an ext3 partition, but this partition needs a mount point.  I can't use "/", because one of the other drives already uses this mount point.  What mount point should I use for the 18G of the 20G drive?

That link only recommends using Guided-Use Entire Disk.  I am pretty sure that option only works for installing over one disk.

---

### Post by sschnee on 2009-04-19
> **japhyr said:**
> The swap area is fine, but that is 2G out of a 20G drive.  I am trying to make the other 18G of this drive an ext3 partition, but this partition needs a mount point.  I can't use "/", because one of the other drives already uses this mount point.  What mount point should I use for the 18G of the 20G drive?

That link only recommends using Guided-Use Entire Disk.  I am pretty sure that option only works for installing over one disk.

Using the partition scheme mentioned earlier, the 18 GB partition should not be mounted to "/", as you have figured out.  You can mount it however you like, but I would recommend mounting it as "/media/18GB" since it will be a 18 GB partition.  You could call it whatever you want, but mounting it as "/media/yournamehere" makes sense to me.

I'm pretty new to Linux myself, so if someone wants to prove me wrong, I won't be offended.

---

### Post by japhyr on 2009-04-19
I mounted the rest of the 20G drive to "/media/18GB".  The installer went to work, and I saw it progress 30%, 50%, but when I came back some time later I found this message:

```
Executing 'grub-install(hd0)' failed.
This is a fatal error.
```

After reading a little about this error code I found a number of suggestions but I have no idea which ones to try.  One suggestion was to set the drive path to (hd0,0).  I don't know how to do this, or why it would work.  Another is to set the swap size to less than 1G - some people report that installation did not work until they set a swap size of 999MB.  The computer has 1G of RAM.

I defined all the partitions as described earlier, but I didn't specify anything about formatting them.  Is that an explicit or necessary step, or does the installer take care of any necessary formatting after I have specified the partition sizes and formats?

---

### Post by japhyr on 2009-04-19
In the interest of time, I was a bad scientist and changed several things at once, so I'm not sure what got it to work.

I changed the swap area size to 999MB, and mounted the rest of the 20G disk to "/".  I mounted the entire second disk at "/home", and did not use the third disk.

The installation worked.

Thank you everyone for the help.  I am planning to use this in a classroom, and if it is being used meaningfully I will try to install ubuntu on some more old computers that are not currently in use.  I have learned a lot from this installation, and next time I choose an old computer to work with I will know what to look for in the hardware (ie choose a computer with just one or two hard drives if possible).

---

