---
title: "Help restoring Grub2 after Win7 install"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by adobrakic on 2010-07-25
I'm following [this](http://ubuntuforums.org/showthread.php?t=1014708) guide to restoring the grub, and I get stuck at the following:

```
mint@mint ~ $ sudo mount /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

fdisk -l shows:

```
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce647

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25977   208659228+  83  Linux
/dev/sda2   *       25978       29164    25599577+   7  HPFS/NTFS
/dev/sda3           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris

```

So I did ```
sudo mkdir /media/sda5

``` with no problems. However, the next step is where it starts giving me trouble. Any suggestions?

---

### Post by SlidingHorn on 2010-07-25
This should get you moving in the right direction :)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by wilee-nilee on 2010-07-25
From the Live Ubuntu CD.
```
sudo mount /dev/sda1 /mnt
```
Then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Boot Ubuntu and in the terminal
```
sudo update-grub
```

Here is a grub2 link that defaults to the live cd grub2 reload.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by adobrakic on 2010-07-26
> **wilee-nilee said:**
> From the Live Ubuntu CD.
```
sudo mount /dev/sda1 /mnt
```


```
mint@mint ~ $ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mint@mint ~ $
```

---

### Post by wilee-nilee on 2010-07-26
Post the boot script in my sig in code tags.

---

### Post by adobrakic on 2010-07-26
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   417,320,504   417,318,457  83 Linux
/dev/sda2    *    417,320,505   468,519,659    51,199,155   7 HPFS/NTFS
/dev/sda3         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a94c09c8-f61a-4d68-bb04-6aa9211e2de5   ext4                                     
/dev/sda2        09722364381B2CE9                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5273e340-0c48-4580-b6ca-50576a886986   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /mnt/boot                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by jtarin on 2010-07-26
Let me ask this....why are you having to restore Grub? I notice your Linux is on the first partition beginning with sector 2,048 ?

---

### Post by adobrakic on 2010-07-26
I had Linux installed first, and then installed Windows 7. Now when I reboot, Windows 7 comes up by default. I'd like to have a choice between which OS turns on.

---

### Post by jtarin on 2010-07-26
Double Post. See below.

---

### Post by jtarin on 2010-07-26
> **adobrakic said:**
> I had Linux installed first, and then installed Windows 7. Now when I reboot, Windows 7 comes up by default. I'd like to have a choice between which OS turns on.
My advice, if you haven't got much invested in either OS at the moment is to is to reinstall Win7 to the first partition on the first disk then Ubuntu to its own partition. Then install Grub2 to the "/" directory of your Ubuntu install and not the MBR overwriting Win Loader. Then install EasyBCD 2.0 to boot Windows and Ubuntu.Easy BCD allows you to edit the Win7 loader to boot anything.I have been dual booting Windows,BSD and Linux for over 13 years and I have made the decision based on experience not to place Grub, BSD Loader or Lilo in the MBR.

---

### Post by wilee-nilee on 2010-07-26
> **adobrakic said:**
> I had Linux installed first, and then installed Windows 7. Now when I reboot, Windows 7 comes up by default. I'd like to have a choice between which OS turns on.

Your Ubuntu install appears to not be there in whole if you posted the whole boot script output.

What ever you did wiped out Ubuntu, if you didn't have a pre-formated partition for W7 this will happen.

Your problems here are not the bootloaders but a partially wiped setup, especially Ubuntu, no boot files, no kernels, no fstab....etc, and you have grub in the windows partition=sda2, but the windows files for booting are correct.

**sda2:** _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR="Red"]/grub/core.img[/COLOR]


It might be possible to clean this grub out with this link.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Then with W7 DVD restore the MBR to MS then delete and reinstall Ubuntu. This is the command highlighted from a W7 install dvd follow the http link for instructions to the command line in the DVD boot.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

The fixmbr will only work after removing grub from sda2 so do the testdisk run the boot script again to see if it's gone if so run the W7 install dvd and the BootRec.exe /fixmbr to reload the mbr. Then see if windows boots if so you can get Ubuntu deleted and reinstalled.

You can see if there is anything salvageable in Ubuntu from a Live Ubuntu cd by mounting the partition.

---

### Post by jarviser on 2010-07-26
> **jtarin said:**
> My advice, if you haven't got much invested in either OS at the moment is to is to reinstall Win7 to the first partition on the first disk then Ubuntu to its own partition. Then install Grub2 to the "/" directory of your Ubuntu install and not the MBR overwriting Win Loader. Then install EasyBCD 2.0 to boot Windows and Ubuntu.Easy BCD allows you to edit the Win7 loader to boot anything.I have been dual booting Windows,BSD and Linux for over 13 years and I have made the decision based on experience not to place Grub, BSD Loader or Lilo in the MBR.

+1  I agree entirely with jtarin. Start again with Win7 first then Ubuntu.  Your installation is all back to front.

 I would always install Win7 to an empty disk containing no partitions. Windows is the awkward SOB. Once that is in its own partition in first position (after the system reserved partition Win creates), you can install Ubuntu.

I am worried that you are running a fix without understanding - for example you are trying to copy commands like sudo mkdir /media/sda5 when sda5 in the article had completely different content to your install (which looks like Mint anyway??)

---

