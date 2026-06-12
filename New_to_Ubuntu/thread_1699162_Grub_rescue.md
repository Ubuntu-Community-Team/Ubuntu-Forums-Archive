---
title: "Grub rescue???"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Alexd4 on 2011-03-03
I've accidently deleted the bootloader on mu Dell XPS which has been running Ubuntu 10.10 qquite happily until I pressed the DEll Media Direct button, which must have a diffirent bios.

I followed the tutorial to re-install it, but when I run the show disk command the only Linux one is Linux "Swap/Solaris".

When I run the mount command for this (sda5) I get the error message

> can't find /dev/sda5/media/sda5 in /etc/fstab or /etc/mtab

Does anybody know what might be amiss? Though my computer is aging Linux had really revitalised it, can't believe how silly I was to press that button. Thanks for you help

---

### Post by howefield on 2011-03-03
Hi and welcome to the forum,

Post moved to its own thread.

You are more likely to get help this way, than hijacking someone else thread.

---

### Post by Rubi1200 on 2011-03-03
> **Alexd4 said:**
> I've accidently deleted the bootloader on mu Dell XPS which has been running Ubuntu 10.10 qquite happily until I pressed the DEll Media Direct button, which must have a diffirent bios.

I followed the tutorial to re-install it, but when I run the show disk command the only Linux one is Linux "Swap/Solaris".

When I run the mount command for this (sda5) I get the error message



