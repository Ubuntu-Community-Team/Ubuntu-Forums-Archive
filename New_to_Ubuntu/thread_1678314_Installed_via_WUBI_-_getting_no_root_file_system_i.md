---
title: "Installed via WUBI - getting no root file system is defined"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by PeeJay16 on 2011-01-30
Hi - I'm an absolute beginner on Linux but here goes.

I've installed using WUBI onto an XP machine. The machine has 2 hard discs. C is the windows drive and shows in partition wizard as active+system+boot. D shows as active. I elected to install on C with 30GB space.

Install seemed to go OK but when I re-booted it got as far as setting the time and then I received an error message 'No root file system is defined. Please correct this from the partitioning menu'

Looking in the forum I found a similar post with a link to this site as a solution

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Fired up the live CD and tried it but where the tutorial says to 'select the free space' I can only see the D: drive. I cannot select the C: drive at all. The panel doesn't show 'free space', only the 500gb disk (i.e. the totality of the D: drive) and the add button is greyed out.

Can anyone point me in the right direction to resolve this?

Thanks

Paul

---

### Post by Rubi1200 on 2011-01-30
Hi and welcome to the forums :-)

We need to get a better overview of your current setup.

To that end,

please use the LiveCD and download and run the boot info script linked at the bottom of my post (with instructions).

Post the results back here.

Thanks.

---

### Post by PeeJay16 on 2011-01-30
Thanks - here's the results

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/pdc_jcahibgbh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

pdc_jcahibgbh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

pdc_jcahibgbh2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     9,221,309     9,221,247  1c Hidden W95 FAT32 (LBA)
/dev/sdb2    *      9,221,310   398,283,479   389,062,170   7 HPFS/NTFS


Drive: pdc_jcahibgbh ___________________ _____________________________________________________

Disk /dev/mapper/pdc_jcahibgbh: 203.9 GB, 203928043520 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398296960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_jcahibgbh1                 63     9,221,309     9,221,247  1c Hidden W95 FAT32 (LBA)
/dev/mapper/pdc_jcahibgbh2   *      9,221,310   398,283,479   389,062,170   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_jcahibgbh1 A82A-F795                              vfat       RECOVERY                      
/dev/mapper/pdc_jcahibgbh2 01CBB1D56F9383C0                       ntfs       Windows                       
/dev/mapper/pdc_jcahibgbh: PTTYPE="dos" 
/dev/sda1        FE2074A820746A13                       ntfs       500GB disk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A82A-F795                              vfat       RECOVERY                      
/dev/sdb2        01CBB1D56F9383C0                       ntfs       Windows                       
/dev/sdb                                                promise_fasttrack_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== pdc_jcahibgbh1/boot.ini: ===========================

[boot loader] 
timeout=5 
default=c:\cmdcons\bootsect.dat 
[operating systems] 
c:\cmdcons\bootsect.dat="Microsoft XP Preinstall Environment" /cmdcons 

=========================== pdc_jcahibgbh2/menu.lst: ===========================

hiddenmenu  
timeout 0  
title openSUSE 11.3 installer (LOCAL)  
find --set-root /openSUSE_hitme.txt 
kernel /openSUSE/linux devfs=mount,dall ramdisk_size=65536  lang=en splash=silent vga=0x31A 
initrd /openSUSE/initrd 

=========================== pdc_jcahibgbh2/boot.ini: ===========================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

============== pdc_jcahibgbh2: Location of files loaded by Grub: ==============


    GPGB: menu.lst

---

### Post by Rubi1200 on 2011-01-31
I don't know what happened, but things are quite messy.

GRUB is installed but it isn't (pointing to a partition that appears not to exist); you have a RAID array, a failed mount on a partition; and a mix with GRUB-legacy from OpenSUSE.

I think the first thing you need to do is get Windows back up and running and then work from there:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
This link explains how to restore the Windows bootloader.

Once that is done, run the boot info script again and please tell us what you are trying to achieve so we can offer advice on how to proceed.

Thanks.

---

### Post by PeeJay16 on 2011-01-31
Thanks - I appreciate any help you can give me to sort this out. I've include another set of results as an attachment, however I'm almost certain I had windows back up and running before I posted so I don't think this one will show any difference.

