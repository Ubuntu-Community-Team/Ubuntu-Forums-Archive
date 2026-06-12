---
title: "Can access GPT disk in Ubuntu but cannot in Windows and viceversa"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by adepoyu on 2011-05-27
Hi,

I have a GPT disk setup with Gparted, but when trying to access in Windows 7, disk management asks me to initialize the disk and if I do so it become unreadable when I come back to Ubuntu.

To srs5694:
I played a bit with gdisk yesterday and I noticed the expert mode (p) command output is different in Windows from Ubuntu. 
Ubuntu: sector size 512, first sector 34, 2048 sector boundaries.
Windows sector size 1024, first sector 18, 1024 sector boundaries. 

Here are the results from the commands you mentioned:


```
sudo gdisk -l /dev/mapper/pdc_ibegcafg
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/mapper/pdc_ibegcafg: 6837014016 sectors, 3.2 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2AFB847D-F150-4931-85DF-DDB494E10601
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 6837013982
Partitions will be aligned on 2048-sector boundaries
Total free space is 3517 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      6837012479   3.2 TiB     0700 


sudo fdisk -lu /dev/mapper/pdc_ibegcafg
[sudo] password for adepoyu: 

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/pdc_ibegcafg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/pdc_ibegcafg: 3500.6 GB, 3500551176192 bytes
255 heads, 63 sectors/track, 425584 cylinders, total 6837014016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes
Disk identifier: 0xcd68fe9e

                   Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_ibegcafg1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

```

---

### Post by srs5694 on 2011-05-27
> **adepoyu said:**
> Hi,

I have a GPT disk setup with Gparted, but when trying to access in Windows 7, disk management asks me to initialize the disk and if I do so it become unreadable when I come back to Ubuntu.

To srs5694:
I played a bit with gdisk yesterday and I noticed the expert mode (p) command output is different in Windows from Ubuntu. 
Ubuntu: sector size 512, first sector 34, 2048 sector boundaries.
Windows sector size 1024, first sector 18, 1024 sector boundaries.

The sector size difference is almost certainly the problem; if the two OSes are seeing the drive as having different sector sizes, that will throw off each OS's interpretation of the disk when reading partitions the other creates. The only way this would not be a problem is if there's a bug in gdisk's interpretation of sector sizes, but I don't think that's the case. (I just checked in both Windows and Linux using gdisk 0.7.1 and disks with both 512-byte and 2048-byte sectors.)

I note that you're using a /dev/mapper filename to access the disk, which suggests you're using motherboard-based software RAID. It's possible this is doing odd things with the sector size -- perhaps the Linux implementation is buggy and is misinterpreting the sector size. If so, I'm not sure what you'd do to fix the problem, aside from look for an updated kernel that includes a bug fix. Perhaps somebody who knows more about this type of software RAID would have a suggestion for how to fix the problem. If it's practical, abandoning the motherboard-based software RAID would be an option. (You could always use Linux software RAID if you just want the RAID features in Linux.)

---

### Post by adepoyu on 2011-05-27
You are right, I have 4x 1TB disks in Raid0. I have setup two disks from this Raid, 500GB and 3.2TB. I was using different gdisk versions so I have updated the one in Ubuntu to 0.7.1, the same as in Windows, but GPT disk sector sizes and other settings still differ from Windows to Ubuntu. I have tried to force one OS GPT settings in the other by using gdisk option of saving and then loading a config file, but did not work either. As I am going to give up accessing this GPT disk from the two OS, I suppose I should leave the GPT working in Windows and wait for a future fix in Ubuntu, right? So are we assuming Windows is the one with valid GPT settings?
Anyway I am posting two txt files with the different OS disk settings in case you want to check out.

---

### Post by psusi on 2011-05-27
I'd say it is the other way around: the windows fakeraid driver is buggy.  Obviously the 1024 byte sector size is wrong.

I wonder if the windows fakeraid driver is misrepresenting the sector size in an attempt to get around the 4tb limit of the msdos partition table?

---

### Post by srs5694 on 2011-05-27
I don't think the problem is with GPT; gdisk uses standard OS system calls to determine the sector size, so if gdisk is saying that the sector size is different in Windows vs. Linux, the same would be true for other utilities and for the OS itself, and that will spell trouble whether you're using GPT, MBR, or anything else.

As to what's valid, that's arbitrary in some sense. The underlying disks almost certainly use 512-byte sectors, or at least claim they do; however, the motherboard software RAID is presumably "translating" that to 1024-byte sectors (in Windows but not in Linux) to enable MBR to be used with the disks. (MBR tops out at 2 TiB with 512-byte sectors but can handle up to 4 TiB with 1024-byte sectors.)

