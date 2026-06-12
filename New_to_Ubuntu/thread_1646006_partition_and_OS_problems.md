---
title: "partition and OS problems"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by marqueemark on 2010-12-15
First I would like to say that is my first post, I have been using this site, almost exclusively, to solve my problems with ubuntu, I find the people here are friendly and know what they are talking about.

A while ago I had a sudden problem with windows vista, I'm willing to bet that I downloaded a virus, but that's all sort of irrelevent.  So to try to fix windows I ran the restore and had it fail multiple times then tried a complete restore from the boot up menu, I tried this twice and it said it failed both times.  

In the meantime I had previously installed ubuntu 10.04 and so decided to use it instead, although it would be my first real experience with it.

It ran fine the first time I used it, but when I ran the update and then tried to reboot it the computer would not even show any OS's to boot up.  So I reinstalled off the disk I have and that went fine until the computer tried to restart.  During the shut down process the disk was ejected and there was an I/O error repeated on my screen hundreds of times and again could not boot to any OS on restart.

So I got another copy of 10.04 and installed it, this time it seemed to work, I still got an I/O error at the end of the install but it rebooted ok, and i have been using it ever since with very few problems, although synaptic PM has frozen a couple times and I have had to reboot to clear the problem.  Also on restart ubuntu never finishes shutting down, eventually i have to do it manually.

My main issue however at this point is that when the computer boots up to the OS selection screen I currently have 8 options to boot from , the screen looks as follows:

UBUNTU, WITH LINUX, 2.6.32 - GENERIC PAE
UBUNTU, WITH LINUX, 2.6.32 - GENERIC PAE RECOVERY MODE
MEMORY TEST (MEMTEST 86+)
MEMORY TEST (MEMTEST 86+ SERIAL CONSOLE 115200)
WINDOWS VISTA (LOADER) (on/dev/sda1)
WINDOWS VISTA (LOADER) (on/dev/sda2)
UBUNTU, WITH LINUX, 2.6.36 - GENERIC PAE (on/dev/sdh5)
UBUNTU, WITH LINUX, 2.6.36 - GENERIC PAE (RECOVERY MODE)(on/dev/sdh...

The last line is too long to see, but i assume ends in 6.  I have seem the partition manager in ubuntu and am wondering if i can  use this to clean this mess up?  But with the shutdown issue i'm also wondering if i should just fresh install.  At this point I only have access to 200Gb of a 1Tb HD.

Any suggestions would be appreciated

---

### Post by Hippytaff on 2010-12-15
Welcome to the forums :-)
 
It looks as though you have both a Wubi install and a 'real' partition. If you can get into windows you can uninstall Wubi in control panel -> add/remove programmes. It might be worth running the boot script and posting the results.txt to get a good look at the partitions, setup etc before advising you any further.
 
Boot script - [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by marqueemark on 2010-12-15
there was a time i could still get into windows and was reading threads suggesting the same thing in order to reinstall ubuntu, however i could not get the program manager to remove wubi, it kept saying it was removing it but it was always still there.  At this point I cannot boot into windows at all, if I select one of the windows options it boots to the screen it would go to if I held alt and pressed f10 repeatedly, where i can choose to do a fresh install on window, but it always fails.

---

### Post by marqueemark on 2010-12-15
Here are the results from the boot script:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdh
 => Syslinux is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdh2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdh3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdh5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdh6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,722,047    30,720,000  27 Hidden HPFS/NTFS
/dev/sda2    *     30,722,048   528,945,991   498,223,944   7 HPFS/NTFS
/dev/sda3         528,947,198   992,172,031   463,224,834   5 Extended
/dev/sda5         528,947,200   974,235,647   445,288,448  83 Linux
/dev/sda6         974,237,696   992,172,031    17,934,336  82 Linux swap / Solaris
/dev/sda4         992,172,032 1,953,521,663   961,349,632   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdh1              34       262,177       262,144 Microsoft Windows
/dev/sdh2         264,192       526,335       262,144 Microsoft Windows
/dev/sdh3         526,336 3,428,822,599 3,428,296,264 Linux or Data
/dev/sdh4   3,428,823,040 3,428,825,087         2,048 Linux or Data
/dev/sdh5   3,428,825,088 3,889,092,607   460,267,520 Linux or Data
/dev/sdh6   3,889,092,608 3,907,028,991    17,936,384 Linux Swap

Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 4278 MB, 4278190080 bytes
2 heads, 63 sectors/track, 66316 cylinders, total 8355840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1    *             64     8,355,839     8,355,776   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        58BCCEFDBCCED522                       ntfs       PQSERVICE                     
/dev/sda2        384AD4024AD3BB38                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        3E40114340110377                       ntfs       DATA                          
/dev/sda5        fe3640d1-7d79-4f62-9a3c-9e4f38d2b890   ext4                                     
/dev/sda6        7d8f03cf-ea0b-47fd-b90d-bd2c0a38122c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        18E82774E8274F76                       ntfs       LaCie                         
/dev/sdb: PTTYPE="dos" 
/dev/sdh3        705A6F045A6EC686                       ntfs       LaCie                         
/dev/sdh5        52a563e7-4a68-4bdb-be4e-16850244d563   ext4                                     
/dev/sdh6        2be8aaee-ff25-4edb-a749-187007d4c46e   swap                                     
/dev/sdh: PTTYPE="gpt" 
/dev/sdi1        9C02-2BDF                              vfat       PENDRIVE                      
/dev/sdi: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdi1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdh5        /media/52a563e7-4a68-4bdb-be4e-16850244d563 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/LaCie             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdh3        /media/LaCie_            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by srs5694 on 2010-12-15
Your /dev/sdh drive uses the GUID Partition Table (GPT), whereas your other drives use the Master Boot Record (MBR) system. This configuration can cause problems with at least some versions of GRUB, causing it to fail to boot Windows. There's a fairly easy solution, but I don't recall the details, offhand. I think it involves explicitly loading the GPT and/or MBR module in the GRUB configuration. I know that the user oldfred here has posted this solution several times; perhaps you can peruse his old posts, or if you're lucky, maybe he'll chime in with the details.

---

### Post by oldfred on 2010-12-15
They fixed the mixed gpt MBR(msdos) issues with the newer versions of grub.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

You did not post the entire boot script. I do not see the grub.cfg files to know what is booting. The script/grub also may not identify drive correctly so I am not sure if you are booting sda5 or sdh5??

Please add code tags and post the entire script.
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

If editing you previous post to manually add the code tags you have to type [ code] and [ /code] but without space. If I did not have space it would have converted to code tags and you would not have seen them.

---

### Post by marqueemark on 2011-01-09
I'm very sorry for the delay in continuing this thread.  It got so I could not boot into any OS, so I went without a computer for a while and have now installed kubuntu 10.10.  I have my whole terabyte HD back and am loving this OS.  I sincerely appreciate your guys' help and look forward to continued support from the kubuntu community, I hope they are all as great as you guys.  Cheers

---