What I'm trying to achieve.

Firstly a dual boot XP/Linux machine so I can try out Linux, see what it does and learn more about it, then if all goes well ditch XP and use Linux exclusively. Ideally I'd like to do the first part in a way that makes doing the second part easier, if possible.

Thanks again for your help

---

### Post by mastablasta on 2011-01-31
a good idea would be to read a bit about linux first - i suggets Ubuntu manual.
You will also find some very good tutorials on how to install linux in dual boot and on separate partition.
 
A better way to just tyr and fiddle arround with the system is to use liveUSB disk and make it persistant. But still nothing beats a hard disk install.

---

### Post by PeeJay16 on 2011-01-31
Thanks :p I'll download the manual and have a read, however from what Rubi1200 says about the state of my install at present I think I'll still need a lot of assitance to get Linux up and running!

---

### Post by oldfred on 2011-01-31
This and the mapper listing say you are running RAID. Are you?

/dev/sdb                                                promise_fasttrack_raid_member                               

Your drives do seem to be different sizes.

If you are not running RAID you will need to remove hidden settings on the drives, but if you have RAID you should not run this:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by PeeJay16 on 2011-01-31
My understanding of RAID is that it mirrors data across disks to avoid data loss in case of disc failure. In that case I'm not running raid.

The system has two discs. C is the internal hard drive (about 185GB) with windows and a recovery partition (not sure what this is as it was on from new and I don't think I've ever used it)

D: is an external hard drive, 500GB and should be all one partition. I say should because one failed Linux install created a partition on there that it appears it subsequently couldn't find, and I deleted the partition and re-sized the existing partition back up up to 500GB, however as I'm learning there might be a lot of things hiding on the disc somewhere!

---

### Post by PeeJay16 on 2011-01-31
I did a bit more digging around the system. The internal hard disc shows as PROMISE 1+0 Stripe/RAID0 SCSI disk device if that helps. I also remembered that just after checking the disc at startup the system issues a message to 'press ctrl-f to go into the fast build utility' I've had a quick look on google and it appears this is some kind of raid utility, which was there when the system was purchased - I've never used it and looking in the BIOS I can't see any obvious settings to turn it off. 

I was wondering if it's used to copy some windows data into the recovery partition on the C: drive?

---

### Post by Rubi1200 on 2011-01-31
Hi PeeJay16,
I am unable to help you as regards RAID, or whatever it is you have on the computer, but I am going to ask someone who knows more about this to have a look.

With timezone differences and all, please be patient.

---

### Post by ronparent on 2011-02-01
PeeJay16 - I am responding at Rubi1200's request that I have a look at your situation. It appears to me that your results.txt indicates that your external drive is id'd as sda and the internal drive is sdb. The sdb is identified as a raid member. But I don't think that is currently the case but is the results of residual meta data on the disk mucking things up.

You could check that the raid is turned off in bios (which is likely the case). The facts that only sdb is id'd as a raid member and that there is no indication of raid breakage is encouraging that no actual raid set is actually present (a valid raid set would be comprised of more than one disk). The next step would be to boot to a live cd and erase the raid meta data as Oldfred suggested from what in results.txt is identified as sdb (be careful that the right drive is designated - though no harm should occur if you try to erase nonexistant meta data). From Odfred the code in a terminal is 'sudo dmraid -E -r /dev/sdb'. You should now be able to view your system from the live cd without raid data mucking things up. 

It doesn't appear that you have Ubuntu currently installed? You should use >System >Administration >gparted To view your system without the raid meta data to verify what you have in the way of partitions on each of your two drives. In any case, if everything looks clean, you should now be able to install. Let us know if you still have problems. Meanwhile, I can't over emphasize, that if you currently have access to your data that you backupit up before proceeding.

---

### Post by Rubi1200 on 2011-02-01
First, thanks to ronparent for the great advice.

PeeJay16, when you have done this, and before attempting anything else, run the boot script again and post it here.

We can then help you further with setting things up the way you want.

Also, as ronparent said, make backups now!

---

### Post by PeeJay16 on 2011-02-01
All - thanks for your assistance - much appreciated.

