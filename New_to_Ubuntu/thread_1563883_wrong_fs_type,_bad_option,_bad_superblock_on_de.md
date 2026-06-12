---
title: "wrong fs type, bad option, bad superblock on /de"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by grewolf on 2010-08-29
I am trying to reinstall grub onto an existing ubuntu hard disk drive.  I have another drive that had windows on it and used the install disk to try and repair the mbr.  I used the windows fixmbr on my ubuntu hard drive in error and now need to install grub again.  I am using the live CD and following the instructions 

```
sudo grub
root (hd0,0)
setup (hd0)
exit
```

When I enter ```
sudo grub
``` I get "Probing devices to guess BIOS drives.  This may take a long time."  When I typ ```
setup (hd0)
``` I get ```
Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no
Error 15: File not found
``` I then tried ```
sudo mkdir /mnt/root
``` and get the terminal prompt I type ```
sudo mount -t ext3 /dev/sda2 /mnt/root
``` and get ```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```



Can I reinstall Grub?

---

### Post by ibuclaw on 2010-08-29
Firstly, ensure you are trying to mount the correct filesystem using the correct type. Information can be obtained from using:
```
sudo blkid
```
If it still gives you that error, use gparted (System->Administration->Partition Manager) to check the filesystem for errors (and fix where possible).

Secondly, make sure you are setting the root partition correctly in GRUB. You can use
```
find /boot/grub/stage1
```
and the correct (device,partition) numbers should be outputted.

Regards

---

### Post by oldfred on 2010-08-29
You may need to run the filecheck on that partition.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

You can also post all the boot info on your system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Are you still running 7.10. Not sure all commands are there or not. Script will list missing commands if any.

---

### Post by grewolf on 2010-08-29
> **ibuclaw said:**
> Firstly, ensure you are trying to mount the correct filesystem using the correct type. Information can be obtained from using:
```
sudo blkid
```

Output of command
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="283a1431-60c0-4344-82db-4ae3d4cbeb97" TYPE="swap" 
/dev/sdb1: UUID="5EECD00BECCFDC01" TYPE="ntfs"
```


If it still gives you that error, use gparted (System->Administration->Partition Manager) to check the filesystem for errors (and fix where possible).

Secondly, make sure you are setting the root partition correctly in GRUB. You can use
```
find /boot/grub/stage1
```

Output of Command
```
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
ubuntu@ubuntu:~$ 
```





Regards





I have entered the info from the commands that you gave me up in your message.  It looks like I only have the device sda5 which is the swap partition.  I went to gparted and opened it up and it shows me 3 partitions I have /dev/sda2 which is the extended file system and I have /dev/sda5 which is the linux-swap file system and I have the /dev/sda1 which is the ext4 files system.  

Under flags for sda1 it has boot listed.  Is there any way I can use Gparted to fix this?

When I click on device information in Gparted for sda1 it shows partition table: msdos.

---

### Post by grewolf on 2010-08-29
I have used the boot info script.  here are the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,932,346,394 1,932,346,332  83 Linux
/dev/sda2       1,932,346,395 1,953,520,064    21,173,670   5 Extended
/dev/sda5       1,932,346,458 1,953,520,064    21,173,607  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2: PTTYPE="dos" 
/dev/sda5        283a1431-60c0-4344-82db-4ae3d4cbeb97   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5EECD00BECCFDC01                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
```

---

### Post by ibuclaw on 2010-08-30
> **grewolf said:**
> 
Output of Command
```
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
ubuntu@ubuntu:~$ 
```

Your meant to run that through the grub prompt, not the shell. ;)

Anyhow, it looks like sda1 has been hosed from here...

Your next option would be to see if testdisk can restore the partition table for sda to it's previous state before Window's fixmbr tinkered with it...

---

### Post by oldfred on 2010-08-30
Since you have two 1000GB drives, were they ever in RAID? That can cause some drive confusion as meta data gets saved in the drive.

---

### Post by grewolf on 2010-08-30
I am not running raid.  I have looked at your suggestion for test disk.  Does anyone know which partition table type I use.  Here are my choices
I also went to this page and like GNU parted but don't know what to put as my start and finish sectors.  

