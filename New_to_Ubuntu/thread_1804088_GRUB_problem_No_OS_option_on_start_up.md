---
title: "GRUB problem: No OS option on start up"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by tompadfield on 2011-07-14
Hello all,

Utter newcomer to Ubuntu here. I have just installed Ubuntu alongside Windows 7 in the naive hope that when I rebooted my computer I would have a nice obvious option as to whther I would like to run Ubuntu or Windows. However, the computer just goes right ahead and loads up Windows as if nothing had ever happened.

I have had a good trawl through the forums trying to find a solution but haven't been able to find anything addressing this particular option or which I can easily understand. 

All help would be very gratefully accepted!
Thanks,
Tom.

---

### Post by mikejonesey on 2011-07-14
start by booting a live cd and verifying both partitions exist as they should, if they do then reinstall grub, otherwise if your linux part is missing install again...

---

### Post by oldfred on 2011-07-14
Reinstall grub2's boot loader as mikejonesey suggests. You have to install to the MBR of the drive not to a partition. If you happened to install to the windows partition you will have windows issues also.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If everything does not work after a grub repair run this script:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by tompadfield on 2011-07-14
Thanks guys, I'm afraid I didn't make it quite clear enough how clueless I am. I'm running from the livecd at the moment but how exactly do I go about verifying the partitions are as they should be? And how exactly should they be anyway?

I'm trying to follow the instructions under your link Reinstalling GRUB2, Oldfred, but I get as far as this:


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1577    12659712   27  Unknown
/dev/sda2   *        1577        1589      102400    7  HPFS/NTFS
/dev/sda3            1589       60802   475622424    7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xccf25dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       47401   380744462+   c  W95 FAT32 (LBA)
/dev/sdb2           47401       77826   244386817    5  Extended
/dev/sdb5           77308       77826     4159488   82  Linux swap / Solaris
/dev/sdb6           76790       77308     4157440   82  Linux swap / Solaris
/dev/sdb7           76272       76789     4155392   82  Linux swap / Solaris
/dev/sdb8           47401       75754   227746816   83  Linux
/dev/sdb9           75754       76272     4154368   82  Linux swap / Solaris

Partition table entries are not in disk order


and then I'm stuck. Are these different /dev/sd?? bits the different partitions? Which one is Ubuntu under?

---

