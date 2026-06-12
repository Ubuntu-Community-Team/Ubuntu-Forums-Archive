---
title: "No option to dual boot new Ubuntu install"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by RLCGRN on 2011-03-19
I have no background in computer tweaking. I installed Ubuntu 10.04.01 from the Live CD.  The install process partitioned half my hard drive for Ubuntu, half for XP (which was already on my machine).  Upon restart the Compaq title screen appeared, then Windows did a checkdisk, then windows started.  A subsequent  computer restart just starts windows only, I am given no opportunity to choose between Ubuntu or windows.  My research on this forum here brings up stuff about Master Boot Record (MBR) and GRUB (I wonder if GRUB didn't install properly?), but I have no idea how to implement any of the instructions referenced.  What do I do?

---

### Post by Dutch70 on 2011-03-19
Removed due to finding out this is a Wubi install.

---

### Post by Quackers on 2011-03-19
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by RLCGRN on 2011-03-19
> Re: Guidance requested for moving out of XP and installing Ubuntu                                                                             First thing is  to take your time & not to freak out when something doesn't go  perfectly. I know from experience that's easier said than done, but it's  also very important. Sometimes it's to be expected when installing a  new OS. These are usually just bumps in the road. 

Please boot into the live cd, open Gparted and take a screenshot of your  partitions. attach it to your next post using the paper clip in the  toolbar. 

Along with the pic. Please post the output of the following command between code tags. Using "#" in the toolbar.
That's a lower case L in the command.
     Code:     sudo fdisk -l Also, reinstalling Grub is quite simple as well. Usually only 2 commands, as given here...
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)                                                                                               __________________
                My Computer Specs - Intel-82945G System Freeze
Please mark your thread "Solved" with "Thread Tools" at the top of the page.
Reg. Linux User-#473773-Reg. Ubuntu User-#23255-Reg. Machine-#384048                                             Last edited by Dutch70; 48 Minutes Ago at 07:04 PM.. 
Here's the results:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29312   235448608+   7  HPFS/NTFS
/dev/sda2           29314       30401     8739360    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```

---

### Post by Quackers on 2011-03-19
It appears that Ubuntu is not installed!
Did you install using wubi (from inside Windows)?

---

### Post by RLCGRN on 2011-03-19
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


           ```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   470,897,279   470,897,217   7 HPFS/NTFS
/dev/sda2         470,913,345   488,392,064    17,478,720   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2B0C1DDB0C1C865                       ntfs       PRESARIO                      
/dev/sda2        4B6E-6BC0                              vfat       PRESARIO_RP                   
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by RLCGRN on 2011-03-19
> **Quackers said:**
> It appears that Ubuntu is not installed!
Did you install using wubi (from inside Windows)?

No, I ran the Live Cd for my install, and proceeded through all the steps therein.  I tried the WUBI many months ago, but it didn't work.  I just continued using xp until recently when it's become so slow and frustrating and I wanted to give Ubuntu another round, but installing direct to hard drive.

---

### Post by Quackers on 2011-03-19
Thanks for the script output. It shows that you have a wubi install, not a normal partition install. It also shows that the sda1/wubi partition is not mounting. I'm afraid I know nothing about wubi.
I suggest that you have a look at the thread below and see if your problem is covered there.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Good luck :-)

---

### Post by Dutch70 on 2011-03-19
DO NOT try to reinstall Grub with a Wubi install.

When you boot into windows, Do you see Wubi in your programs?

---

### Post by RLCGRN on 2011-03-20
> **Dutch70 said:**
> DO NOT try to reinstall Grub with a Wubi install.

When you boot into windows, Do you see Wubi in your programs?

I do not see wubi under "add/remove programs", however I saw Ubuntu there, so I removed it thinking it may be interfering with my hard drive install.
I just ran a Windows search for Wubi, found a Wubi.exe and uninstall-wubi.exe, both PF (prefetch) files.  Trying to open or run them does nothing.

I'm jumping between XP and Live CD at this point to do this - having to restart system for each OS change!

---

### Post by Quackers on 2011-03-20
I feel your pain!
However, I re-iterate, you do not appear to have  Ubuntu installed in a partition.
Your gparted screenshot earlier shows only 2 partitions - none of those an Ubuntu partition. In fact, if you have a 250GB hard drive, it's filled with those 2 partitions. There is no room for Ubuntu to install there. You would need to resize a Windows partition first. I appreciate that you said the installer appeared to do that, but it hasn't.
I would recommend that you remove everything wubi, or Ubuntu based. I would then recommend that you resize your main Windows partition to allow for some unallocated space for Ubuntu to install into. Then try installing Ubuntu again, using the manual partitioning option and creating Ubuntu partitions within the unallocated space you created earlier.
If you are installing 10.10 DO NOT use the "install alongside" option - it may very well hose your Windows system!

---

### Post by RLCGRN on 2011-03-20
> **Quackers said:**
> I feel your pain!
However, I re-iterate, you do not appear to have  Ubuntu installed in a partition.
Your gparted screenshot earlier shows only 2 partitions - none of those an Ubuntu partition. In fact, if you have a 250GB hard drive, it's filled with those 2 partitions. There is no room for Ubuntu to install there. You would need to resize a Windows partition first. I appreciate that you said the installer appeared to do that, but it hasn't.
I would recommend that you remove everything wubi, or Ubuntu based. I would then recommend that you resize your main Windows partition to allow for some unallocated space for Ubuntu to install into. Then try installing Ubuntu again, using the manual partitioning option and creating Ubuntu partitions within the unallocated space you created earlier.
If you are installing 10.10 DO NOT use the "install alongside" option - it may very well hose your Windows system!