[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")


```
Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

```

---

### Post by oldfred on 2010-08-31
For most it is intel which really is msdos or MBR partitions.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by grewolf on 2010-08-31
I think I understand a little bit better now.  I don't have a missing partition.  I replaced grub or the boot loader for my ubuntu lucid lynx drive with the windows mbr by mistake.  What I want to do is to put grub or the boot loader back on to my Ubuntu lucid lynx drive which is sda1 and has listed 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

```

Is what I want to do possible?

---

### Post by grewolf on 2010-08-31
ibuclaw and oldfred thank you for all the links.  I have read though the link to herman's testdisk and it looks like it might work but I'm kind of nervous as it looks like  I could really damage things too.  While looking through some of the other links I found [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/") and want to try rescatux it looks like it might be safer.  What do you think?

---

### Post by oldfred on 2010-08-31
If you just want to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Is system seeing Ubuntu in sda1 or sdb1. I would install grub to the same drive and then in BIOS make sure you are booting that drive. I have two identical 160GB drives and in BIOS cannot easily tell them apart so sometimes I just have to try booting one and if it does not work boot the other.

---

### Post by grewolf on 2010-08-31
Thanks again oldfred.  I have tried to follow the instructions but it won't let me mount sda.  It says I should specify the file type

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type
```

I have tried to attach a screen capture of gparted.  It shows my swap and extended and ext4 partitions for sda.  

This is what I did to device sda in error 

```
How to restore the Windows XP bootloader

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

Code:

fixboot

Code:

fixmbr

Then type
Code:

exit

then remove your XP cd. If everything has gone well, you should come to your XP bootloader.
```

I should have done this to device sdb.  

Now it won't let me mount device sda or install grub on it.

---

### Post by grewolf on 2010-08-31
I have used test disk to list my partitions here is the output.  

```
ubuntu@ubuntu:~$ sudo testdisk /list
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512
Disk /dev/sr0 - 718 MB / 685 MiB - CHS 351010 1 1 (RO), sector size=2048

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition			Start        End    Size in sectors
 1 * Linux                    0   1  1 120282 254 63 1932346332
 2 E extended LBA         120283   0  1 121600 254 63   21173670
 5 L Linux Swap           120283   1  1 121600 254 63   21173607
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition			Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 60799 254 63  976751937
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition			Start        End    Size in sectors

Partition sector doesn't have the endmark 0xAA55
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition			Start        End    Size in sectors
 1 * Linux                    1   0  1 121600 254 63 1953504000 [storage-space]
Disk /dev/sr0 - 718 MB / 685 MiB - CHS 351010 1 1 (RO)
     Partition			Start        End    Size in sectors

Partition sector doesn't have the endmark 0xAA55

```

---

### Post by oldfred on 2010-08-31
When booting from the liveCD is it seeing the 500GB drive first with its partition being NTFS? Normally we do not have an issue mounting the ext partition for Ubuntu. Or perhaps from running teskdisk it was still mounted somewhere else and then will not let you mount it again? First try starting over.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda


There are several ways to reinstall if the quick two line one does not work there is the full chroot version.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

See methods two or three:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by grewolf on 2010-09-06
Thanks oldfred,  I'm sorry it took so long for my response but I had to leave out of town for work.

It is not seeing the NTFS drive first.  I have been off the computer now for a while and have not used test disk.  Just to clarify you want me to install ubuntu on sda5 is that correct?  If this is so once I have installed ubuntu on sda5 you want me to follow the commands you have listed

---

### Post by grewolf on 2010-09-06
I have used this and it seems it might have worked not sure though.  I will try and reboot

```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo touch /mnt/empty_file
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
Installation finished. No error reported.
```

From bug 518582




Cure:

Boot from the Ubuntu LiveCD and create a file on the affected partition:

```
sudo mount /dev/sda1 /mnt
sudo touch /mnt/empty_file
```

---

### Post by oldfred on 2010-09-06
I do not think you can reinstall grub until you have fixed sda1 which is your Ubuntu install.

Have you run thru the entire testdisk procedure?

---

### Post by grewolf on 2010-10-16
Thank you oldfred I think this is what finally worked for me the last link you gave me I followed those instructions and was able to boot into my system again.


> **oldfred said:**
> If you just want to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Is system seeing Ubuntu in sda1 or sdb1. I would install grub to the same drive and then in BIOS make sure you are booting that drive. I have two identical 160GB drives and in BIOS cannot easily tell them apart so sometimes I just have to try booting one and if it does not work boot the other.

---