### Post by tompadfield on 2011-07-14
Right, having attempted to follow the advice at [https://help.ubuntu.com/community/Gr...alling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2") my computer on start up now displays:

error: no such device: 9a0af67c-c0ba-4b7baee0-4787b64f0d68
grub rescue>

To an absolute beginner like me this is terrifying. 

Here is what I ran in the terminal (as best as I can remember):

sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

[FONT=Arial]Please see my post above for the information about my partitions.

PLEASE HELP!
[/FONT]

---

### Post by tompadfield on 2011-07-14
**Further adding to my terror is the fact that now that I do**
sudo fdisk -l

[FONT=Arial]**I only get **
[FONT=Courier New]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x811615c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1577    12659712   27  Unknown
/dev/sda2   *        1577        1589      102400    7  HPFS/NTFS
/dev/sda3            1589       60802   475622424    7  HPFS/NTFS

[B][FONT=Arial]compared to the 

[/FONT][/B][/FONT][/FONT][FONT=Courier New][SIZE=1]D[/SIZE][/FONT][FONT=Courier New][SIZE=1]evice Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1577    12659712   27  Unknown
/dev/sda2   *        1577        1589      102400    7  HPFS/NTFS
/dev/sda3            1589       60802   475622424    7  HPFS/NTFS
Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xccf25dda
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       47401   380744462+   c  W95 FAT32 (LBA)
/dev/sdb2           47401       77826   244386817    5  Extended
/dev/sdb5           77308       77826     4159488   82  Linux swap / Solaris
/dev/sdb6           76790       77308     4157440   82  Linux swap / Solaris
/dev/sdb7           76272       76789     4155392   82  Linux swap / Solaris
/dev/sdb8           47401       75754   227746816   83  Linux
/dev/sdb9           75754       76272     4154368   82  Linux swap / Solaris
Partition table entries are not in disk order
[/SIZE][/FONT][FONT=Courier New][SIZE=1]
[B][FONT=Arial]that I had before.
Feeling more than a little out of my depth...
[/FONT][/B][/SIZE][/FONT]

---

### Post by grahammechanical on 2011-07-14
On the live CD you should find something called Disk Utility. That will give a graphical or visual reprentation of your hard disks and show you how they have been partitioned. Some screen shots would be useful.

From that printout it seems to me that you have two hard disks. Is this correct? The first hard disk or drive is sda (SATA device a) and it has 3 partitons 1, 2, and 3. The second drive is sdb with 7 partitions.

sdb2 is called an extended partition. Partitions from 5 to 9 are inside this extended partition which is as it should be except for the fact that you have 5 Linux swap partitions. You only need one. I have three versions of Ubuntu on my hard disk and I have assigned them the same swap partition as I am only running one example of Ubuntu at a time.

It seems to me that you have made more than one attempt to install Ubuntu. Your actual Ubuntu partition, I would guess is sdb8.

Think about (read up on) installing Ubuntu again and using the Do something else option to give you control over the partition manager. Delete partitions 5, 6 and 7 and enlarge partition 8 to take up the now unallocated space. so, that you have only tow partitions inside sdb2.

Regards.

P.S. Here is a link to Community Documentation with pictures.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by tompadfield on 2011-07-14
Thank you, Graham. I'm in the process of trying to find that Disk Utility. Yes, I have made more than one attempt to install Ubuntu. 


I've had a look at the Do Something Else Option but its only showing the following:

---

### Post by tompadfield on 2011-07-14
I can't even manage to get a screen shot to work. 
What I was trying to show was that it was only showing 3 partitions.

---

### Post by tompadfield on 2011-07-14
[IMG]http://ubuntuforums.org/desktop[/IMG]

---

### Post by Quackers on 2011-07-14
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tompadfield on 2011-07-14
```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 8 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    25,321,471    25,319,424  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     25,321,472    25,526,271       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          25,526,272   976,771,119   951,244,848   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A6C849DEC849AD7D                       ntfs       Recovery
/dev/sda2        36DC8D6CDC8D26E9                       ntfs       System Reserved
/dev/sda3        6E688F0D688ED36F                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

```

---

### Post by Quackers on 2011-07-14
I think you've chopped most of the output off :-)
Please copy/paste the whole contents of Results.txt In code tags please!

---

### Post by tompadfield on 2011-07-14
I'm afraid I haven't: I selected all with Ctrl+A and I've just gone to  the text file and double checked, it's all there. Just to be on the safe  side here it all is again:


```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 8 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    25,321,471    25,319,424  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     25,321,472    25,526,271       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          25,526,272   976,771,119   951,244,848   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A6C849DEC849AD7D                       ntfs       Recovery
/dev/sda2        36DC8D6CDC8D26E9                       ntfs       System Reserved
/dev/sda3        6E688F0D688ED36F                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

```

---

### Post by Quackers on 2011-07-14
That is only giving information for /dev/sda - nothing for /dev/sdb.
Did you try manually copy/paste?
The boot script picks up details from all connected storage devices.
Is /dev/sdb connected?

---

### Post by tompadfield on 2011-07-14
Aw, I've just realised something that's going to have complicated matters hugely. When I installed Ubuntu and messed about with the GRUB stuff as I described above I had plugged in a little USB hard drive. When things started to go wrong I unplugged said external hard drive. I'm guessing that it was the external drive that was being recognised as the external partition?

Please feel free to tell me that I am an utter half-wit.

Now with external hard drive reconnected here are the new results:

```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 8 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /grub/core.img

sdc9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    25,321,471    25,319,424  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     25,321,472    25,526,271       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          25,526,272   976,771,119   951,244,848   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   761,488,987   761,488,925   c W95 FAT32 (LBA)
/dev/sdc2         761,489,406 1,250,263,039   488,773,634   5 Extended
/dev/sdc5       1,241,944,064 1,250,263,039     8,318,976  82 Linux swap / Solaris
/dev/sdc6       1,233,623,040 1,241,937,919     8,314,880  82 Linux swap / Solaris
/dev/sdc7       1,225,304,064 1,233,614,847     8,310,784  82 Linux swap / Solaris
/dev/sdc8         761,489,408 1,216,983,039   455,493,632  83 Linux
/dev/sdc9       1,216,985,088 1,225,293,823     8,308,736  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A6C849DEC849AD7D                       ntfs       Recovery
/dev/sda2        36DC8D6CDC8D26E9                       ntfs       System Reserved
/dev/sda3        6E688F0D688ED36F                       ntfs       
/dev/sdc1        0107-1806                              vfat       USB-HDD
/dev/sdc5        9b8c545c-3dab-4ec4-bfd9-dfe312d273dd   swap       
/dev/sdc6        7db4b794-4574-4066-9096-899c45e1cf79   swap       
/dev/sdc7        193a69b7-cfa0-460a-8c4d-a940b158ea8a   swap       
/dev/sdc8        9a0af67c-e0ba-4b7b-aee0-4787b64f0d68   ext4       
/dev/sdc9        cec7e0f4-1283-4f11-b9a9-f9ffb1bff4a2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/6E688F0D688ED36F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/USB-HDD           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc8        /media/9a0af67c-e0ba-4b7b-aee0-4787b64f0d68 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sdc8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb8       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=cec7e0f4-1283-4f11-b9a9-f9ffb1bff4a2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 541.233398438 = 581.144936448  grub/core.img                                  1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
```

```

---

### Post by Quackers on 2011-07-14
So /dev/sdc is an external hard drive?
If that is the case it would be better to repair the Windows bootloader on /dev/sda with a Windows repair/installation disc. That should get Windows booting again if /dev/sda is first bootable hard drive in your bios.

I would then recommend that as your current Ubuntu is in a bit of a mess (currently you have 4 swap partitions! and I'm not convinced it is fully installed) you re-install Ubuntu using the whole disc on /dev/sdc (or in pre-created partitions) and this time at the bottom of the partitioning screen (manual - or "something else" in Natty) you change the default destination for installing the bootloader from /dev/sda to /dev/sdc (the drive - not a partition).
This way, if you set the external drive as the first bootable hard drive in bios, it will load grub only when that drive is connected. If the external drive is not connected your /dev/sda drive will just boot Windows normally.

---

### Post by tompadfield on 2011-07-14
> So /dev/sdc is an external hard drive?Yes, I guess it must be.

> If that is the case it would be better to repair the Windows bootloader  on /dev/sda with a Windows repair/installation disc. That should get  Windows booting again if /dev/sda is first bootable hard drive in your  bios.I'm in the process of trying to find somewhere to download a windows repair disk. If you (or anyone else) can point me in the right direction of where to find one I would be even more indebted to you even more than I already am.

> I would then recommend that as your current Ubuntu is in a bit of a mess  (currently you have 4 swap partitions! and I'm not convinced it is  fully installed) you re-install Ubuntu using the whole disc on /dev/sdc  (or in pre-created partitions) and this time at the bottom of the  partitioning screen (manual - or "something else" in Natty) you change  the default destination for installing the bootloader from /dev/sda to  /dev/sdc (the drive - not a partition).I'm afraid I understand very little of this. At the moment I would be very happy just to get back to a usable windows computer as much as I love the ethos of Ubuntu.

> This way, if you set the external drive as the first bootable hard drive  in bios, it will load grub only when that drive is connected. If the  external drive is not connected your /dev/sda drive will just boot  Windows normally.     Thats not really possible I'm afraid as the external drive contains my record collection and is constantly connected to my laptop. Is it really not possible to easily install a dual boot that gives you the option when you start up which OS you would like to run?


Again, I can't tell you how grateful I am for your help.

---

### Post by Quackers on 2011-07-14
If /dev/sdc is a USB drive then it's external. If it's plugged in to your motherboard then it's internal and connected all the time.
Don't you have a Windows installation disc? There used to be a site that I used to download Windows repair discs from but they have removed them, however others still do I believe. Google for that.
Ideally you should have made one from within Windows (Control Panel > Backup & Restore Centre > create recovery cd) and should do so when you get it booting again.
You will need a Vista or Win 7 repair disc for your specific architecture - ie if you system is 32 bit you will need a 32 bit repair disc.

As far as your concerns regarding your record collection etc, that's fine. Just create partitions for Linux manually or let the installer do it (after deleting the contents of your curren extended partition - not sdc1.

Yes it's possible to easily install a dual boot system with a menu that gives you a choice of which OS to boot - if the installation goes normally. Yours may not have done.

There is another alternative. 
Boot from the Ubuntu live cd/usb when both hard drives are connected.
Select "try Ubuntu" and when the desktop loads start gparted.
Right-click on all the swap partitions and select "swapoff" if necessary.
Delete all the linux and swap partitions one at a time and the extended partition (sdc2), so you just end up with sdc1 (your data partition), and some free space.
Don't forget to apply the changes by clicking on the green tick mark in the toolbar.
Close gparted.
On the desktop click on the "Install Ubuntu" icon and start again.
Leave the default location for grub as /dev/sda.
When finished on rebooting Ubuntu should boot directly. If it does open up a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to make sure that the Windows Loader is picked up.
If it is, reboot and you should then get a grub menu giving you the choice of which OS to boot.

---

### Post by tompadfield on 2011-07-14
Its definitely an external USB drive. No I don't have a windows installation disc, and yes I feel like a tit for not making one before I started buggering about with things. I have made the back-up disks in the past but I know I don't have one here with me now. Is it even possible to download and burn a windows recovery disk whilst the only way I can use my computer is by running it from the Ubuntu liveCD? Perhaps the best bet would be to get a friend to do one from their computers for me and do it that way? I have also read that you can download the recovery data to a USB stick but how do get the computer to recognize its there on start up?

I will definitely try your advice on how to do it properly once I get things functional again , as I'm determined to become a Ubuntu user, but its really all gone a bit Pete Tong this first time round.

---

### Post by Quackers on 2011-07-14
If you have no data in the Ubuntu install (which I presume is brand new) you should try the alternative suggestion I made. That should work and you should get both booting at the end of it :-)

---

### Post by tompadfield on 2011-07-14
I got my hands on a recovery CD from a flatmate and have tried to run the Start-Up repair feature but all it says is that Windows can not solve this problem automatically. Any suggestions as to what to try next?

---

### Post by Dead ChexMix on 2011-07-14
Providing you have a valid Ubuntu install, if you boot into Windows, you can use a utility called EasyBCD to help you greatly.

_YOU MUST BE ABLE TO BOOT INTO WINDOWS. QUAKERS SUGGESTION BELOW ME WILL HELP IF THATS NOT POSSIBLE._

1. Download and Install EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1))

2. Launch EasyBCD

3. Click "Add New Entry"

4. In the tabs select "Linux/BSD"

5. Select "Grub2"

6. Go to "Edit Boot Menu"

7. Change the NeoSmart Linux entry to whatever you like.

8. Click "Save Settings"

9. Reboot and test out the Linux entry.

This will allow the Windows MBR to be the default. Grub will not be the default anymore. Providing your Ubuntu install is correct, this should suit your needs. (Unless you want a Grub MBR default.)

---

### Post by Quackers on 2011-07-14
Try entering the command prompt option in the recovery console and run this ```
bootrec.exe /fixmbr
``` NOTE the space between exe and /fixmbr, then press enter. If it reports no errors please reboot and see if Windows boots up.
Also which hard drive is set to boot first in your bios? Please check.

---

### Post by tompadfield on 2011-07-14
Thanks again, Quakers. I'll try thoso now. But how do I check which hard drive is set first to boot in my bios?

---

### Post by Quackers on 2011-07-14
At boot you have to enter your computer's bios. There will be a key to tap whilst booting which may be particular to your computer. It is often something like F2 or F11 or the del key or maybe ctrl+F11/ You need to find that out from your manual or the manufacturer's website.

---

### Post by tompadfield on 2011-07-14
At last I have some good news to report: windows is back to running normally thanks to following this that I found in another GRUB problems thread:

> From an Ubuntu Live CD you should be able to get Windows back with the  following if you just need to restore the MBR (assumes Windows is on  sda):

     Code:
     sudo apt-get install lilo sudo lilo -M /dev/sda mbr 
Don't worry if lilo complains about not being fully installed...What I would like to do now is to make sure I've completely uninstalled every last scrap of Ubuntu, de-frag my hard drive and burn all the appropriate back-up and repair disks and THEN have another go at installing Ubuntu with going doing anything I'm not sure about.

Can you offer any advice as to what the best way to clean my drives of all Ubuntu/GRUB is?

---

### Post by Quackers on 2011-07-14
Well that's good - if unexpected :-)

You don't have to uninstall Ubuntu as such. If you make all your backups and discs then boot from the Ubuntu live cd/usb and open up gparted. Then select /dev/sdb (or it could be /dev/sdc because the disk designation has changed from your first post - maybe due to plugging something in) from the drop-down box and delete all the partitions from /dev/sdb (or sdc) except your NTFS partition which will be sdb1 or sdc1.
Don't forget the extended partition - once it's empty!

You can then try installing Ubuntu from scratch once again. Either using the install alongside option (on the correct drive! ) or by manually creating the necessary partitions by selecting the "something else" option in the Ubuntu installer.

---

### Post by oldfred on 2011-07-14
To add to the good advice from Quackers. You want to be sure to install  grub2's boot loader to the MBR of the external device, so your internal still directly boots windows.

To get the combo box that lets you choose where to install the boot loader you have to do manual install or 'Something Else' in Natty. You can partition in advance with gparted or partition as part of the manual install. You just need / (root) & swap but we often suggest a separate /home. When the grub2 boot loader is installed to sdb or sdc (whichever it is then seen as) then it will give you the option to boot windows or Ubuntu. If you set in BIOS to boot the external first, but if the external is not plugged in then you can boot the internal drive's windows boot loader.

Lots of detailed info. Not as difficult as it may first seem as Herman has so much related info.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by tompadfield on 2011-07-14
Thank you, Quackers. Your advice has been invaluable today; if it wasn't for you I'd have probably have spent the last seven hours on the phone to the Samaritans!

---

### Post by Quackers on 2011-07-14
Well, at least I was cheaper :-)

---

