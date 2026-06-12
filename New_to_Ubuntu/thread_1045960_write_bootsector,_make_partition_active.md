---
title: "write bootsector, make partition active"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by archyslave on 2009-01-21
Playing around with Ubuntu, I managed to mess up the partitions for my MSI Wind such that I cannot boot into Windows, or even run the recovery partition utility.  I asked about my problem on a MSI-specific forum, and this was the reply.


"The recovery partition is crap.

It only operates if the second partition on the drive is NTFS and has a valid xp boot sector.

Otherwise, it will just reboot.

You will need a linux live cd most likely to fix this.

Create a primary NTFS partition as second partition. Set it active. Use whatever means you can to write a bootsector to it. Then the recovery partition will suceed in restoring your C drive partition. After doing this, you want to get the recovery disc made by BUrnRecovery onto a usb drive. At this point, you can restore not only your wind if you screw it up again, but any other of the same model."


How do I do this is in Ubuntu?  The second partition is NTFS, but I'm not sure how I would write a bootsector to the NTFS partition, or how that would interact with GRUB.  I'm also not sure what it means to set a partition "active."  

I'm not experienced with Linux beyond the gui and basic command line operations, so messing with boot sectors is unfortunately out of my reach at the moment.  Any help would be appreciated.

---

### Post by caljohnsmith on 2009-01-21
If your second partition is NTFS, it should all ready have a valid NTFS boot sector assuming it hasn't been damaged by something else. To set the second partition as "active" just means setting the boot flag on it. In Ubuntu, you can that from a terminal (Applications > Accessories > Terminal) with:
```
sudo sfdisk -A2 /dev/sda
```
Also, please post the output of:
```
sudo fdisk -lu
```
So I can see what your drive/partitions look like. We can work from there if you want.

---

### Post by archyslave on 2009-01-21
fdisk returns before changing active drive

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8193149     4096543+  12  Compaq diagnostics
/dev/sda2         8193150    90124649    40965750    5  Extended
/dev/sda3   *    90124650   234436544    72155947+   7  HPFS/NTFS
/dev/sda5         8193213    12289724     2048256   82  Linux swap / Solaris
/dev/sda6        12289788    90124649    38917431   83  Linux


```

and after ```
sudo sfdisk -A2 /dev/sda

```
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8193149     4096543+  12  Compaq diagnostics
/dev/sda2    *    8193150    90124649    40965750    5  Extended
/dev/sda3        90124650   234436544    72155947+   7  HPFS/NTFS
/dev/sda5         8193213    12289724     2048256   82  Linux swap / Solaris
/dev/sda6        12289788    90124649    38917431   83  Linux


```

So it looks like NTFS isn't the second partition, but the the third.  So if I reformat /dev/sda2 to NTFS, then the restore utility should work?

Also, setting /dev/sda2 active didn't affect GRUB, so I can still boot into Ubuntu.

---

### Post by caljohnsmith on 2009-01-21
OK, so your NTFS partition is actually sda3 and not sda2. You could reorder the partition names so that the NTFS partition becomes sda2 and the extended partition becomes sda3 (without changing the physical layout of your partitions), and then you would have a better chance of getting your Windows recovery partition to work I think. Even that might not work since your NTFS partition is physically at the end of the drive and does not come right after the recovery partition, but I don't know if that matters to the recovery partition or not. Either way, I would strongly suggest backing up anything important in Ubuntu, because it might be that booting the recovery partition will actually overwrite the whole drive in order to restore Windows. So if you want to swap the sda2 and sda3 partition names so that there is a better chance of successfully using your Windows recovery partition, how about posting:
```
sudo sfdisk -d /dev/sda
```
And we can work from there if you want.

---

### Post by archyslave on 2009-01-21
sudo sfdisk -d /dev/sda returns

```
/dev/sda1 : start=       63, size=  8193087, Id=12
/dev/sda2 : start=  8193150, size= 81931500, Id= 5, bootable
/dev/sda3 : start= 90124650, size=144311895, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=  8193213, size=  4096512, Id=82
/dev/sda6 : start= 12289788, size= 77834862, Id=83
```

working on changing the names now, will update after.

---

### Post by caljohnsmith on 2009-01-21
Have you made a backup of all your important files in Ubuntu? If so, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
Please post the output so I can check that everything went OK. Also, the above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so that if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. Next reboot, and once you get back into Ubuntu, please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there.

---

### Post by archyslave on 2009-01-21
After backing up all of my files and such I used the "nuclear option" and just started from scratch, preserving the restore partition,  but deleting both the Ubuntu and Windows partitions.  I set /dev/sda2 to NTFS, and this time the recovery utility ran and completed successfully.  I installed Ubuntu again on the end of the disk. 

The problem now is that I still can't boot into Windows.  GRUB allows me to boot into Ubuntu, but the Windows GRUB entry runs the recovery utility again.  Looking at /dev/sda2 in Ubuntu shows me what looks like a full Windows install.  At this point, should I tell GRUB to look for Windows at /dev/sda2 rather than /dev/sda1?

sudo fdisk -lu

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8971d0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8193149     4096543+  12  Compaq diagnostics
/dev/sda2   *     8193150   193470794    92638822+   7  HPFS/NTFS
/dev/sda3       193470795   234436544    20482875    5  Extended
/dev/sda5       193470858   230339969    18434556   83  Linux
/dev/sda6       230340033   234436544     2048256   82  Linux swap / Solaris

```

sudo sfdisk -d

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  8193087, Id=12
/dev/sda2 : start=  8193150, size=185277645, Id= 7, bootable
/dev/sda3 : start=193470795, size= 40965750, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=193470858, size= 36869112, Id=83
/dev/sda6 : start=230340033, size=  4096512, Id=82

```

---

### Post by caljohnsmith on 2009-01-21
Yes, your Windows is on sda2, so your Windows entry in the menu.lst should use (hd0,1).

---

### Post by archyslave on 2009-01-21
I had to endure some silly Microsoft keyboard rock, but I'm writing this from a clean Windows XP install.  Ubuntu is still installed and works fine.  Thanks for your help!

---

