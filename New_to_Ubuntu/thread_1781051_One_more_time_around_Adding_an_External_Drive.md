---
title: "One more time around: Adding an External Drive"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by JohnBonne on 2011-06-12
This is a specific problem which maybe I can help someone else with down the line. Yesterday, the O/S on my external drive would not allow me to log in. it was Ubuntu. I had installed Linux Mint two days previously; HAD Ubuntu installed on my External Drive first. I am going about this ***-backwards hoping to solve unsolvable problems. Now, since Ubuntu died; I have Windows VIsta and Linux Mint on the internal drive and want to install an operating system on my E.D. 

How do I not create a problem with this triple set-up, say I want to install Xbuntu on the External Drive?

---

### Post by jtarin on 2011-06-12
What problems are you anticipating?

---

### Post by JohnBonne on 2011-06-12
> **jtarin said:**
> What problems are you anticipating?

Anticipating a boot failure after install. I had Windows and Ubuntu. When I installed Mint alongside Windows abd Updated GRUB the boot would not launch Natty.

---

### Post by jtarin on 2011-06-12
Does your external drive show up in /media in your Mint install?

---

### Post by jtarin on 2011-06-12
[If you need to edit your existing Grub to boot Natty on your EHD]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries")

---

### Post by oldfred on 2011-06-12
Do not know the exact difference that Xbuntu has with an install of Ubuntu. Installer should be similar if not identical. But with Ubuntu on a second drive you have to use manual install or Something Else in Natty. Then you get the choice on where to install the grub2 boot loader which is the MBR of the second/external drive. Otherwise grub2 defaults to the MBR of sda.


Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by manzdagratiano on 2011-06-12
I would suggest using Linux Mint's Grub2 as the bootloader, since it is on the internal drive and therefore always plugged in. You will just have to install Ubuntu on the external drive without a bootloader, and then run 'sudo update-grub' from Mint (I assume it works the same way as Ubuntu, I have myself never used Mint), and all should be fine. I do not use external HDs for OSes, but I have multiple Linuxes on my hard drive all handled by Ubuntu's grub2 and it all works like a charm.

---

### Post by JohnBonne on 2011-06-12
> **jtarin said:**
> Does your external drive show up in /media in your Mint install?

yes.

---

### Post by jtarin on 2011-06-13
Then you can install it to the external drive and use Mints Grub as manzdagratiano suggest. In my signature is a link to EasyBCD which when you have time you might want to consider if you plan on keeping Windows for a long time......just another way to boot your sytems without touching Win MBR with Grub2.

---

### Post by JohnBonne on 2011-06-13
> **oldfred said:**
> Do not know the exact difference that Xbuntu has with an install of Ubuntu. Installer should be similar if not identical. But with Ubuntu on a second drive you have to use manual install or Something Else in Natty. Then you get the choice on where to install the grub2 boot loader which is the MBR of the second/external drive. Otherwise grub2 defaults to the MBR of sda.


Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

I am sure it was the update of the Grub2 loader that corresponded to the loss of my Ubuntu O/S. Installed Ubuntu on the E.D. using Ubuntu's native installer, then installed Mint on the Sda/1 using Grub2. There maybe was a conflict where the Operating systems  were installed? I believe this is where the trouble lies.

---

### Post by oldfred on 2011-06-13
Once you have more than one operating system or more than one bootable drive, you should use this tool to know what is where. I find it also worthwhile just as a backup of the details of the boot configuration in case I have to recover drive or install info.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by JohnBonne on 2011-06-13
Fred: Thanks!

This is the reading bootinfoscript gave me.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdc7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
90 heads, 63 sectors/track, 110254 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   538,920,958   538,920,896   7 NTFS / exFAT / HPFS
/dev/sda2         538,922,221   625,141,759    86,219,539   f W95 Extended (LBA)
/dev/sda5         538,922,223   546,951,519     8,029,297  83 Linux
/dev/sda6         546,953,216   625,141,759    78,188,544  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301908992 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1       2,200,680,153 2,930,272,064   729,591,912   7 NTFS / exFAT / HPFS
/dev/sdc2          84,550,095 2,200,680,089 2,116,129,995   f W95 Extended (LBA)
/dev/sdc5          84,550,158    91,008,224     6,458,067   7 NTFS / exFAT / HPFS
/dev/sdc6          91,008,288 1,465,336,844 1,374,328,557   7 NTFS / exFAT / HPFS
/dev/sdc7       1,465,336,908 2,200,680,089   735,343,182   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63     7,855,784     7,855,722   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       51479331-6238-4a26-93c0-7aa2cbc867ee   ext4       
/dev/sda1        14F00DDCF00DC548                       ntfs       
/dev/sda5        8f852101-b54f-4c28-910f-556ed53835fe   ext3       
/dev/sda6        e15d8c8d-b680-4c9b-9656-cefdb1546600   ext4       
/dev/sdc1        01CBD0945E4134E0                       ntfs       
/dev/sdc5        01CC23A0787AE040                       ntfs       
/dev/sdc6        01CC23A0B75AEA30                       ntfs       
/dev/sdc7        8CC651E0C651CADA                       ntfs       Drive 2
/dev/sdd1        C61A-19CC                              vfat       DISK I

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc1        /media/01CBD0945E4134E0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/01CC23A0787AE040  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc6        /media/01CC23A0B75AEA30  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc7        /media/Drive 2           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/DISK I            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdd1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 30 04  |.X.MSDOS5.0...0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  6a de 77 00 e8 1d 00 00  00 00 00 00 02 00 00 00  |j.w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 cc 19 1a c6 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Something is stopping me from installing on the E.D. There are errors there and I don't know what they mean. Can anyone find the 
reason I get the error message when I try to run the LiveCD.
Thanks in Advance,

