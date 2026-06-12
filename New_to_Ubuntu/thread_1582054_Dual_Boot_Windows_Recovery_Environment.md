---
title: "Dual Boot Windows Recovery Environment"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by AndrewAustern on 2010-09-25
I installed 10.04 Ubuntu for a computer that already has Windows Vista installed.  Now when it boots, I get a menu that lists the Windows Vista option as:

Windows Recovery Environment (loader) (on /dev/sda1)

I don't exactly know what that means, but it doesn't sound good.  From what I read, a Windows Recovery Environment is for when Windows is broken.  I'm afraid my Windows Vista is now broken.  I did try choosing this option and Vista does seem to come up, but I'm afraid I've done some damage.  

- Is this a serious or cosmetic problem?
- How do I fix this problem?

Thanks, 

Andrew

---

### Post by papibe on 2010-09-26
I had the same situation. If Vista boots OK, it means that  the option is pointing to the right place (just wrongly named).

I think it a grub2's bug since it doesn't get the correct info from the disk. It is not clear to me why this hasn't been fixed yet, specially since there is a public script that does a better job of recognizing the OSes on the disk (boot info script).

Regards.

---

### Post by AndrewAustern on 2010-09-26
Sounds like this is simply cosmetic then.  Good to know.  I'd hate to be adding files only to find out I corrupted my Vista environment.  
 
Thanks.
 
Can you tell me how to get a hold of this "public script" (not sure what that means) that would fix the cosmetics?

---

### Post by warfacegod on 2010-09-26
This is purely cosmetic. I've done a number of dual installs where GRUB sees Vista incorrectly as a recovery partition. And vice versa, it sees the recovery partition as the Vista partition. If it bothers you, there's likely (been a while since I've read it) a way to fix the entry somewhere in this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by AndrewAustern on 2010-09-26
I only have the Windows Recovery Environment option.  Does this mean I don't have a recovery partition anymore?  I didn't know I had one to begin with, but sounds like something that Vista normally has?

Now I'm worried somethings not right...

---

### Post by AndrewAustern on 2010-09-26
Ignore this comment...

---

### Post by jtarin on 2010-09-26
Ok.

---

### Post by warfacegod on 2010-09-26
> **AndrewAustern said:**
> I only have the Windows Recovery Environment option.  Does this mean I don't have a recovery partition anymore?  I didn't know I had one to begin with, but sounds like something that Vista normally has?

Now I'm worried somethings not right...

Not necessarily. You don't need both partitions for GRUB to mess up the name. Many Windows installs, XP, Vista, 7, don't have recovery partitions. It all depends on how the computer manufacturer did the initial setup. They all do them differently.

---

### Post by presence1960 on 2010-09-26
Instead of speculating or guessing what may or may not be on your disk and what those options refer to why not find out for sure? 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by julio_cortez on 2010-09-27
Isn't the Windows Recovery Environment the small 100MB partition Vista and 7 use to create on their own if not forced to do otherwise?

As far as I know (I've been told so in the Vista era and I somehow saw it myself while installing 7), /sda1 is this 100MB partition, then /sda2 is Windows itself.

This small partition holds the bootloader plus bitlocker (where available) and the recovery environment that will be loaded in case Windows is unable to boot, while the rest of Vista files are located in the /sda2 partition usually..

---

### Post by presence1960 on 2010-09-27
> **julio_cortez said:**
> Isn't the Windows Recovery Environment the small 100MB partition Vista and 7 use to create on their own if not forced to do otherwise?

As far as I know (I've been told so in the Vista era and I somehow saw it myself while installing 7), /sda1 is this 100MB partition, then /sda2 is Windows itself.

This small partition holds the bootloader plus bitlocker (where available) and the recovery environment that will be loaded in case Windows is unable to boot, while the rest of Vista files are located in the /sda2 partition usually..

The 100 MB partition in **_some_** windows 7 installations is "System Reserved". It is actually the equivalent of a separate /boot partition in linux. It contains files necessary to boot windows 7. It is usually auto created when you install windows 7 to a totally unallocated disk. My install does not have it. See here:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Testdisk is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 312223275.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda7 and looks 
                       at sector 281279891 on boot drive #1 for the stage2 
                       file, but no stage2 files can be found at this 
                       location.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7408b4a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,216,579   312,216,517   7 HPFS/NTFS
/dev/sda2         312,223,275   333,188,099    20,964,825   b W95 FAT32
/dev/sda3         333,188,100   354,168,989    20,980,890   7 HPFS/NTFS
/dev/sda4         354,169,051   488,392,064   134,223,014   5 Extended
/dev/sda5         354,169,053   417,079,529    62,910,477  83 Linux
/dev/sda6         417,079,593   425,465,459     8,385,867  82 Linux swap / Solaris
/dev/sda7         425,465,523   488,392,064    62,926,542  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   754,974,674   754,974,612  83 Linux
/dev/sdb2         754,974,675   976,768,064   221,793,390   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8a8a8a8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   838,866,104   838,866,042  83 Linux
/dev/sdc2         838,866,105 1,953,520,064 1,114,653,960   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5C21A069471313D7                       ntfs       windows7                      
/dev/sda2        039B-7ADA                              vfat       clonezilla-                   
/dev/sda3        42AAC3ED50603A5D                       ntfs       mozilla-profiles              
/dev/sda5        68133ee7-9788-4905-b012-452696873308   ext4       karmic 9.10                   
/dev/sda6        4f17c8fd-b57d-4870-864a-694c0610686f   swap                                     
/dev/sda7        9e202df5-42a8-4954-80a3-8b9b28d422af   ext4       sabayon                       
/dev/sdb1        2c0ea91f-1ea5-4394-b694-0a60f5b08b78   ext4       data-linux                    
/dev/sdb2        3075F35B7A562F9F                       ntfs       data-windows                  
/dev/sdc1        945dc762-b626-42a0-9d92-b6c8cf0c090b   ext4       backup-linux                  
/dev/sdc2        088EA3930C3D1FE5                       ntfs       movies     
```  

The above is part of the output from the boot info script I asked the OP to run. If he would do as suggested we won't have to guess and debate as to what the item in question actually is.

---

### Post by julio_cortez on 2010-09-27
> **presence1960 said:**
> The 100 MB partition in **_some_**  windows 7 installations is "System Reserved". It is actually the  equivalent of a separate /boot partition in linux.I thought it  also included "Windows Recovery Environment" aswell (see [LINK]("http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/")).

You're indeed right that only Ultimate and Professional have this  feature (I know for sure about the latter because I'm running it so I  won't see a reason for Ultimate not to have it). My fault I didn't mention Home versions not having it ;)

Being the boot files located in that partition, in my opinion GRUB lists that  partition as "bootable" but maybe retains the "Windows RE" name, that's  all!!

> **presence1960 said:**
> My install does not have itNeither does mine (I did the same as shown in "Method 3" on the link I provided above), that's why I think GRUB lists my Windows 7 like "Windows 7 (loader)" instead of "Windows RE".

But, again, an output of his boot info script should clarify things :)

---

