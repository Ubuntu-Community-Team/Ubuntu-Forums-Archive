---
title: "error: no such partition. grub rescue&gt;"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by offbeat404 on 2011-03-10
Hello good folks, I'm having an 'error: no such partition. grub rescue>' after trying & failing to remove Kubuntu KDE and restoring my default Gnome. I was running 10.10 dual-boot with xp but everything started going south after trying to delete an 'unknown' partition via My Computer>Manage which was an instruction i read on the forum showing how to remove Ubuntu completely so i can re-install it from scratch. Long story short, i'm stuck on the grub error screen and your help would be highly appreciated. I booted through Ubuntu live and ran the bootinfo script as requested. I was also trying to install and run TestDisk but i get an error saying i have insufficient storage.   PS: i can see my widows installation via the Live cd - i really need that.   Thanks in advance. ```
                Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in     partition #8 for (,msdos8)/boot/grub.  => Syslinux is installed in the MBR of /dev/sdb  sda1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows XP     Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM  sda2: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sda5: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:  According to the info in the boot sector, sda5 starts                        at sector 63.     Operating System:       Boot files/dirs:    sda6: _________________________________________________________________________      File system:           Boot sector type:  Unknown     Boot sector info:       Mounting failed: mount: unknown filesystem type ''  sda7: _________________________________________________________________________      File system:           Boot sector type:  Unknown     Boot sector info:       Mounting failed: mount: unknown filesystem type '' mount: unknown filesystem type ''  sdb1: _________________________________________________________________________      File system:       vfat     Boot sector type:  Unknown     Boot sector info:  According to the info in the boot sector, sdb1 starts                        at sector 0. But according to the info from fdisk,                        sdb1 starts at sector 62.     Operating System:       Boot files/dirs:    =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Partition  Boot         Start           End          Size  Id System  /dev/sda1    *             63   218,192,564   218,192,502   7 HPFS/NTFS /dev/sda2         218,193,918   488,396,799   270,202,882   f W95 Ext d (LBA) Extended  partition  linking to another extended partition /dev/sda5         257,168,583   448,435,599   191,267,017   7 HPFS/NTFS Invalid MBR Signature found /dev/sda6     ?   707,937,913   707,937,912                   Unknown /dev/sda7     ?   707,937,913   707,937,912                   Unknown  /dev/sda6 ends after the last sector of /dev/sda the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2 /dev/sda7 ends after the last sector of /dev/sda the logical partition /dev/sda7 is not contained in the extended partition /dev/sda2  Drive: sdb ___________________ _____________________________________________________  Disk /dev/sdb: 2062 MB, 2062548992 bytes 64 heads, 62 sectors/track, 1015 cylinders, total 4028416 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                          /dev/loop0                                              squashfs                                 /dev/loop1       b2267437-9df4-4d54-a75a-4da0298bcb83   ext3                                     /dev/sda1        ECA0B8F1A0B8C2FE                       ntfs                                     /dev/sda2: PTTYPE=&quot;dos&quot; /dev/sda5        52ECD2B6ECD29417                       ntfs       dev                           /dev/sda: PTTYPE=&quot;dos&quot; /dev/sdb1        89CD-833C                              vfat                                     /dev/sdb: PTTYPE=&quot;dos&quot; error: /dev/sda6: No such file or directory error: /dev/sda7: No such file or directory  ============================ &quot;mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sda1        /media/ECA0B8F1A0B8C2FE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/loop1       /media/b2267437-9df4-4d54-a75a-4da0298bcb83 ext3       (rw,nosuid,nodev,uhelper=udisks)   ================================ sda1/boot.ini: ================================  [boot loader] timeout=30 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=&quot;Microsoft Windows XP Professional&quot; /noexecute=optin /fastdetect multi(0)disk(0)rdisk(0)partition(2)\WINDOWS=&quot;Windows Server 2003, Enterprise&quot; /noexecute=optout /fastdetect =========================== Unknown MBRs/Boot Sectors/etc =======================  Unknown BootLoader  on sda6   Unknown BootLoader  on sda7   Unknown BootLoader  on sdb1  00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .| 00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....| 00000020  42 74 3d 00 58 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.X...........| 00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 00000040  00 00 29 3c 83 cd 89 20  20 20 20 20 20 20 20 20  |..),~...ruv.| 00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..| 00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f| 00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`| 00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`| 00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1| 00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...| 00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa| 00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.| 000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......| 000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........| 000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot| 000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........| 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200   =============================== StdErr Messages: ===============================  hexdump: /dev/sda6: No such file or directory hexdump: /dev/sda6: No such file or directory hexdump: /dev/sda7: No such file or directory hexdump: /dev/sda7: No such file or directory
```

---

### Post by offbeat404 on 2011-03-10
:confused:

---

### Post by Dorsenstein on 2011-03-10
If you have all your data backed up, I would just reinstall everything. If you don't have your data backed up, my best idea would be to do the following.

Use the Ubuntu Live CD to open gparted under System -> Administration. (If it's not there use the command sudo apt-get install gparted in terminal)

Delete all the Ubuntu related partitions, but be really careful not to delete the boot partition of Windows. You should then be able to resize the Windows partition with all the unallocated space. If you reboot after that it should work.

Since you said you really needed the Windows partition, I assume most of your vital data is on there.

---

### Post by offbeat404 on 2011-03-10
> **Dorsenstein said:**
> If you have all your data backed up, I would just reinstall everything. If you don't have your data backed up, my best idea would be to do the following.

Use the Ubuntu Live CD to open gparted under System -> Administration. (If it's not there use the command sudo apt-get install gparted in terminal)

Delete all the Ubuntu related partitions, but be really careful not to delete the boot partition of Windows. You should then be able to resize the Windows partition with all the unallocated space. If you reboot after that it should work.

Since you said you really needed the Windows partition, I assume most of your vital data is on there.
Thanks for your quick response Dorsenstein, I haven't backed up my data yet but i'm working on it as we speak. I just ran gparted and its telling me i have 232.89GiB unallocated, i don't see any ubuntu related partitions :confused:

ps: when i do $ sudo fdisk -l i get an error "Unable to seek on /dev/sda"
"

---

### Post by offbeat404 on 2011-03-10
I'm almost done backing up my data (on xp) and decided to start off from scratch. I want to reformat my whole hdd and start with windows xp followed by ubuntu 10.10 as dual boot. can you direct me how i can forward in reformatting since my Win XP cd is saying no HDD found in the setup.

thank you in advance

---

