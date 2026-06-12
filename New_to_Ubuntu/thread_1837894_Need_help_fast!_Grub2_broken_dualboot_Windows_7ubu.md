---
title: "Need help fast! Grub2 broken dualboot Windows 7/ubuntu 10.04LTS"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by beseiker on 2011-09-02
Hello,
 
I am a complete beginner with ubuntu, and I installed it inside of windows and dual booted it. After an update, the purple ubuntu boot screen faded to a white screen, and wouldn't boot. When I tried a hard reboot, the laptop booted straight into windows, with no options appearing.
 
I used a liveCD and tried reinstalling grub2 after doing some research, and now the computer boots to the gurb command line, and I am now stuck, unable to boot windows. 
 
I have no clue what to do...

---

### Post by lmarmisa on 2011-09-02
> **beseiker said:**
> Hello,
 
I am a complete beginner with ubuntu, and I installed it inside of windows and dual booted it. After an update, the purple ubuntu boot screen faded to a white screen, and wouldn't boot. When I tried a hard reboot, the laptop booted straight into windows, with no options appearing.
 
I used a liveCD and tried reinstalling grub2 after doing some research, and now the computer boots to the gurb command line, and I am now stuck, unable to boot windows. 
 
I have no clue what to do...

Are you able to boot into Ubuntu now?.

---

### Post by HarriU11-04 on 2011-09-02
> **beseiker said:**
> Hello,
 
I am a complete beginner with ubuntu, and I installed it inside of windows and dual booted it. After an update, the purple ubuntu boot screen faded to a white screen, and wouldn't boot. When I tried a hard reboot, the laptop booted straight into windows, with no options appearing.
 
I used a liveCD and tried reinstalling grub2 after doing some research, and now the computer boots to the gurb command line, and I am now stuck, unable to boot windows. 
 
I have no clue what to do...
Look here
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

and here
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Fairly straight-forward tutorials, written for Windows users

---

### Post by beseiker on 2011-09-02
No, not able to boot into ubuntu. Not really sure what I did, but i broke something. At the prompt, i type 
 
[boot (hd0, 5)] 
 
and it says error: no loaded kernel

---

### Post by lmarmisa on 2011-09-02
Boot into an Ubuntu Live CD, select Try Ubuntu, open Firefox and go to this web page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please, run the Boot Info Script and post the results. Follow the instructions of the link.

---

### Post by beseiker on 2011-09-02
ok here is the results

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   586,969,087   583,895,040   7 NTFS / exFAT / HPFS
/dev/sda3         586,969,088   953,970,687   367,001,600   f W95 Extended (LBA)
/dev/sda5         586,971,136   953,970,687   366,999,552   7 NTFS / exFAT / HPFS
/dev/sda4         953,970,688   976,773,119    22,802,432  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D090DD3F90DD2CAA                       ntfs       System
/dev/sda2        8A34034D34033BA7                       ntfs       TI105955W0C
/dev/sda4        DE28298C282964AD                       ntfs       HDDRECOVERY
/dev/sda5        34064164064127E6                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda5/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/stage2                               1

---

### Post by lmarmisa on 2011-09-02
Your computer has installed [Ubuntu with Wubi]("https://wiki.ubuntu.com/WubiGuide").

You should not have installed GRUB2. This was a mistake!!.

You have to restore the MBR of your hard drive /dev/sda now:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by beseiker on 2011-09-02
Ha yea clearly i goofed. Surprise!
 
I was afraid that would be required. i do not have a windows 7 rescue cd. 
 
any way of doing it from ubuntu liveCD?

---

### Post by chris153 on 2011-09-02
so when you start up, it goes to the grub menu, right? what you need to do is chainload windows. the way to do this is,

chainloader (hdX,Y)+1
boot

you are probably going to use (hd0,2) from the looks of that printout, but i could be mistaken.

---

### Post by lmarmisa on 2011-09-02
Sorry. I am not an expert in Windows 7. The partition /dev/sda1 seems a recovery environment. I do not if this partition could be used for repairing your system.

**If you are not able to find any procedure for recovering Windows7,** you could try this procedure. You will use your Ubuntu Live CD:

1 ) Make a complete backup of you system using [Clonezilla Live]("http://clonezilla.org/") and an external USB hard drive.
 
2 ) Boot into an Ubuntu Live CD.

3 ) Open Gparted for modifying your partitions.

4 ) Shrink the NTFS partition /dev/sda5. Try to release about 15 - 20 Gbytes.

5 ) Define a new ext4 logical partition /dev/sda6 using the free space of the disk minus the size of your RAM (it would be better if you could leave unallocated a bit more free space than your RAM).

6 ) Define a new swap partition /dev/sda7 with a size slightly bigger than your RAM (use the free space of the hard drive).
 
7 ) Close Gparted.

8 ) Install Ubuntu selecting manual definition of partitions. Use /dev/sda6 for root ( / ) and /dev/sda7 for swap.

After this new installation, you should be able to boot not only into Ubuntu but also into Windows 7.

Use this procedure only if you are unable to recover the MBR of Windows 7.

Best regards,

Luis

---

### Post by ajgreeny on 2011-09-02
Try this site:-
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Or you might like to try this option from a live ubuntu CD.
Open a terminal and run the two commands ```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
``` lilo will complain and throw warnings up but you can ignore them since all you want is to get lilo installed to the MBR.


