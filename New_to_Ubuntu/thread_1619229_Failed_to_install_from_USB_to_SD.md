---
title: "Failed to install from USB to SD"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2010-11-11
Hi
I'm trying to install UNR 10.04 LTS on an EeeBox 1012 Barebone (without HDD).

I tried to install Ubuntu from a SD Card 2GB installed on an USB adapter, to an 8GB SD Card install in the media card reader.

The 2 GB SD Card is setup with Universal-USB-Installer-1.7.9.6.exe on Windows, and ISO file 10.04.1

Ubuntu Installer start correctly, ask options (times, keyboard) detect 8G SD Card, and I select installation on complete 8GB SD Card.

Installation go on until it ask to restart.  I remove USB SD Card, and wait system to restart on the 8GB SD Card, but doesn't boot.

I tried to install from external CD ROM and alway get same behavior.

Any idea to install Ubuntu from USB to SD Card ?

---

### Post by oldfred on 2010-11-11
Are you sure you did not install grub to you sda drive. Grub likes to default to sda unless told differently.

So you may not have grub in the 8GB card.

Plug everything in and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

To install grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Pierrot Lafouine on 2010-11-12
Thanks,
I have downloaded boot_info_sccript and ran it as specified in sourceforge pag.  I get this error :

Line 1: !DOCTYPE: no such file or directory

etc...

How can I fix this ?

---

### Post by oldfred on 2010-11-12
You have to run it from where ever you downloaded it to. LiveCD used to download to the  desktop, now I think they down load to Downloads. But the path has to be where ever it is at.

sudo bash /Downloads/boot_info_script055.sh

You can use tab as you start to type boot.. and it will complete the line.

---

### Post by Pierrot Lafouine on 2010-11-13
I downloaded with wget, in /home/xx/downloaded
I ran command in /home/xx/downloaded folder and got these error messages:

Line 1: !DOCTYPE: no such file or directory

What is this error about ?

---

### Post by Pierrot Lafouine on 2010-11-14
Ok, I read this is XML/HTML statement.
Can BASH run these command ?
Am I runing the good script ?

Thanks

---

### Post by oldfred on 2010-11-14
the boot info script is just a script, not related to any HTML.

run a 
ls boo*

and the command you are using to run it, after you type boot you can use tab to complete the line.
sudo bash boot_info_script055.sh

and post all of the screen like below

I copy my boot scripts to a different folder:
```
fred@fred-laptop:~/Documents/LinuxDocs/CurrentSys$ ls boo*
boot_info_script032.sh  boot_info_script042.sh  boot_info_script052.sh
boot_info_script034.sh  boot_info_script044.sh  boot_info_script053.sh
boot_info_script037.sh  boot_info_script047.sh  boot_info_script055.sh
boot_info_script039.sh  boot_info_script049.sh  boot_info_script055.sh~
boot_info_script041.sh  boot_info_script051.sh  boot_info_script05x.sh
fred@fred-laptop:~/Documents/LinuxDocs/CurrentSys$ sudo bash boot_info_script055.sh
[sudo] password for fred: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda4 for information... 
Searching sdb1 for information... 
Finished. The results are in the file RESULTS5.txt located in /home/fred
fred@fred-laptop:~/Documents/LinuxDocs/CurrentSys$ 

```

---

### Post by Pierrot Lafouine on 2010-11-14
Hi
This is the output of the 2 commands :

```

xx@TspEeeBoxLucyd:~$ cd downloaded/
xx@TspEeeBoxLucyd:~/downloaded$ ls boo*
boot_info_script055.sh
xx@TspEeeBoxLucyd:~/downloaded$ sudo bash boot_info_script055.sh 
[sudo] password for xx: 
boot_info_script055.sh: line 1: !DOCTYPE: No such file or directory
boot_info_script055.sh: line 2: syntax error near unexpected token `newline'
boot_info_script055.sh: line 2: `        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'
xx@TspEeeBoxLucyd:~/downloaded$ 

```

With vi, I have copied/pasted the content of the first 3 lines of boot_info_script055.sh :

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<!-- Create Server: sfs-web-3 -->

```

Look to me I don't have the good script file!!!
I will download it again

Thanks

---

### Post by Pierrot Lafouine on 2010-11-14
ok
I download the script again and the script worked.
This is the content of RESULT.txt:

```

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2028 MB, 2028994560 bytes
63 heads, 62 sectors/track, 1014 cylinders, total 3962880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             62     3,960,683     3,960,622   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8017 MB, 8017412096 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    14,884,863    14,882,816  83 Linux
/dev/sdb2          14,886,910    15,656,959       770,050   5 Extended
/dev/sdb5          14,886,912    15,656,959       770,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D06E-53A6                              vfat       PENDRIVE
/dev/sda: PTTYPE="dos"
/dev/sdb1        1873dbb4-86db-4311-9002-562f9bc7453d   ext4
/dev/sdb2: PTTYPE="dos"
/dev/sdb5        2b5b1b1c-c702-43ba-9220-9dc0911c29e8   swap
/dev/sdb: PTTYPE="dos"


```

So you are right, grub is installed on the wrong SD card.  How can I fix this ?  Any link ?

Thanks

---

### Post by oldfred on 2010-11-14
this is the full replace boot boot loaders but I so not know what you have or need in sda the 2GB flash drive.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If just installing grub to sdb:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Install MBR from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb1 if not correct, and/or even sdb if sda wanted:
sudo fdisk -l
#confirm that it is sdb1 
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

---

### Post by Pierrot Lafouine on 2010-11-15
Hi
I finally fixed the 8G SD Card with grub-install.
Thank you very much for your expert advices.

Cheers!

---

### Post by ReproMan on 2010-12-02
My equipment is the Intel DG965OT mainboard flashed with final Nov.2008 BIOS. Support is discontinued by Intel after Nov.2008.

This thread was helpful to narrow down the booting problem with 10.04.1 Ubuntu (and also 10.10 Ubuntu with syslinux problem within usb creator) so I decided to post my observations.

I would also suggest to the author of gdisk to add the information from this thread to their man page and please add a --help option to the command line of their program.

OBSERVATIONS:

I have a very simple MBR partition scheme that worked perfectly in 9.10 Ubuntu with both 1TB and 2TB hard disk:

/boot (EXT4 200MB)
/LVM (remainder of disk)

LVM holds an encrypted EXT4 partition and swap file.

What I discovered is that 10.04.1 alternate installer can produce bootable system but when I did the process manually (as done under 9.10) it would not boot.  

The only difference was my manually created boot partition was 200MB and the automatically created boot partition was 256MB.  I also tried many variations like EXT2 vs EXT4 or different LVM vs encrypted partition arrangement/order and finally found this strange quirk with the 200MB boot partition being too small.

Can anybody shed some light on why a 256MB boot partition will boot and 200MB partition will not boot under the new 10.04.1 Ubuntu?

Another quirk I noticed is the new 10.04.1 installer tries to write the MBR to the flash stick.  You have to tell installer where the hard drive is eg: answer NO then specify /dev/sdb.  The 9.10 installer puts the hard drive partitions first and ahead of the flash stick, so this was not a problem before.  

If the developers of the Ubuntu installer are reading this, there is definitely room for improving the installation heuristics of the 10.04 and higher installers.  From comments on other threads you are definitely losing some people by introducing show stopping quirks like these. 2 year old motherboards are still useful and should be supported properly without the excuses and pushback I read about "legacy".  What is legacy after all?  Isn't everything "legacy" eventually?  Please consider installer heuristic changes more carefully.  If it can't boot people will use something else and Ubuntu becomes less relevant as a result.

---

