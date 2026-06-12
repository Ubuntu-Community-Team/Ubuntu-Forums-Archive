---
title: "Error: no such partition. grub rescue &gt;"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by 2by on 2011-07-22
I have seen other threads on this, but nothing worked for me.

Here is my situation. I am very new to Ubuntu. I have a 27" iMac. It comes with OS X, from there i used Boot Camp to install Windows 7. Afterwards i installed Ubuntu, and the Grub loader took over. It caused some problems but i managed to install rEFIt, and this worked.

I had some free disk space, and wanted to make my Windows 7 partition bigger, so i used the Windows disk partition tool, to make the partition bigger. It worked fine, until I started my Mac next day. I now get this error everytime i start my Mac:
```
error: no such partition.
grub rescue>
```

I am running latest version of Ubuntu.

If you need any other information to help me, please let me know.

Thank you!

Regards

Toby

---

### Post by 2by on 2011-07-23
Anyone? :-)

---

### Post by drs305 on 2011-07-23
Welcome to Ubuntu.

Running the boot info script will show us the status of your boot files. Download the script from the following site, run it and post the contents of the RESULTS.txt file it generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by 2by on 2011-07-23
Hello

Thank you, but how should i run it, i cant even start the machine? :-)

---

### Post by sadaruwan12 on 2011-07-23
If you have your installation CD with you which you used to install ubuntu pop that in and boot in to a Live CD session from there run the script.

---