I've not done this ever, but it is pretty well documented in various forums.

---

### Post by beseiker on 2011-09-02
Chris153,
 
Nah i tried that. it says "No such disk" for every option. 
 
Luis,
 
I believe my brother has a rescue cd, so hopefully that will fix it. Thank you so much for your help!

---

### Post by bcbc on 2011-09-02
You are missing the \ubuntu\disks folder (or all the files that should be there including the root.disk and swap.disk).

You also have a \ubuntu\winboot\menu.lst (grub legacy) which is not part of 10.04LTS unless perhaps you have upgraded from an older version of Wubi e.g. 8.04? 

If you had important data on your Wubi install, you'll have to try and locate the root.disk after you get windows booting again. The quickest way is as *ajgreeny* suggested using lilo from the live CD.

PS this might help locate the root.disk: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by beseiker on 2011-09-02
bcbc, 
 
i will give that a whirl. before I played with the grub, I tried to just boot into windows, and delete ubuntu in order to reinstall it, but windows couldn't find the wubi application or ubuntu so it couldn't delete it. perhaps the pointers were reassigned somehow by the update i did. Im not sure. 
 
I guess my next question would be, 
 
assuming that recovering the MBR for windows solves the problem of not being able to boot into windows, I want to install Ubuntu next to windows, not using wubi.
 
Can i boot into windows and partition the disk into two drives, then reboot from the liveCD and install ubuntu next to windows on the partitioned drive?
 
People seem to have lots of trouble with wubi....

---

### Post by bcbc on 2011-09-02
> **beseiker said:**
> bcbc, 
 
i will give that a whirl. before I played with the grub, I tried to just boot into windows, and delete ubuntu in order to reinstall it, but windows couldn't find the wubi application or ubuntu so it couldn't delete it. perhaps the pointers were reassigned somehow by the update i did. Im not sure. 
 
I guess my next question would be, 
 
assuming that recovering the MBR for windows solves the problem of not being able to boot into windows, I want to install Ubuntu next to windows, not using wubi.
 
Can i boot into windows and partition the disk into two drives, then reboot from the liveCD and install ubuntu next to windows on the partitioned drive?
 
People seem to have lots of trouble with wubi....
You have an extended partition already so you should be able to shrink /dev/sda5 (using gparted or through Windows) and then create two new logical partitions in that space - one for Ubuntu and one for swap. Then just install Ubuntu directly to those partitions. Don't worry about creating a new 'drive' in Windows - that's not required.

You could also let the Ubuntu installer automatically split /dev/sda5 but I've heard that it doesn't always create a big enough swap partition (required to hibernate) so my own preference is to partition manually.

PS If you manage to recover your root.disk you can also [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") that to your newly created partitions. Great if you've done a lot of setup. Otherwise, just do a fresh install.

---

### Post by ajgreeny on 2011-09-02
> **beseiker said:**
> I guess my next question would be, 
 
assuming that recovering the MBR for windows solves the problem of not being able to boot into windows, I want to install Ubuntu next to windows, not using wubi.
 
Can i boot into windows and partition the disk into two drives, then reboot from the liveCD and install ubuntu next to windows on the partitioned drive?
 
People seem to have lots of trouble with wubi....
That's a better idea than using wubi, which is meant as a tool to check if you like Ubuntu, and if your hardware will run it properly.

Before we give you a straight answer to how best to proceed we need to know the current partition layout, so from the live Ubuntu CD using a terminal run the command ```
sudo fdisk -l
```(lower case L at the end), and report the output back here.

Win7 often uses all of the 4 possible partitions on a disk, and means that something has to go, but we need to know what they all are first, so look in any documentation you have as well to see if there are **recovery** or **manufacturer's tools **partitions listed, and we can then give you a better clue about how best to make new partitions for Ubuntu.

---

### Post by beseiker on 2011-09-02
here's the fdisk output
 
[FONT=Courier New][SIZE=2]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff592f49[/SIZE][/FONT]

[SIZE=2][FONT=Courier New]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       36538   291947520    7  HPFS/NTFS
/dev/sda3           36538       59382   183500800    f  W95 Ext'd (LBA)
/dev/sda4           59382       60802    11401216   17  Hidden HPFS/NTFS
/dev/sda5           36538       59382   183499776    7  HPFS/NTFS[/FONT][/SIZE]

[FONT=Courier New][SIZE=2]Disk /dev/sdc: 4043 MB, 4043309056 bytes
150 heads, 48 sectors/track, 1096 cylinders
Units = cylinders of 7200 * 512 = 3686400 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xafc8f73f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1097     3948520    7  HPFS/NTFS[/SIZE][/FONT]

---

### Post by kansasnoob on 2011-09-02
> **beseiker said:**
> Ha yea clearly i goofed. Surprise!
 
I was afraid that would be required. i do not have a windows 7 rescue cd. 
 
any way of doing it from ubuntu liveCD?

Yes. Boot into the Ubuntu live desktop and run these commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Also, something I won't live without anymore is this disc:

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

It doesn't fix anything but the "detect any OS" feature will boot almost anything :)

---

### Post by beseiker on 2011-09-03
Got windows up and running again! no problem!

Thank you guys, you are awesome!

I will mark this thread as solved.

---

