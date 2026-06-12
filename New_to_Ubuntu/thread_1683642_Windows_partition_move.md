---
title: "Windows partition move"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Jason9 on 2011-02-07
I currently have 2 primary partitions, one containing windows xp and one containing windows 7. I'm ready to delete the xp partition, and want to move the windows 7 partition to the beginning of the drive so I can install ubuntu on another new partition, and make full use of the space I have. Can I use Gparted to safely move the partition to the beginning of the drive without messing up the Windows 7 bootloader?

---

### Post by Rhizoid on 2011-02-07
> **Jason9 said:**
> Can I use Gparted to **safely** move the partition to the beginning of the drive without messing up the Windows 7 bootloader?

I've done this with Vista and it worked ok, not tried it with 7. Image the drive and test that you can put it back the way it is now - best to to that to another drive to avoid possible problems - before doing a move/resize.

Why not simply remove the XP partition and use the space created for Ubuntu?

---

### Post by jonnny_j22 on 2011-02-07
i agree  with rhizoid, there is no reason you can't put ubuntu in place of the windows xp install, this will definatley protect your windows 7 bootloader.

but to answer your question,yes, in short. Either from the ubuntu live cd, or using the gparted live cd from here
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Just two points - firstly back up your data and double check the windows xp partition hasn't got anything you've forgotten about in it -If I had a penny for every time Ive deleted a partition then remembered something was in there!

Second do each step one by one - there are large amounts of data involved, so best not arrange it as you want then hit apply - i've had gparted errors before caused by asking it to do too many tasks.

okay if you want to cut xp, move 7 and then install ubuntu after... here we go...

Firstly delete the xp partition - this will only take a couple of seconds to apply

second move the windows 7 partition up to the start of the drive - this will take a very long time to apply probably hours, depending on the size of data and partition.

Third now is the time to create a data partition - as you said you only have the two partitions, this means that my documents and the like are on the same partition as your windows os. this is fine, but if you have to blank reinstall windows you automatically loose all the data on that partition and only have your backup - also if you set up another 'data' partition, you can mount it as /home (ubuntu's version of mydocuments).

The way I do this is to shrink the partition down, then create an extended partition in the free space. Into this create a 2GB logical partition formated as swap, another logical partition for your ubuntu (size of your choosing) formated as ext4, and format the rest as ntfs.

this will mean that you're set up now goes

[ntfs] [start extended{swap}{ext4}{ntfs}end extended]

This way you get it all in and ready to install ubuntu and you are only using 2 primary slots on your hard drive incase you want to install another windows, or bsd or whatever that uses another primary slot.

once you have it set up as you want, reboot and check your windows install for errors - if something has gone wrong and you need to do any reinstalling - mbr or operating system, doing this first means that the windows installer won't replace grub. (you can also move My Documents onto your new ntfs partition that will apear as a second hard drive in computer - most likely drive D)

Finally install ubuntu - you already have the partitions set up, so you just use the swap partition as swap, set ext4 partition as mountpoint / and the ntfs partition as mountpoint /home and install!

Job Done

---

### Post by Jason9 on 2011-02-07
To answer Rhyzoid, I don't currently have my whole drive formatted, and the slot that XP leaves is not where I want to install Ubuntu because it wouldn't be a very effective use of the space on my drive; I would have to move windows 7 anyways If I wanted to utilize all of the space on my drive, otherwise Ubuntu would have a way larger partition than it needs for just the system, leaving less space for my files. I think I'll end up doing what jonny says, sounds good.

---

### Post by presence1960 on 2011-02-07
You may want to be careful before you remove one of the windows installs. if you installed the second windows without removing the boot flag from the first install and placing onto the partition you were installing the second windows onto your boot files are combined. if you remove the windows that contains your boot files, the other version of windows will not be bootable. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Jason9 on 2011-02-08
Just providing more info, I installed XP first, and when I boot it appears it boots straight to the win7 loader, but it might be chainloading through XP..

although you probably can tell that from this: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,857,600   167,772,159    62,914,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FA4CBFEC4CBFA1B5                       ntfs                                     
/dev/sda2        78D8A52AD8A4E798                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
```

---

### Post by presence1960 on 2011-02-08
> **Jason9 said:**
> Just providing more info, I installed XP first, and when I boot it appears it boots straight to the win7 loader, but it might be chainloading through XP..

although you probably can tell that from this: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,857,600   167,772,159    62,914,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FA4CBFEC4CBFA1B5                       ntfs                                     
/dev/sda2        78D8A52AD8A4E798                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
```

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini [COLOR="Red"]/bootmgr /Boot/BCD[/COLOR] /ntldr /NTDETECT.COM

```

It is a good thing you did not remove XP since your windows 7 boot files in red above are on the XP partition.

You may want to see [here]("http://support.microsoft.com/kb/927392") for ways to fix windows 7 boot process.

---

### Post by Jason9 on 2011-02-08
First I tried using the startup repair utility, didn't do anything/ said there were no errors
Then I used the recovery console to run these:
```
BootRec.exe /FixBoot
BootRec.exe /FixMbr
BootRec.exe /RebuildBcd
```looks like it gave the same results file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,857,600   167,772,159    62,914,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FA4CBFEC4CBFA1B5                       ntfs                                     
/dev/sda2        78D8A52AD8A4E798                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
```What should I do?
Delete XP *then* run these maybe?

---

### Post by Rhizoid on 2011-02-08
The first thing you should do, if you haven't already is image the drive with something like Acronis (paid for) or Ping3 (Open Source) in case you do something you can't recover from ;)

---

### Post by Jason9 on 2011-02-08
Already done, Rhizoid.

---