Why are you using RAID 0, particularly for a cross-OS configuration? RAID 0 presents the illusion of one big disk, but if you're using two OSs, you're presumably carving the big virtual disk up between them. You might do better with two 2-disk arrays, which will keep you under 2 TiB per virtual disk. That might result in a virtual disk with a 512-byte sector value in both OSes. It's also likely to be safer; with RAID 0, if one disk fails completely, you'll lose all your data, and with four disks, such a failure is rather too likely for my own personal comfort, although of course you might have a higher tolerance for such risks.

You might want to consider starting a new thread with a title that better reflects the nature of the problem, such as "'Fake' RAID array sector size varies between Linux and Windows." That might catch the attention of somebody more familiar with motherboard-based software RAID. Be sure to include a link to this thread, along with a summary of what's happening and why you're using RAID 0.

---

### Post by srs5694 on 2011-05-27
> **psusi said:**
> I wonder if the windows fakeraid driver is misrepresenting the sector size in an attempt to get around the 4tb limit of the msdos partition table?

You posted the same speculation just as I began my reply! ;-)

I wouldn't say that changing the logical sector size is necessarily a bug, if it's done from the moment the array is defined. I've heard of such things being done in the past, particularly with hardware RAID controllers. I've never looked into it in any detail, though; perhaps it does violate a standard of some sort.

One other thought occurred to me: It might be worth creating a two-disk array to see if it generates 512-byte sectors. If it does, then growing the array by adding two more disks *should* keep that 512-byte sector size, on the grounds that changing the sector size would break any partitions that were already defined, so any software that made such a change would certainly be considered buggy. OTOH, even if this were successful it would reduce the speed benefits of having four disks in a striped array; you'd have two 2-disk stripe sets vs. one 4-disk stripe set. From a speed perspective, this would be like having two virtual disks, each with 2 physical disks.

---

### Post by psusi on 2011-05-27
Yes, it could fall under undocumented feature rather than bug.  Fakeraids also generally don't support reshaping the array.

---

### Post by adepoyu on 2011-05-28
Ok, so I followed the wise advice and created two raid 0 disks, 2TB each.
Now when I launch gdisk in Windows 7, sector size and other settings are correct!! :)....... but ......
I went back to Ubuntu and gparted does not see the second disk at all.
I launched Parted Magic 6.1 live CD and I do see this second disk properly recognized, so I suppose I am missing something stupid.
I am getting closer to finally get this to work. I can smell it in the air!!!!
Many thanks guys!

---

### Post by adepoyu on 2011-06-01
Hi,

It seems the only thing I was smelling was crap :b

I reinstalled everything after wiping the four hds. The setup is the same: two bios raid 0 disks, 2TB each. They are both correctly detected in windows, any other linux distros, and boot utilities cds as parted magic or acronis. But in Ubuntu only one of them is detected, the one in which Ubuntu is installed, of course.

Do you have any ideas what the problem could be?

Thanks

---

### Post by psusi on 2011-06-01
Is the working one using an MSDOS partition table, and the other one using GPT?  dmraid does not understand GPT.

---

### Post by adepoyu on 2011-06-01
No, both are mbr basic. I think parted Magic cd uses dmraid also, and you can see this disk from gparted in the Parted Magic CD.
Some days ago,  I had one of the disks as gpt and although I could not access it from both Windows and Ubuntu at the same time because each OS needed to initialize it, Ubuntu did detect the disk even it was gpt.
It is really strange. I can only think the problem may be of having intalled Ubuntu when only one disk was created. After I installed Ubuntu and Windows, I created this second raid 0 disk from bios, and it is detected by everyone except by Ubuntu.

---

### Post by psusi on 2011-06-01
Hrm.. can you post the results of the following commands from Ubuntu:

sudo dmraid -s
sudo dmraid -n
sudo dmraid -ay
ls /dev/mapper

---

### Post by adepoyu on 2011-06-02
Hi psusi,

Im away right now and will not come back home until sunday. Thanks for your support, and I will post the results as soon as I can.

---

### Post by adepoyu on 2011-06-04
> **psusi said:**
> Hrm.. can you post the results of the following commands from Ubuntu:

sudo dmraid -s
sudo dmraid -n
sudo dmraid -ay
ls /dev/mapper

Hi psusi,

I am back with the results in the attached file.

Thanks

---

### Post by psusi on 2011-06-04
So both arrays are now under 2TB in size?  I think you are suffering from this bug:

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/770600](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/770600)

If you could test the build in my PPA that should fix it.  It should get uploaded to the main archive "soon".

---

### Post by adepoyu on 2011-06-05
Hi Phillip,

I did as the other guys. Installed your dmraid build, rebooted, and then upgraded libdmraid and a few more packages. Finally it is working fine.

Thanks A LOT! :)

---

