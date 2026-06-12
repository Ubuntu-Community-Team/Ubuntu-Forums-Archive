---
title: "Ubuntu doesn't shows all NTFS Partitions"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by pappusarkar on 2011-09-05
I have bought two 500 GB hard disk drives recently and connected them via SATA port.My 1st HDD has 5 NTFS partition and my second one has 2 ext4 and 1 NTFS partition.When I boot into Windows everything runs fine with no problems but when I boot into Ubuntu 11.04,One 123 GB NTFS partition doesn't show up.I checked into the disk utility everything is fine except my 1st hard disk is showing 4 partitions and 184 TB of free space.

Is there any limitations in ubuntu about NTFS partitions? If not then why my 123 GB NTFS partitions is showing as free space. :confused:

---

### Post by Mark Phelps on 2011-09-05
Could simply be a problem with Disk Utility ...

To get a couple of other readings, you could try the following:
1) Open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  This will list out the partitions on all your drives. See if all the partitions show up in this list.
2) Run Gnome Partition Editor.  This was the partitioning tool generally used before Disk Utility came along.  Again, with this one, see if all the partitions are shown.

---

### Post by mikechant on 2011-09-06
NTFS partitions may not show up correctly if they were not unmounted cleanly by Windows. You might need to access the partition in Windows, and possibly do a Windows filesystem check on it.

---

### Post by snip3r8 on 2011-09-06
Have you tried different sata ports or cable?

> 184 TB of free space. 
Wow,i bet you wish that were true

---

### Post by nipunshakya on 2011-09-06
My advice, boot windows and defragment your hdd with the NTFS partition.......and then check for errors...for doing so, goto your HDD, right click>properties>tools>Check now>then select both the options and start......i assume you have windows 7 so i guided through this....even u have other version of windows, the process might be similar....after checking disk is complete, reboot to your ubuntu and then see what happens.....

Its just a simple trick but i guess it might help you out too...best of luck

Regards, NeptuneTech

---

### Post by YesWeCan on 2011-09-06
There is something wrong with that Disk Utility screenshot. What does this show:
sudo parted /dev/sda print

---

### Post by pappusarkar on 2011-09-07
> **Mark Phelps said:**
> Could simply be a problem with Disk Utility ...

To get a couple of other readings, you could try the following:
1) Open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  This will list out the partitions on all your drives. See if all the partitions show up in this list.
2) Run Gnome Partition Editor.  This was the partitioning tool generally used before Disk Utility came along.  Again, with this one, see if all the partitions are shown.

Looks like its showing only 1 partition where  I installed Windows.Gparted also not working correctly.

---

### Post by pappusarkar on 2011-09-07
> **YesWeCan said:**
> There is something wrong with that Disk Utility screenshot. What does this show:
sudo parted /dev/sda print

I'm too confused to understand this.

---

### Post by pappusarkar on 2011-09-07
I checked for HDD errors in windows 7.It showed no problems.
lets see what happens after defragment.:-k

---

### Post by YesWeCan on 2011-09-07
[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)

---

### Post by Mark Phelps on 2011-09-07
Since fdisk and Gparted both apparently show both the drives and all the partitions, other than the faulty info from Disk Utility, is there any other problem?

---

### Post by nipunshakya on 2011-09-07
^^^^ i was just curious to know..what might be the problem with Disk Utility..? im sorry if its totally unrelated to the topic but was curious to know....Why did gparted and fdisk show the partitions but not the DiskUtility?

Regards,WinuxUser

---

### Post by YesWeCan on 2011-09-07
I think the problem is that the disk is using Windows "type 42 SFS" - Secure File System? I don't think linux tools support this.

I thought it might be dynamic disks, but I'm not familiar with this stuff.

So I suppose the drive will either have to be used only with Windows or will have to be reformatted and Windows reinstalled.

Forum member **oldfred** may know about this.

---

### Post by oldfred on 2011-09-07
SFS is what fdisk shows for Dynamic partitions. The tools to convert back work when it has just been created and there is a one to one correspondence from logical to physical partitions. I do not think I have seen a user with multiple logical partitions in just two physical. 

My notes on Dynamic, even some windows repair tools have had issues working with Dynamic partitions. MS Windows offical policy is to totally backup delete everything and create new basic partitions. Or it is a one way conversion.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by YesWeCan on 2011-09-07
Thanks oldfred.

Some surfing reveals that partition type 42 is used for several different things:
> 42	Secure File System; Windows 2000 (NT 5): Dynamic extended; PTS-DOS 6.70 & BootWizard: Alternative Linux swap & DR-DOS
from: [http://myfreebsd.homeunix.net/hints_n_kinks/partition-types.html](http://myfreebsd.homeunix.net/hints_n_kinks/partition-types.html)

It may be that fdisk is mapping 42 to SFS without doing any further checks. If so, in this case it is not reporting the right System name for type 42.

---

### Post by srs5694 on 2011-09-07
Linux provides some limited Logical Disk Manager (LDM) support, but I don't know all that much about it. AFAIK, installing Linux to an LDM disk is not practical, but you should be able to use the LDM volumes much as you would use data partitions.

I seem to recall that LDM volumes often show up as if they were Linux Logical Volume Manager (LVM) volumes (they're conceptually very similar), in /dev/mapper. Thus, you might try checking there. There's also a kernel compilation option, and the documentation suggests that LDM partitions handled by this driver show up as normal partitions (/dev/sda1, /dev/sda2, etc.). If this module is compiled and working correctly, it's conceivable that you'll have access to the Windows LDM volumes using these device nodes even though fdisk, parted, and other tools don't show the LDM volumes.

So, what to do? I recommend you run the following commands:

```

ls /dev/sda*
ls /dev/mapper/*

```

If the first command returns /dev/sda, /dev/sda1, and /dev/sda2, then the kernel is probably assigning device nodes for the MBR partitions in the usual MBR way; but if it returns /dev/sda and /dev/sda1 through /dev/sda5, then the kernel is probably showing you the LDM volumes, and you should be able to access them normally.

If the second command shows /dev/mapper/control and five more files, then those five additional files should give you access to the LDM volumes.

If you can't find the LDM volumes in either of these ways, please try posting the output of the "dmesg" command -- that is, type "dmesg > dmesg.txt" and then post the dmesg.txt file, either as an attachment or by cutting-and-pasting it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This last is important; the dmesg output will be ridiculously long if you don't include the code tags!

If you can find device nodes in /dev for your LDM volumes but if you can't access the volumes via your normal desktop tools, you should be able to do so by using the text-mode "mount" command or by creating /etc/fstab entries. Post back with details of what you've found, as well as information on which LDM volumes you want to access, for more advice.

---