Does anybody know what might be amiss? Though my computer is aging Linux had really revitalised it, can't believe how silly I was to press that button. Thanks for you help
Please post the results of the boot info script so we can help you.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Alexd4 on 2011-03-04
Thanks for both of your help and guidance! Here are the results of the boot info script test:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'swsuspend'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    220,508,253   224,701,154     4,192,902   c W95 FAT32 (LBA)
/dev/sda2         228,302,846   234,440,703     6,137,858   5 Extended
/dev/sda5         228,302,848   234,440,703     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D7-0108                              vfat       MEDIADIRECT                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c20a2c10-af25-4080-a435-72ecffd87670   swsuspend                                
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/MEDIADIRECT       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b1 38 f5 75 3a 76 fa ad  82 af 2f 5a b1 5d dd 03  |.8.u:v..../Z.]..|
00000010  bb 24 3c e0 49 d0 aa 5e  51 3a 00 c5 a3 7b 74 f1  |.$<.I..^Q:...{t.|
00000020  d4 7d 9d 6f 48 66 0e 4f  c6 ae f4 0e f5 d1 43 cb  |.}.oHf.O......C.|
00000030  e9 e5 3a e9 e8 79 2f 28  b6 5a 3a cc c1 79 30 b2  |..:..y/(.Z:..y0.|
00000040  d3 60 06 c3 cc bd 1e e9  c5 dd ce 8b 26 63 d5 3b  |.`..........&c.;|
00000050  d8 03 4e 90 fa 64 93 a9  2d 88 59 9a be 96 b8 c9  |..N..d..-.Y.....|
00000060  a2 90 81 cb eb 75 f0 19  c2 06 55 8b 5a b8 ee c1  |.....u....U.Z...|
00000070  e0 84 a0 0d 0f 13 17 53  e4 a2 cb d8 55 7b 8d 70  |.......S....U{.p|
00000080  75 c5 6b 80 45 34 8d ba  b2 53 fc b6 89 98 d3 31  |u.k.E4...S.....1|
00000090  a4 ba e6 b8 38 d4 11 c3  aa df a1 af 5e 3b 75 0c  |....8.......^;u.|
000000a0  9e 8a 76 9d a1 d0 b2 92  78 80 24 44 bf 0d 63 38  |..v.....x.$D..c8|
000000b0  9f 05 62 d2 34 b6 d6 19  cf a7 a9 99 12 46 84 7c  |..b.4........F.||
000000c0  9a 0b a4 1c 48 43 32 76  fa 42 75 a3 ee 94 b8 db  |....HC2v.Bu.....|
000000d0  08 32 21 d0 a7 23 30 a1  9c 07 5a c8 70 6d 03 92  |.2!..#0...Z.pm..|
000000e0  4e 03 2d 11 cd 99 52 fc  26 b2 92 84 59 39 41 59  |N.-...R.&...Y9AY|
000000f0  6c b9 3d c9 f7 d2 89 ae  d7 3c f4 e8 aa fa 8b 36  |l.=......<.....6|
00000100  76 fb 5b 06 57 72 f3 79  cb 79 24 c2 01 8a 4f 2a  |v.[.Wr.y.y$...O*|
00000110  ec 5d 85 e6 72 28 98 8b  2d aa cb d2 ac a5 0f c4  |.]..r(..-.......|
00000120  9f 9e 03 05 4f e0 b2 1b  01 83 cb 72 7b d0 ba 0b  |....O......r{...|
00000130  68 14 85 54 0f 68 f5 00  49 7e ae 8f be ab 81 a9  |h..T.h..I~......|
00000140  1e 66 8f 47 9a 3f 7d 8b  16 ae 30 9d eb b6 6f 55  |.f.G.?}...0...oU|
00000150  a8 b2 c4 65 06 c4 94 26  9c f8 b0 86 db ea cc 47  |...e...&.......G|
00000160  04 43 a7 74 3d fe 00 7e  85 1b c2 9a 97 cb d0 ed  |.C.t=..~........|
00000170  db 8f 6a fc 7c fd 05 22  f2 3d a3 09 38 cb 8d e2  |..j.|..".=..8...|
00000180  ae 3c 4c 35 b5 0c 05 08  55 bd d6 cf e6 39 34 28  |.<L5....U....94(|
00000190  a0 de 2d d5 35 48 d7 76  d6 f8 f1 fe ec 39 15 ce  |..-.5H.v.....9..|
000001a0  2d 1d fa 34 7d dd 89 92  44 a5 6d 10 e0 33 07 09  |-..4}...D.m..3..|
000001b0  7d cf fa 5f fd 49 df 7d  f5 32 33 c7 10 77 00 fe  |}.._.I.}.23..w..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by Rubi1200 on 2011-03-04
Well, I must admit I have never seen something like this before:

> mount: unknown filesystem type 'swsuspend'

I assume your Ubuntu install was on sda5?

But why does GRUB point to sda1?

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1

Can you give us some more background information please on how you originally installed Ubuntu and what exact steps you took afterwards:

> I followed the tutorial to re-install it

Please provide a link if possible to the tutorial.

Any other information you consider relevant should also be posted.

Thanks.

---

### Post by Alexd4 on 2011-03-04
Thanks for your interest, I am unhappy to know I'm an outlier!

I installed Ubuntu 10.10 from CD a few months back on a Dell XPS M1210 (info [here]("http://www.notebookreview.com/default.asp?newsID=2965") and [here]("http://support.dell.com/support/edocs/systems/xpsm1210/en/SM/index.htm")). Since the hardware was aging a little, and I had no particular love or need for Windows XP, I did a a complete install to ubuntu and wiped the partition which had been there.  No problems with it until now.

As I mentioned before, the Dell machine had a Dell/Windows home media set-up. Beside the power button there is another button "Dell Media Direct" which boots the machine directly to a home entertainment set-up (sort of like Mythubuntu). This must have had its own boot process because it wasn't running the full operating system and booted very fast. I'm also presuming it was deleted with my ubuntu install. The problem started when I accidently pressed the remaining "MediaDirect" button which now has no software behind it. I guess the grub has re-directed to that. 

I followed [these instructions to re-install it ]("http://ubuntuforums.org/showthread.php?t=1014708&highlight=Grub+rescue+tutorial")([http://ubuntuforums.org/showthread.php?t=1014708&highlight=Grub+rescue+tutorial](http://ubuntuforums.org/showthread.php?t=1014708&highlight=Grub+rescue+tutorial)), but got the error message below.


I hope this info helps, please take all of my suppositions with a pinch of salt as I'm a layman and thanks again

---

### Post by Rubi1200 on 2011-03-04
If I understand your post correctly, you overwrote the Windows partition with Ubuntu?

In other words, as far as you were concerned Windows was no longer on the computer, right?

I suggest you give Testdisk a run and see if it can find and restore your Ubuntu partitions:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You should run this from a LiveCD.

Boot with the CD, go to the terminal and run:

```
sudo apt-get update && sudo apt-get install testdisk
```

After installation:
```
sudo testdisk
``` to start and then use the guide above to try and find what appears to have been lost.

If at any point you are unsure, post back here and ask before moving ahead.

---

### Post by Alexd4 on 2011-03-05
Hi again,

Yes I completely deleted windows, I declined the chance to keep a partition. 

I'm continually getting the following error message;

> ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk


except this one once
:> ubuntu@ubuntu:~$ sudo apt-get install testdisk
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


when I exited the program and tried again i again was told to was not located. Is there some problem with the repository?

thanks

---

### Post by Rubi1200 on 2011-03-05
On the LiveCD, go to System > Administration > Synaptic > Repositories and put a check-mark next to universe and multiverse if not already enabled and then try to install again (after closing Synaptic).

edit: I meant Repositories > Software Sources

---

### Post by Alexd4 on 2011-03-05
I've already checked this, it was allowed as the default but am unfortunately getting the same message.
> ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
  I am running ubuntu 10.10 from the CD so I can't think how my set-up would be different from others.

I've also tried downloading it from [here]("http://www.cgsecurity.org/wiki/TestDisk_Download"), and extracting the files, but there is no .exe. I ran the command in terminal;
> ubuntu@ubuntu:~$ sudo testdisk-6.9/linux/testdisk_static
sudo: testdisk-6.9/linux/testdisk_static: command not found


I feel I have angered the partition god...

---

### Post by Rubi1200 on 2011-03-05
Did you try running sudo apt-get upgrade before the command to install testdisk?

If the repositories are enabled, I see no reason why this would not work.

---

### Post by Alexd4 on 2011-03-06
So i got it to work in the end. Here are the results of the testdisk search:

> Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
P HPFS - NTFS             11   0  1 13724 254 63  220315410
L FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
P FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

Yes i had intended to completely remove Windows from the system, but as suspected the mediadirect appears to have remained. The primary bootloader seems to have been changed to that when I pressed that button on the hardware. Does this sound correct?

Should I change the primary bootable to one of the other primary drives.  just to recap i am getting the error message "Unknown filesystem, grub rescue" on booting.

Sorry about earlier fretting with the install

---

### Post by Rubi1200 on 2011-03-06
Hi Alexd4,
here's the problem: I was hoping that Testdisk would find and restore your Ubuntu install.

Instead, it appears to have found your old Windows partitions. Unless you want Windows back, I am not sure this will help you.

Did you try the Deeper Search option or just the Quick Search?

Also, just for the record, I am not an expert on Testdisk. I know other users have employed it to successfully restore lost data and partitions. Therefore, I am wary of answering your question and suggesting what you should do next other than to try the Deeper Search option.

In the meantime, I will send a message to some other users who may have different perspectives to offer on your current situation.

Please hang in there as I would not like you to lose an opportunity to recover your data.

---

### Post by Alexd4 on 2011-03-06
Hi Rubi,

That was just the quick search. Preliminary results of the deeper search are showing a linux result;

> FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
  Linux                    0  32 33 14211  17 14  228298752
  HPFS - NTFS             11   0  1 13724 254 63  220315410



I'll post the full results when the search is finished.

---

### Post by Rubi1200 on 2011-03-06
Okay, that is good news. I have to go out now, but will check back in on the thread in about an hour or so.

Post the results of the deeper search once you have them.

Thanks.

---

### Post by Alexd4 on 2011-03-06
Rubi, thanks for your continued help and patience, I really appreciate it. The deeper search definitely showed some linux results, but alas I skipped ahead by accident while trying to copy-paste them. 

I got this summary of the drive size afterward;

> Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63, sector size=512Here's the full results from the log file, apologies for the length of the post, I hope you can make better sense of this than I can!

> 

Sun Mar  6 15:17:43 2011
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.35-22-generic (#33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.12, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       234441648 sectors
/dev/sda: user_max   234441648 sectors
/dev/sda: native_max 234441648 sectors
/dev/sda: dco        234441648 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63, sector size=512 - ATA SAMSUNG HM120JI
Disk /dev/sr0 - 726 MB / 693 MiB - CHS 354896 1 1 (RO), sector size=2048 - PHILIPS DVD+-RW SDVD8820

Partition table type (auto): Intel
Disk /dev/sda - 120 GB / 111 GiB - ATA SAMSUNG HM120JI
Partition table type: Intel

Analyse Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Geometry from i386 MBR: head=255 sector=63
FAT32 at 13726/1/1
Info: size boot_sector 4192902, partition 4192902
FAT1 : 32-4124
FAT2 : 4125-8217
start_rootdir : 8218 root cluster : 2
Data : 8218-4192897
sectors : 4192902
cluster_size : 8
no_of_cluster : 523085 (2 - 523086)
fat_length 4093 calculated 4087
check_part_i386 failed for partition type 82
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
 2 E extended             14211  49 45 14593  66  1    6137858
 5 L Linux Swap           14211  49 47 14593  66  1    6137856
 5 L Linux Swap           14211  49 47 14593  66  1    6137856
Computes LBA from CHS for Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
FAT16 at 0/1/1
FAT1 : 1-173
FAT2 : 174-346
start_rootdir : 347
Data : 379-176650
sectors : 176652
cluster_size : 4
no_of_cluster : 44068 (2 - 44069)
fat_length 173 calculated 173

FAT16 at 0/1/1
     FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
     FAT16, 90 MB / 86 MiB
NTFS at 11/0/1
filesystem size           220315410
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             11   0  1 13724 254 63  220315410
     NTFS, 112 GB / 105 GiB
FAT32 at 13726/1/1
FAT1 : 32-4124
FAT2 : 4125-8217
start_rootdir : 8218 root cluster : 2
Data : 8218-4192897
sectors : 4192902
cluster_size : 8
no_of_cluster : 523085 (2 - 523086)
fat_length 4093 calculated 4087

FAT32 at 13726/1/1
     FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
     FAT32, 2146 MB / 2047 MiB
FAT32 at 13987/0/1
FAT1 : 32-9526
FAT2 : 9527-19021
start_rootdir : 19022 root cluster : 2
Data : 19022-9735389
sectors : 9735390
cluster_size : 8
no_of_cluster : 1214546 (2 - 1214547)
fat_length 9495 calculated 9489
set_FAT_info: name from BS used

FAT32 at 13987/0/1
     FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]
     FAT32, 4984 MB / 4753 MiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
   * FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
     FAT16, 90 MB / 86 MiB
   P HPFS - NTFS             11   0  1 13724 254 63  220315410
     NTFS, 112 GB / 105 GiB
   L FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
     FAT32, 2146 MB / 2047 MiB
   P FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]
     FAT32, 4984 MB / 4753 MiB


dir_partition inode=0
   * FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
     FAT16, 90 MB / 86 MiB
Directory /
       2 -r-xr-xr-x     0      0     53569 22-Jun-2005 00:54 command.com
      29 -r-xr-xr-x     0      0     29690 26-Jul-2005 00:48 DELLBIO.BIN
      44 -r-xr-xr-x     0      0     33352 22-Jun-2005 00:54 DELLRMK.BIN
      61 -rwxr-xr-x     0      0        49  5-Jan-2000 20:32 CONFIG.BTS
      62 drwxr-xr-x     0      0         0  8-Jan-2007 09:50 DELL
   39541 -rwxr-xr-x     0      0       813  8-Oct-2006 05:13 DIR.LST
      74 -rwxr-xr-x     0      0     50393 13-Dec-2005 06:05 SEAL.EXE
      70 -rwxr-xr-x     0      0        77  8-Oct-2006 05:13 config.sys
   41439 -rwxr-xr-x     0      0     10802 26-Jan-2007 08:49 SEAL.INI
   37984 -rwxr-xr-x     0      0    325139  8-Oct-2006 05:13 Adaptec.mdm
   38143 -rwxr-xr-x     0      0    316659  8-Oct-2006 05:13 Adaptec2.mdm
   38298 -rwxr-xr-x     0      0     48155  8-Oct-2006 05:13 ami_raid.mdm
   38322 -rwxr-xr-x     0      0       241  8-Oct-2006 05:13 AUTOEXEC.UP
   38323 -rwxr-xr-x     0      0     18955  8-Oct-2006 05:13 BiosMp.mdm
   38333 -rwxr-xr-x     0      0    203266  8-Oct-2006 05:13 CABLES.mdm
   38433 -rwxr-xr-x     0      0     52711  8-Oct-2006 05:13 Cache.mdm
   38459 -rwxr-xr-x     0      0        77  8-Oct-2006 05:13 CONFIG.UP
   38460 -rwxr-xr-x     0      0        85  8-Oct-2006 05:13 COPYUP.BAT
   38461 -rwxr-xr-x     0      0     33578  8-Oct-2006 05:13 Cpu.mdm
   38478 -rwxr-xr-x     0      0      4419  8-Oct-2006 05:13 DDInit.mim
   38481 -rwxr-xr-x     0      0      1814  8-Oct-2006 05:13 DDINIT.MLM
   38482 -rwxr-xr-x     0      0      2635  8-Oct-2006 05:13 Dellboot.exe
   38484 -rwxr-xr-x     0      0     10321  8-Oct-2006 05:13 DELLDIAG.COM
   38490 -rwxr-xr-x     0      0   1201923  8-Oct-2006 05:13 DELLDIAG.EXE
   39077 -rwxr-xr-x     0      0       319  8-Oct-2006 05:13 DellDiag.INI
   39078 -rwxr-xr-x     0      0     83479  8-Oct-2006 05:13 DellSys.msm
   39119 -rwxr-xr-x     0      0    863731  8-Oct-2006 05:13 DELLTBUI.EXE
   39542 -rwxr-xr-x     0      0    259563  8-Oct-2006 05:13 Disk.mdm
   39669 -rwxr-xr-x     0      0     62772  8-Oct-2006 05:13 Diskette.mdm
   39700 -rwxr-xr-x     0      0     18946  8-Oct-2006 05:13 Dvd.mdm
   39710 -rwxr-xr-x     0      0    186829  8-Oct-2006 05:13 GenAudio.mdm
   39802 -rwxr-xr-x     0      0     78003  8-Oct-2006 05:13 HDAudio.mdm
   39841 -rwxr-xr-x     0      0    106367  8-Oct-2006 05:13 Iaudio.mdm
   39893 -rwxr-xr-x     0      0     28655  8-Oct-2006 05:13 IEEE1394.mdm
   39907 -rwxr-xr-x     0      0     38980  8-Oct-2006 05:13 IMchEcc.mdm
   39927 -rwxr-xr-x     0      0       900  8-Oct-2006 05:13 INT15_88.COM
   39928 -rwxr-xr-x     0      0     50830  8-Oct-2006 05:13 IoApic.mdm
   39953 -rwxr-xr-x     0      0     62438  8-Oct-2006 05:13 IR.mdm
   39984 -rwxr-xr-x     0      0    199019  8-Oct-2006 05:13 Keyboard.mdm
   40082 -rwxr-xr-x     0      0     90839  8-Oct-2006 05:13 LSI.mdm
   40127 -rwxr-xr-x     0      0    125117  8-Oct-2006 05:13 Memory.mdm
   40189 -rwxr-xr-x     0      0     41523  8-Oct-2006 05:13 MiscPci.mdm
   40210 -rwxr-xr-x     0      0     77101  8-Oct-2006 05:13 Mouse.mdm
   40248 -rwxr-xr-x     0      0     57342  8-Oct-2006 05:13 MpCache.mdm
   40276 -rwxr-xr-x     0      0    104432  8-Oct-2006 05:13 mpmemory.exe
   40327 -rwxr-xr-x     0      0     42936  8-Oct-2006 05:13 NbBatt.MDM
   40348 -rwxr-xr-x     0      0     33316  8-Oct-2006 05:13 Nbfan.MDM
   40365 -rwxr-xr-x     0      0     70808  8-Oct-2006 05:13 NbSvc.MDM
   40400 -rwxr-xr-x     0      0     48212  8-Oct-2006 05:13 Nbtherm.MDM
   40424 -rwxr-xr-x     0      0    239232  8-Oct-2006 05:13 Nic.mdm
   40541 -rwxr-xr-x     0      0     83515  8-Oct-2006 05:13 nic8254x.MDM
   40582 -rwxr-xr-x     0      0     47741  8-Oct-2006 05:13 Parallel.mdm
   40606 -rwxr-xr-x     0      0     14691  8-Oct-2006 05:13 Pci.mdm
   40614 -rwxr-xr-x     0      0     33490  8-Oct-2006 05:13 Perc2Ada.mdm
   40631 -rwxr-xr-x     0      0     13931  8-Oct-2006 05:13 PM.MDM
   40638 -rwxr-xr-x     0      0     24251  8-Oct-2006 05:13 Pnp.mdm
   40650 -rwxr-xr-x     0      0     62222  8-Oct-2006 05:13 Raid.mdm
   40681 -rwxr-xr-x     0      0    274886  8-Oct-2006 05:13 Scsi.mdm
   40816 -rwxr-xr-x     0      0     48564  8-Oct-2006 05:13 Serial.mdm
   40840 -rwxr-xr-x     0      0    112763  8-Oct-2006 05:13 Smbios.mdm
   40896 -rwxr-xr-x     0      0     23572  8-Oct-2006 05:13 SMBus.mdm
   40908 -rwxr-xr-x     0      0     27750  8-Oct-2006 05:13 Smi.mdm
   40922 -rwxr-xr-x     0      0      1979  8-Oct-2006 05:13 SYMTREE.INI
   40923 -rwxr-xr-x     0      0     84397  8-Oct-2006 05:13 SYSBDMON.mdm
   40965 -rwxr-xr-x     0      0     76252  8-Oct-2006 05:13 System.mdm
   41003 -rwxr-xr-x     0      0     72648  8-Oct-2006 05:13 Usb.mdm
   41039 -rwxr-xr-x     0      0     48239  8-Oct-2006 05:13 Usb2.mdm
   41063 -rwxr-xr-x     0      0    119144  8-Oct-2006 05:13 UsbDevID.mdm
   41122 -rwxr-xr-x     0      0     52388  8-Oct-2006 05:13 USBEHCI.mdm
   41148 -rwxr-xr-x     0      0    142406  8-Oct-2006 05:13 UsbKbd.mdm
   41218 -rwxr-xr-x     0      0     23801  8-Oct-2006 05:13 UsbMass.mdm
   41230 -rwxr-xr-x     0      0     51298  8-Oct-2006 05:13 UsbMouse.mdm
   41256 -rwxr-xr-x     0      0     34043  8-Oct-2006 05:13 USBOHCI.mdm
   41273 -rwxr-xr-x     0      0     52481  8-Oct-2006 05:13 UsbTm.mdm
   41299 -rwxr-xr-x     0      0     61981  8-Oct-2006 05:13 UsbUfi.mdm
   41330 -rwxr-xr-x     0      0     38267  8-Oct-2006 05:13 USBUHCI.mdm
   41349 -rwxr-xr-x     0      0    157811  8-Oct-2006 05:13 Video.mdm
      69 -rwxr-xr-x     0      0       241  8-Oct-2006 05:13 AUTOEXEC.BAT
      71 -rwxr-xr-x     0      0       264 29-Sep-2006 10:45 EEPROM.DMP

interface_write()
 1 * FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
 2 P HPFS - NTFS             11   0  1 13724 254 63  220315410
 3 E extended LBA         13725   0  1 13986 254 63    4209030
 4 P FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]
 5 L FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
FAT16 at 0/1/1
FAT1 : 1-173
FAT2 : 174-346
start_rootdir : 347
Data : 379-176650
sectors : 176652
cluster_size : 4
no_of_cluster : 44068 (2 - 44069)
fat_length 173 calculated 173

FAT16 at 0/1/1
     FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
     FAT16, 90 MB / 86 MiB

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                    0  32 33 14211  17 14  228298752
     EXT4 Large file Sparse superblock, 116 GB / 108 GiB
NTFS at 11/0/1
filesystem size           220315410
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             11   0  1 13724 254 63  220315410
     NTFS, 112 GB / 105 GiB

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7065 242 26 21276 227  7  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113514496, size=228298752, end=341813247, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7068 160  5 21279 144 49  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113557504, size=228298752, end=341856255, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7069  67 39 21280  52 20  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113567744, size=228298752, end=341866495, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7069 230 10 21280 214 54  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113577984, size=228298752, end=341876735, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7070 202 45 21281 187 26  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113592320, size=228298752, end=341891071, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7073  55 23 21284  40  4  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113631232, size=228298752, end=341929983, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7079 118 16 21290 102 60  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113731584, size=228298752, end=342030335, disk end=234452610)

recover_EXT2: s_block_group_nr=0/870, s_mnt_count=7/30, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 28537344
recover_EXT2: part_size 228298752
     Linux                 7081  30 54 21292  15 35  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
This partition ends after the disk limits. (start=113758208, size=228298752, end=342056959, disk end=234452610)
NTFS at 13724/254/63
filesystem size           220315410
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             11   0  1 13724 254 63  220315410
     NTFS found using backup sector!, 112 GB / 105 GiB
FAT32 at 13726/1/1
FAT1 : 32-4124
FAT2 : 4125-8217
start_rootdir : 8218 root cluster : 2
Data : 8218-4192897
sectors : 4192902
cluster_size : 8
no_of_cluster : 523085 (2 - 523086)
fat_length 4093 calculated 4087

FAT32 at 13726/1/1
     FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
     FAT32, 2146 MB / 2047 MiB
FAT32 at 13726/1/7
FAT1 : 32-4124
FAT2 : 4125-8217
start_rootdir : 8218 root cluster : 2
Data : 8218-4192897
sectors : 4192902
cluster_size : 8
no_of_cluster : 523085 (2 - 523086)
fat_length 4093 calculated 4087
set_FAT_info: name from BS used

FAT32 at 13726/1/7
     FAT32 LBA            13726   1  1 13986 254 63    4192902 [NO NAME]
     FAT found using backup sector!, 2146 MB / 2047 MiB
FAT32 at 13987/0/1
FAT1 : 32-9526
FAT2 : 9527-19021
start_rootdir : 19022 root cluster : 2
Data : 19022-9735389
sectors : 9735390
cluster_size : 8
no_of_cluster : 1214546 (2 - 1214547)
fat_length 9495 calculated 9489
set_FAT_info: name from BS used

FAT32 at 13987/0/1
     FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]
     FAT32, 4984 MB / 4753 MiB
FAT32 at 13987/0/7
FAT1 : 32-9526
FAT2 : 9527-19021
start_rootdir : 19022 root cluster : 2
Data : 19022-9735389
sectors : 9735390
cluster_size : 8
no_of_cluster : 1214546 (2 - 1214547)
fat_length 9495 calculated 9489
set_FAT_info: name from BS used

FAT32 at 13987/0/7
     FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]
     FAT found using backup sector!, 4984 MB / 4753 MiB
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (120 GB / 111 GiB) seems too small! (< 175 GB / 163 GiB)
The following partitions can't be recovered:
     Linux                 7065 242 26 21276 227  7  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7068 160  5 21279 144 49  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7069  67 39 21280  52 20  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7069 230 10 21280 214 54  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7070 202 45 21281 187 26  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7073  55 23 21284  40  4  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7079 118 16 21290 102 60  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
     Linux                 7081  30 54 21292  15 35  228298752
     EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
     FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
     FAT16, 90 MB / 86 MiB
     Linux                    0  32 33 14211  17 14  228298752
     EXT4 Large file Sparse superblock, 116 GB / 108 GiB
     HPFS - NTFS             11   0  1 13724 254 63  220315410
     NTFS, 112 GB / 105 GiB
     FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
     FAT32, 2146 MB / 2047 MiB
     FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]
     FAT32, 4984 MB / 4753 MiB

interface_write()
 
No partition found or selected for recovery

---

### Post by srs5694 on 2011-03-06
Try running TestDisk again, do the deep search, and recover the Linux partition this time.

Also, when posting big files, it's best to do so either as an attachement or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings, which improves legibility and sets up a scrollable area for long extracts.

---

### Post by Rubi1200 on 2011-03-06
srs5694 is right; run it again and find the Linux partition. Use the options in Testdisk (see the link I gave before) to check everything is correct (p option to check the files). Once you are sure you have the right partition then, and only then, write the partition table to restore.

Remember this is a risky operation.

Good luck!

---

### Post by Alexd4 on 2011-03-06
Ok, thanks for the support, I'm about to go ahead and recover the linux partition. Here are the deeper search results

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63

The harddisk (120 GB / 111 GiB) seems too small! (< 175 GB / 163 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                 7065 242 26 21276 227  7  228298752
  Linux                 7068 160  5 21279 144 49  228298752
  Linux                 7069  67 39 21280  52 20  228298752
  Linux                 7069 230 10 21280 214 54  228298752
  Linux                 7070 202 45 21281 187 26  228298752
  Linux                 7073  55 23 21284  40  4  228298752
  Linux                 7079 118 16 21290 102 60  228298752
  Linux                 7081  30 54 21292  15 35  228298752



[ Continue ]
EXT4 Large file Sparse superblock Recover, 116 GB / 108 GiB 
```though the next screen is showing them as all deleted;

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
D Linux                    0  32 33 14211  17 14  228298752
D HPFS - NTFS             11   0  1 13724 254 63  220315410
D FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
D FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 90 MB / 86 MiB

```Remember I am getting the grub rescue prompt on start-up. should I change the status of one to 'primary bootable" ? clicking "p' shows that they all have file lists and none are corrupted or damaged as in the tutorial. Mediadirect has two ominous looking red lines. I've re-written the linux partition. So I have to re-write and see what happens. If i'm not back it's not gone well....

I feel I'm making progress, thanks for your help.

---

### Post by psusi on 2011-03-06
It looks like you reinstalled windows, overwriting Ubuntu in the process.  Time to reinstall Ubuntu and/or restore from backup I'd say.

---

### Post by Alexd4 on 2011-03-07
Thanks for all the assistance, especially Rubi. I rewrote the linux partition and it now boots properly from bios, I'll be staying away from the remaining windows button!

I have got a "fatal" error message saying that certain modules from the kernel cannot be loaded, it does not appear to be affecting performance though are you aware of any diagnostic I could run?

Thanks again for the help and hand-holding. I'll be looking out to pay it forward in the community sometime soon.

---

### Post by Rubi1200 on 2011-03-07
Excellent! Really glad you got things sorted out :)

After making a backup of important data, you might want to consider updating the system.

---

### Post by Alexd4 on 2011-03-09
Hi, Thanks again for your help and your sincere enthusiasm.

I've backed up recently, unfortunately the back-up is in another country at the moment, I'm still a little untrusting of the cloud. 

I'm using the latest version of ubuntu (10.10), and after updating with the most recent patches the second boot issue I mentioned is no longer coming. 

I think it's a hardware problem more than a software one: sometimes I can really hear the harddrive working! Are there some powerful defragging tools or optimisers I can use, similar to Smart Defrag on Windows?

Best,

A

---

### Post by psusi on 2011-03-09
> **Alexd4 said:**
> 
I think it's a hardware problem more than a software one: sometimes I can really hear the harddrive working! Are there some powerful defragging tools or optimisers I can use, similar to Smart Defrag on Windows?


The short answer is no, Linux doesn't need defragging.  The long answer is [http://launchpad.net/e2defrag](http://launchpad.net/e2defrag).

---