### Post by 2by on 2011-07-26
Ah okay, of course :)
Sorry for my late answer. Here is the result of the boot script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1282707512 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 5 for (,gpt5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,407,862,783 1,407,862,783  42 SFS
/dev/sda2    *  1,407,862,784 1,608,794,111   200,931,328  42 SFS
/dev/sda3       1,608,794,112 1,953,523,119   344,729,008  42 SFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640 1,407,600,639 1,407,191,000 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda3   1,407,862,784 1,608,794,111   200,931,328 Data partition (Windows/Linux)
/dev/sda4   1,608,794,112 1,620,512,767    11,718,656 Swap partition (Linux)
/dev/sda5   1,620,512,768 1,718,169,599    97,656,832 Data partition (Windows/Linux)
/dev/sda6   1,718,169,600 1,815,826,431    97,656,832 Data partition (Windows/Linux)
/dev/sda17 4,594,164,201,127,149,5681,153,414,085,816,090,624-3,440,750,115,311,058,943 -
/dev/sda18              0             0             1 -

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        df943ada-fba8-3a25-8096-ea0d21401a7a   hfsplus    Macintosh HD
/dev/sda4        FCAED714AED6C674                       ntfs       BOOTCAMP
/dev/sda5        cb54672f-59ca-42f6-a0a9-03da42ccb0e3   swap       
/dev/sda6        2105448b-08bb-46bf-afad-10ee584f8010   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
505249564845414400002f8e0002000c
Unknown GPT Partiton Type
64302d613562652d3030613063393164

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

```

---

### Post by srs5694 on 2011-07-26
You've hosed your disk pretty badly.

Apple, in its infinite wisdom, decided to use a dangerous hack known as a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) as part of its method of getting Windows to boot on its Intel-based Macs. A Mac that boots just OS X uses a GUID Partition Table (GPT), which is the next-generation way of defining partitions. A hybrid MBR is a way to duplicate up to three GPT partitions in a Master Boot Record (MBR) data structure, which is what Windows expects to see. So, in sum, GPT is the "master" definition of partitions, whereas the hybrid MBR that Windows uses is just a "backup" of the partitions. What's more, because the hybrid MBR can describe at most three partitions, chances are it didn't include all the partitions used in your three-OS configuration.

What you've done is to alter this hybrid MBR backup without modifying the original GPT data. Worse, Windows has decided to convert the hybrid MBR partitions into its own proprietary format (Logical Disk Manager/LDM, aka "dynamic disks"), so you've now got *three* partition table systems in use on the disk.

Your best and simplest option is to restore everything from a backup. I hope you've got one. If you don't, it's likely you'll be able to recover some of your data, but I can't make any promises, and in a worst-case scenario, you might be picking the disk's contents apart file by file. If you're luckier you'll be able to restore one or two OSes more-or-less intact.

Assuming you have no backups, my recommendation for how to begin is as follows:


[list=1]
[*]Using another computer, download and burn [Parted Magic](http://partedmagic.com) or some other Linux emergency disc system. (The Ubuntu installer in its "live CD" mode will work, but you'll need to install some extra software; see below....)
[*]Boot the emergency disc.
[*]If possible, do a low-level backup of the disk, as in "sudo dd if=/dev/sda of=/dev/sdb" to copy everything from /dev/sda to /dev/sdb. Note that this will *wipe out* everything on /dev/sdb. (You can back up to a file instead, as in "sudo dd if=/dev/sda of=/some/dir/backup.img".) This assumes that /dev/sda is the original disk. If there's any doubt in your mind about this, verify it, since if you back up the wrong way, dd will wipe out all your data, making everything complete unrecoverable.
[*]If you're using the Ubuntu installer, open a terminal window and type "sudo apt-get install gdisk" to install the gdisk package.
[*]Type "sudo gdisk /dev/sda". (You can omit "sudo" with most emergency disc systems, but not with the Ubuntu installer.)
[*]The gdisk program will probably tell you that it's found valid MBR data and damaged GPT data and ask you which to use. Select GPT.
[*]Type "p" to view the partition table.
[*]Cut-and-paste the partition table data into a text file and store that file on a USB flash drive or the like.
[*]Type "q" to exit from gdisk *without saving your changes*.
[*]In a terminal, type "dd if=/dev/sda of=damaged-parts.gpt bs=512 count=34". Be very careful to type this command correctly. It's intended to back up your current GPT data, but if you get the if= and of= options wrong, you could end up making things even worse.
[*]Copy the damaged-parts.gpt file to the same medium on which you stored the cut-and-pasted gdisk output.
[*]Post the gdisk output here. Stop here if you want my advice before proceeding further.
[*]If you want to proceed with the risky part, launch gdisk again and tell it to use the GPT data.
[*]Type "w" in gdisk to save the GPT data, wiping out the MBR data.
[*]Launch GParted and use it to check the status of the partitions. If it can correctly identify partitions' types, you can try mounting them and see if they contain the files they should. If a partition is mountable and contains sensible files, it may be bootable. OS X might be immediately bootable, but you'll probably have to re-install a boot loader for Linux. I'll hold off on providing more advice on that score until I know more about what's on the disk. Windows will not be bootable at this point, and might never be, at least not before re-installing it.
[/list]


An alternative way to proceed would be to use [EaseUS Partition Master](http://www.partition-tool.com/personal.htm) to try to convert the "dynamic disk" data back to conventional MBR form and try to reconcile that layout with the GPT layout. This might be more likely to recover Windows to a bootable form, but I'm not sure how EaseUS will react to your current setup. It might further damage the GPT data, making it less likely that you'll recover OS X and/or Linux.

Whatever you do, do it *very cautiously*. It's easy to do further damage to your system the way it is now, so if you run into something unexpected, play it safe and  *do not* allow any program to write data to the disk without further advice. This means that filesystem repair operations should be done only if the utility can positively identify the filesystem in the first place -- and even that could overwrite data from a newly-overlapping filesystem.

You might want to consider complaining to Apple. They caused this problem by using a flaky and standards-violating hack in the first place.

---

### Post by 2by on 2011-07-26
Thank you very much for your current solution. Right now I'm wondering if it's worth all the work. I think i did a backup not long ago of my most important files in Windows, so I think i just re-install the whole system, OS X, Win7 and Ubuntu. I hate Apple right now... 

If i choose to install it all over, do you have any good advice for installing the different OS?  I think i will only install OS X and Win7 on the Mac, and then install Ubuntu on my Windows laptop instead. Again, any good advice to stay out of trouble this time? Im thinking, which partition program to use- in which OS and how do i make a backup of the boot system, and all the OS in the same time (is it possible?).

Thank you all for your time.

---

### Post by srs5694 on 2011-07-26
The single best piece of advice I can give is to *not* attempt a dual boot of Windows and OS X on a Mac, since AFAIK the only way to achieve this is to use a hybrid MBR, which is what got you into this trouble in the first place. Instead, try running Windows in a virtual environment, such as VirtualBox.

If that's not a practical solution for you, then use only partitioning tools that are capable of safely handling a hybrid MBR. Apple's Disk Utility can do so, although it doesn't always tell you what it's doing. *Never* use Windows' own partitioning tools when you've installed using a hybrid MBR, since they "see" only the MBR side, which is a recipe for disaster.

FWIW, Linux can handle a GPT-only configuration, so it's a much safer dual-boot partner on a Mac than is Windows; however, most of the tutorials for doing it set up Linux with a hybrid MBR as if it were Windows.

---

### Post by 2by on 2011-07-26
Yea okay - thank you :-)

What about backup?

Linux and Windows on a windows laptop should be no problem, right?

---

### Post by srs5694 on 2011-07-26
Ordinarily, Linux and Windows on a standard PC will use MBR with no GPT; however, some recent PCs use UEFI firmware, and Windows will use GPT in that situation. Ideally, this will result in a pure-GPT configuration, since Linux is fine with GPT. There are a lot of teething problems with UEFI on PCs, though, and people have tried all sorts of weird things, including hybrid MBRs, to get over those problems. This will all get much simpler in another year or two, but right now we're suffering through a chaotic transition period, I'm afraid.

---

### Post by cbradyl90 on 2011-10-21
Im having the same problem BUT I have a netbook and its the only means of a computer I have other that my andriod phone. Can any one email me a boot image of ubuntu, if I had a boot image I can use my andriod to fix my netbook. Any advice?

---