Ok - I will give 'er a shot.  should I just split the partition in two, one for xp, one for ubuntu, using gparted from live cd?
I do appreciate your help, Quackers!

---

### Post by Quackers on 2011-03-20
If you intend to use gparted for the split, I would recommend defragmenting XP first, at least once and preferrably twice.
After you have resized the Windows partition you should boot into XP TWICE before installing Ubuntu. Windows can be finicky about its partitions being resized.
You can make the free space any size you want to (assuming the Windows partition allows it).
You should also backup anything on XP that you don't want to lose first!
Partitioning carries risks!

---

### Post by Dutch70 on 2011-03-20
> **RLCGRN said:**
> Ok - I will give 'er a shot.  should I just split the partition in two, one for xp, one for ubuntu, using gparted from live cd?
I do appreciate your help, Quackers!

No, you'll need at least 2 partitions for Ubuntu, 3 is preferred.

One for "/" (root) & one for Swap. Swap partition should be equal to the size of your phisical RAM. The rest for "/" 

If you want a separate partition for /home (similar to documents & settings) you'll need to create a 3rd partition. Also, under this arrangement you would want "/" to be around 10-20 GB. The rest for /home.

You can take a look at my partitions to get an idea of what it would look like with a /home.
Notice that all of my Ubuntu partitions are inside of an extended partition.
btw I wish I had made mine much larger, I can't remember the last time I logged-in to windows.

---

### Post by RLCGRN on 2011-03-20
> **Quackers said:**
> If you intend to use gparted for the split, I would recommend defragmenting XP first, at least once and preferrably twice.
After you have resized the Windows partition you should boot into XP TWICE before installing Ubuntu. Windows can be finicky about its partitions being resized.
You can make the free space any size you want to (assuming the Windows partition allows it).
You should also backup anything on XP that you don't want to lose first!
Partitioning carries risks!
  
I will defrag now, did it about 2 days ago to prep for the install.
I will be going throught this tutorial when back on the live cd and implementing the necessary changes: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by RLCGRN on 2011-03-20
> **Dutch70 said:**
> No, you'll need at least 2 partitions for Ubuntu, 3 is preferred.

One for "/" (root) & one for Swap. Swap partition should be equal to the size of your phisical RAM. The rest for "/" 

If you want a separate partition for /home (similar to documents & settings) you'll need to create a 3rd partition. Also, under this arrangement you would want "/" to be around 10-20 GB. The rest for /home.

You can take a look at my partitions to get an idea of what it would look like with a /home.
Notice that all of my Ubuntu partitions are inside of an extended partition.
btw I wish I had made mine much larger, I can't remember the last time I logged-in to windows.

The attached thumbnail begins to solidify in my mind what's transpiring  in this partitioning function.
How can I buy you and Quackers a real coffee or beer as thanks for the help?

---

### Post by Hedgehog1 on 2011-03-20
> **RLCGRN said:**
> How can I buy you and Quackers a real coffee or beer as thanks for the help?

[SIZE="3"]They get REAL BEER?!?!? [/SIZE] You two are **SOOO** lucky..



***The Hedge***

:KS

---

### Post by RLCGRN on 2011-03-20
> **Hedgehog1 said:**
> [SIZE=3]They get REAL BEER?!?!? [/SIZE] You two are **SOOO** lucky..



***The Hedge***

:KS
I'm in VANWA - would you like a [SIZE=3]REAL BEER[/SIZE] too?:P

---

### Post by Dutch70 on 2011-03-20
Hahaa, beer? I'm from Kentucky
Make mine a quart of moonshine please. :lolflag:

Seriously though, knowing the true meaning of Ubuntu & paying it forward is thanks enough.

_

---

### Post by Quackers on 2011-03-20
Just a small fish or two for me please :-)

---

### Post by Dutch70 on 2011-03-20
> **Quackers said:**
> Just a small fish or two for me please :-)

LOL ...You quack me up! :D

---

### Post by Quackers on 2011-03-20
:wink:  :-)

---

### Post by RLCGRN on 2011-03-20
I'm finding everything I can about using gparted to setup my HD properly; now I need to figure which file system(s) to use, and how Ubuntu and windows can share files.  If searching here or on the www doesn't turn up what I want, I'll start a new post with those questions.

Thanks all

---

### Post by RLCGRN on 2011-03-22
Ok - 
So i wiped every thing wubi and Ubuntu related off my windows C: drive.  I then  defragged the disk 6 or 8 times until all the sections (for lack of proper term) were cohesive and contiguous. Then I ran chkdsk a couple times.  I mostly understand the process of using Gparted to setup multiple partitions, but lack the knowledge and couldn't find the guidance necessary to set up my hd with the correct type and style of partitions (primary/extended, swap, format, etc), so I decided to give the Live CD install process a second chance to do it's job as far as this goes.  It worked properly this time, and now my computer has both XP and Ubuntu availble at startup.
Thanks All!

---

### Post by Dutch70 on 2011-03-22
Nice work! Glad to hear you are successfully dual booting with Ubuntu. Now if windows goes down, you'll still have a computer ;). 

 Just to let you know, to mark your thread solved, use "[COLOR="Red"]Thread Tools[/COLOR]" at the top right of the page. That way it shows up as solved in the forum & on google searches. 

 Happy Ubuntuing :D

---

