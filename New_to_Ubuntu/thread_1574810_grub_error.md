---
title: "grub error"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by timmy303 on 2010-09-14
I just started use ubuntu( like 2 hours ago) and I seemed to mess some things up. after i got the netbook remix running i opened a web browser and it asked me to update so i did. right after that i rebooted and now i can't get either OS to boot. it takes me to a prompt screen where it says "error: no such device" and "grub recue". i tried booting from my usb and i get the message "geom error" then the same as before. any ideas? thanks.

i would really like to just boot windows if anyone can help with that

---

### Post by timmy303 on 2010-09-15
so i have been reading over anything i can find that has do with with grub rescue> commands and i have found few that do anything for me. most of the faqs or tutorials have commands that dont work for me(help being one that is a "unknown command). im not quit sure how to post the boot info script from willie-nillie's sig from the grub rescue prompt either.

---

### Post by garvinrick4 on 2010-09-15
If your USB is set to boot first in order in BIOS or you have a selection to choose what you want to boot from at each boot instance then USB install flash drive should boot. It has nothing to do with hard disk boot at all.
 It seems you most likely have to put grub into sda which is quite easy to do if you get your flash to boot and choose try Ubuntu and get to desktop.

#sda being your hard drive and it has a mbr which holds the grub.
When you get into ubuntu desktop open up a terminal and put this in:
```
sudo fdisk -l
```(small L)```
sudo blkid
```Copy and paste them to this thread you started and will be able to give you code
to put the grub back to where it belongs. 
Now if you can download this script to your DESKTOP .
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
and then run this code in a terminal and it will put a file on your desktop. Copy and 
Paste that and it will tell everything about your boot process and easier to fix.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by timmy303 on 2010-09-15
When i tried to boot from my USB it would give me a "geom error" and then the same as before right under. im going to download the USB installer again and retry.

---

### Post by garvinrick4 on 2010-09-15
> **timmy303 said:**
> When i tried to boot from my USB it would give me a "geom error" and then the same as before right under. im going to download the USB installer again and retry. OK, post when info when you can.

---

### Post by candtalan on 2010-09-15
What does it do when you run a live session from the live USB stick? 

I guess you are using Ubuntu version 10.04 (latest for netbook)? 

At the early stage of booting from the USB stick, if you press a key when you see three symbols at the bottom of the screen, then you will be given a menu, and one of the items allows to check the media (your usb stick) for errors, this might be worth considering also.

---

### Post by bcbc on 2010-09-15
If you installed using WUBI (installed within windows) - and it sounds like you have - then likely you allowed a grub update to install itself to your drive MBR. You can't do anything with the grub rescue> prompt if this is the case.

You will need to reinstall the windows bootloader:
For win7, boot from your recovery CD/USB and run: 
bootrec.exe /fixmbr

For win XP run:
fixmbr

If you don't have the ability to run windows repair, then your best bet is to boot into an Ubuntu live CD/USB and run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

That will install the lilo bootloader in a version equivalent in function to the windows bootloader. You can ignore the warnings the first command gives you - it's related to booting linux, not windows.

This fix will likely get you booting Ubuntu again as well.
ONLY if you installed using wubi. If you didn't install using wubi it will still get windows booting (just not ubuntu).

---

### Post by timmy303 on 2010-09-15
ok here we go. I downloaded a new installer and booted with it just fine. I guess I did something to mess my USB up( im thinking not ejecting it before i removed it). i ran the script so here you go. i cant thank everyone who helped enough. for a know nothing noob to be able to mess everything up from the get go and still find help is awesome. im looking forward to using linux more and more, regardless if i jammed up my computer for 2 days.
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,193,149     8,193,087  12 Compaq diagnostics
/dev/sda2    *      8,193,150    90,124,649    81,931,500   7 HPFS/NTFS
/dev/sda3          90,124,650   312,576,704   222,452,055   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,837,695     7,837,664   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ebeb01d1-7a61-43c9-aa1c-4633c474749c   ext4                                     
/dev/sda1        C097-EDA3                              vfat       WINRE                         
/dev/sda2        78F4CDDDF4CD9DAE                       ntfs       OS_Install                    
/dev/sda3        9C60A50260A4E46C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C6B-4075                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu Netbook" 
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by bcbc on 2010-09-15
OK you do have wubi, and you are suffering from the problem I described. Reinstall the windows bootloader, or lilo as per my previous post. This will get windows booting.

Your wubi root.disk is also looking a bit rough (could not be mounted by bootinfoscript). Doesn't mean it can't be recovered, but get windows back first, and try booting ubuntu and then we can take it from there.

PS here's the bug report: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by timmy303 on 2010-09-16
That worked. It took a minute to figure out, but it works just fine now. Thank you again for the help. I see a whole lot of faqs and tutorials in my future.

P.S. reading the bug report was a little intense, but helpful. Thanks for posting it.

---

### Post by bcbc on 2010-09-16
It's unfortunate to have a bug like this, because wubi is aimed at new users. However, there are a number of issues with grub2 (which is relatively new) and I don't think this wubi one is high on the list of priorities. So I guess we'll just have to live with it.

My advice for wubi is: don't install grub to any devices, consider backing up the root.disk before a major update/upgrade. Don't feel that every update needs to be installed right away - read the changelog and unless it's a critical security fix or you have a problem that needs fixing, it's probably safe to ignore. 

If you do all that, likely you can ignore the manuals and faqs and get on with using the OS the way it is intended.

---