---

### Post by oldfred on 2011-06-13
If you still have Mint on sda6 and sda5, it is showing corruption of some sort as it cannot mount them.

I would try repair them. Often gparted does not open drives with errors but I do not know why it would not open the external drive even with corruption on the internal.

From liveCD so everything is unmounted,swap off if necessary, change sda5 & sda6 for your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

You are showing a wubi inside sda1, is that how you installed Ubuntu? That only boots from the windows boot loader, so you would have to boot windows and it will then give a choice of windows or Ubuntu.

---

### Post by JohnBonne on 2011-06-14
> **oldfred said:**
> If you still have Mint on sda6 and sda5, it is showing corruption of some sort as it cannot mount them.

I would try repair them. Often gparted does not open drives with errors but I do not know why it would not open the external drive even with corruption on the internal.

From liveCD so everything is unmounted,swap off if necessary, change sda5 & sda6 for your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

You are showing a wubi inside sda1, is that how you installed Ubuntu? That only boots from the windows boot loader, so you would have to boot windows and it will then give a choice of windows or Ubuntu.


You hit the nail right on the head, Fred. Sorry the pun was unintended. 

When I boot up, the old Ubuntu loader is still there. I.E., the wubi screen from when I installed Ubuntu first is  still there. I have to boot through the original load list to the Windows/Linux dual boot. I looked in Windows programs for the Ubuntu/Wubi Install/Uninstall but the Wubi aint there and tried to update Grub2 but the Ubuntu still shows up first which tells me the problem is I didn't lay out the installs right. I should have installed Windows, then Mint, then Ubuntu. but I installed Windows, then Ubuntu on the E.D. then Mint. There is some compatibility problem between Wubi and Grub, right? Is there a way to clean this mess up while keeping the Windows/Mint? I can't install Ubuntu as things are halting the install and I get a boot error when using the LiveCD. 

It just feels I am buried by the problem because I don't want to be doing this. I want life to be happy and gay as the song says.

---

### Post by oldfred on 2011-06-14
Is the drive shown as sdc 1500GB not the external? If so then the script could not see sdb also, I would check that BIOS sees it. 

You are supposed to be able to delete wubi just like a windows program. But I think you can just delete the files and use bcdEdit in windows to remove the Ubuntu/wubi boot entry.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

### Post by JohnBonne on 2011-06-15
What a drag. I installed Ubuntu all right, right n top of the Windows partition. I have Just Ubuntu installed now, and the  mint is hidden on it's partition. Could you help me? I want to find the partition that Mint resides on and try to recover it. It does not show up in files search, partition search or GParted.

---

### Post by JohnBonne on 2011-06-15
```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   566,546,431   566,544,384  83 Linux
/dev/sda2         566,548,478   625,141,759    58,593,282   5 Extended
/dev/sda5         566,548,480   625,141,759    58,593,280  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301908992 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1       2,200,680,153 2,930,272,064   729,591,912   7 NTFS / exFAT / HPFS
/dev/sdb2          84,550,095 2,200,680,089 2,116,129,995   f W95 Extended (LBA)
/dev/sdb5          84,550,158    91,008,224     6,458,067  83 Linux
/dev/sdb6          91,008,288 1,465,336,844 1,374,328,557   7 NTFS / exFAT / HPFS
/dev/sdb7       1,465,336,908 2,200,680,089   735,343,182   7 NTFS / exFAT / HPFS
/dev/sdb3               2,048    84,549,631    84,547,584  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        fad75621-ce4f-4e1e-8e0f-ade58a4461e7   ext4       
/dev/sda5        64bfc3e5-3ada-4be2-91d5-82b39ce12f1b   swap       
/dev/sdb1        01CBD0945E4134E0                       ntfs       
/dev/sdb3        5398b826-dc2f-4106-94a3-b0717b553e92   ext4       
/dev/sdb5        eddbccae-e949-4ef5-8b04-83283b8dc2c0   ext4       
/dev/sdb6        01CC23A0B75AEA30                       ntfs       
/dev/sdb7        8CC651E0C651CADA                       ntfs       Drive 2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/01CBD0945E4134E0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/5398b826-dc2f-4106-94a3-b0717b553e92 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/eddbccae-e949-4ef5-8b04-83283b8dc2c0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6        /media/01CC23A0B75AEA30  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/Drive 2           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fad75621-ce4f-4e1e-8e0f-ade58a4461e7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fad75621-ce4f-4e1e-8e0f-ade58a4461e7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fad75621-ce4f-4e1e-8e0f-ade58a4461e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=64bfc3e5-3ada-4be2-91d5-82b39ce12f1b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.135009766 = 77.454376960   boot/grub/core.img                             1
  72.137126923 = 77.456650240   boot/grub/grub.cfg                             1
   1.067607880 = 1.146335232    boot/initrd.img-2.6.38-8-generic               1
  72.133281708 = 77.452521472   boot/vmlinuz-2.6.38-8-generic                  1
   1.067607880 = 1.146335232    initrd.img                                     1
  72.133281708 = 77.452521472   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-06-15
Script now does not show the mint partitions. Did you do an install to the entire drive?

Because I do not trust auto installers and want more control over sizes & locations of partitions, I always partition in advance. 

But even that does not always work unless you pay attention. I created several new partitions at once and then promptly installed a new Ubuntu install to my data partition. Memory seems to not work well anymore, so I have to write down everything or print it out.

---

