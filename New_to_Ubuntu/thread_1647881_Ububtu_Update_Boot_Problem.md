---
title: "Ububtu Update Boot Problem"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by prbugzdaman7 on 2010-12-18
I have a desktop dual booting windows 7 as primary OS and Ubuntu on partition.

Today i was updating ubuntu on my desktop, and while i was updating it asked me if i wanted to update GRUB so i did. when the update was finished it asked to restart so i did. When my desktop booted up i did not see either of my operating systems.

I was reading about the issue being the MBR and how it needs to be fixed or something like that, but i'm new to the linux community so i have no idea on what i have to do in order to get my desktop's OS's back up and running.

Thanks all in advanced.

---

### Post by lmarmisa on 2010-12-18
Please, boot your system into a Live CD (or Live USB). Then run the Boot Info Script of this page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Finally, post the file RESULTS.txt.

You will get more help according to the results of that script.

---

### Post by amjjawad on 2010-12-18
> **lmarmisa said:**
> Please, boot your system into a Live CD (or Live USB). Then run the Boot Info Script of this page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Finally, post the file RESULTS.txt.

You will get more help according to the results of that script.

+1 to the boot script 

Please, don't forget to wrap up your text with "#" or "CODE" tags ;)

---

### Post by prbugzdaman7 on 2010-12-18
#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   874,371,071   874,164,224   7 HPFS/NTFS
/dev/sda3         874,371,072   976,769,023   102,397,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       983803ed-eaef-4b4d-bea8-885af3648396   ext4                                     
/dev/sda1        1014C18C14C1756E                       ntfs       System Reserved               
/dev/sda2        A490C42890C402B2                       ntfs       Windows 7                     
/dev/sda3        8AF05AEAF05ADBCF                       ntfs       Linux                         
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


=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by amjjawad on 2010-12-18
Apparently it's Wubi installation.

Check this link: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
It might help you.

---

### Post by sikander3786 on 2010-12-18
Yes Wubi. See problem # 1 on the thread that *amjjawad* linked in above post.

And once it is all fixed, don't forget to apply the 'Permanent Fix' from that thread in order to save you the troubles later.

If you've got any queries, you can post in that thread as Wubi experts keep an eye on that one ;-)

Good Luck!

---

### Post by amjjawad on 2010-12-18
And if your problem is solved, please mention that here and mark this thread as "SOLVED" from Thread Tools for future reference ;)

---

### Post by prbugzdaman7 on 2010-12-18
Thanks,  so i don't have my windows recovery cd but in my situation I will got with the second solution provided by that link. when i run the command sudo lilo -M /dev/sd[COLOR=Red]a[/COLOR] mbr, where [COLOR=Red]a[/COLOR] is where my  Windows drive? Now once this is done can i restart my computer?

---

### Post by prbugzdaman7 on 2010-12-18
# sorry about not wrapping the text i'm still getting used to this

---

### Post by sikander3786 on 2010-12-18
> **prbugzdaman7 said:**
> Thanks,  so i don't have my windows recovery cd but in my situation I will got with the second solution provided by that link. when i run the command sudo lilo -M /dev/sd[COLOR=Red]a[/COLOR] mbr, where [COLOR=Red]a[/COLOR] is where my  Windows drive? Now once this is done can i restart my computer?
Yes reboot and see if you can boot Windows successfully now.

---

### Post by amjjawad on 2010-12-18
> **prbugzdaman7 said:**
> Thanks,  so i don't have my windows recovery cd but in my situation I will got with the second solution provided by that link. when i run the command sudo lilo -M /dev/sd[COLOR=Red]a[/COLOR] mbr, where [COLOR=Red]a[/COLOR] is where my  Windows drive? Now once this is done can i restart my computer?

sda is your HDD.
sda1, sda2, etc are partitions.

---

### Post by amjjawad on 2010-12-18
> **prbugzdaman7 said:**
> # sorry about not wrapping the text i'm still getting used to this

Too late for that now :D
Never mind ;)

---

### Post by prbugzdaman7 on 2010-12-18
# WOW you guys are awesome!!! It worked perfectly and i am up and running. thank you very much. ;) #

---

### Post by amjjawad on 2010-12-18
> **prbugzdaman7 said:**
> # WOW you guys are awesome!!! It worked perfectly and i am up and running. thank you very much. ;) #

HOOHAA, well done :)

---