I've been thinking about how to do this and I'm going to get a second external disk so I can copy stuff around for backup before I start making any changes. My other thought is that I can then (hopefully) install to the new external HDD and use that exclusively for Linux.

I'll need to get the drive etc and get to work. This means I'll probably not be posting for a few days but I'm not giving up so so thanks for your help and I'll re-post when I've got as far as suggested in this thread.

):P

---

### Post by PeeJay16 on 2011-02-05
******* Sorry - ignore this post. Windows wouldn't come up until I re-built the raid part of the C drive so I probably need to re-run the boot info script again **********

Hi - back again.

I've run the sudo command and attached the results.txt file in this post. I'm not sure if it's clean enough to start again? What I'd like to achieve is to install Linux alongside XP as a dual boot setup. Not too bothered whether the Linux setup goes on sda or sdb but as Windows is on /dev/sdb it probably makes sense to install it there?

---

### Post by oldfred on 2011-02-05
It looks like the RAID is gone. Does windows boot ok. Which drive is internal and/or external?
You show sda as the 500GB and sdb with windows as the 200Gb drive. Is one an IDE drive?

USB ports are slower than SATA or even PATA ports so performance is not quite as good with an external USB drive but it is very acceptable for most users.

Even though the script says the windows drive is sdb, Windows says it is in drive 0, so I assume you are booting sdb directly?

---

### Post by PeeJay16 on 2011-02-05
Apologies for the earlier post. I thought everything was OK but had problems when I tried to boot back into windows as the raid on the internal hard drive had disappeared and I couldn't get past the BIOS without re-creating it. 

I've found out how to disable RAID in the BIOS but if I do disable it windows won't come up, so if I need to disable it permanently I think I may need to reload windows - not the end of the world but I'd rather avoid doing it if possible. I don't think there are any technical issues with it it's just that I've done it a few times over recent weeks!

The enclosed results.txt is from a working system. 

sda is the internal drive. sda1 is a small recovery partition that appears to be controlled (if that's the right word) by the RAID setup. SDA2 is the main partition that includes windows.

sdb is an external 500GB disk. 

I'd probably put Ubuntu on sda by preference if possible

---

### Post by oldfred on 2011-02-05
I do not know enough about RAID to be helpful and your title of wubi will not get those who know about RAID to help. wubi & RAID are at opposite ends of the technology. RAID is more often servers and not so often on desktops.

---

### Post by PeeJay16 on 2011-02-06
Thanks for the suggestion oldfred. I'll leave this thread open for a day or so in case Rubi1200 or ronparent see it, and if not I'll close it and re-open with a different title

---

### Post by Steve Moss on 2011-02-07
Hi

I want to install Ubuntu alongside my existing Windows XP OS so I can switch between them

I am worried that I might lose the existing Windows OS if I don't do this correctly

I am using Wubi and am experiencing the same error message (no root file system is identified) however I think I only have one hard drive

I have already successfully installed using Wubi on my laptop running alongside Windows Vista

I repeated the process for my desktop running Windows XP and got the above error message when launching Ubuntu

I have tried following this thread but seem to have even less technical expertise in the areas of partitioning BIOS etc

Please can you make any instructions as detailed as possible

Thanking you in advance for your help

PS I include file with details of current configuration

---

### Post by PeeJay16 on 2011-02-07
Steve - I think it's probably better to start your own thread for this problem. I think we might confuse people if we start posting two sets of configuration data in the same thread. Also my problem isn't around Wubi anymore so I'll probably close this thread and start a new one around RAID and my specific configuration as the current thread title isn't relevant any more.

Might also be worth running this boot info script and posting the results in the thread to give the forum members some info on your system. Details of what to do are included on the page.

[Boot info script]("http://bootinfoscript.sourceforge.net/") courtesy of meierfra

I've found the people on here very helpful so I'm sure they will be able to help you out.

:p

---

### Post by Steve Moss on 2011-02-07
Ok

Thanks

Will do

---

### Post by PeeJay16 on 2011-02-09
I've marked this as closed as the issue is around my RAID configuration, so I'm openning a new thread around that topic

---

