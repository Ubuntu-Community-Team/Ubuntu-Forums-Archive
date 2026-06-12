---
title: "&quot;Disk Utility&quot; - WARNING: The partition is misaligned by 1024 bytes...."
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-12-01
Hello:

Disk Utility suggests that I repartition.

How I got to this point:

I did a complete, fresh install of Ubuntu 10.10 Maverick 64-bit on my 1.0TB hard disk accepting all the installer's defaults.

If I repartition, I guess I should re-install, right? (I have no data yet so that would not matter.)

My question is, I guess, how do I prevent 'ground-hog day'? I don't want this to happen again.

Thanks,

---

### Post by Robert.Thompson on 2010-12-01
hello:

I have decided to just do a re-install but to do the partitioning part all by myself - Yikes!!!!

---

### Post by Robert.Thompson on 2010-12-02
Hello:

It happened again!!!!!!

Does anyone know why or what I have to do to get rid of this problem?

The msg says that I should repartition - what exactly does this mean? Repartition and re-install? Did that and it happened again.

Thanks,

---

### Post by jtarin on 2010-12-03
Be glad to help if you could explain your re-partition process or just download and run the script in my signature and post here within the code brackets.
Did you format the disk before or after partitioning and with what filesystem?

---

### Post by Robert.Thompson on 2010-12-03
> **jtarin said:**
> Be glad to help if you could explain your re-partition process or just download and run the script in my signature and post here within the code brackets.
Did you format the disk before or after partitioning and with what filesystem?

Hello:

I have included the error msg in the attachment.

I think that I formatted when I set up the partitions with "Parted Magic" and again through the Ubuntu installer - using Ext4 in both places.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sda2         204,804,094 1,953,523,711 1,748,719,618   5 Extended
/dev/sda5         204,804,096   286,724,095    81,920,000  83 Linux
/dev/sda6         286,726,144   305,162,239    18,436,096  82 Linux swap / Solaris
/dev/sda7         305,164,288 1,953,520,064 1,648,355,777  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0C54B294348B5C8E                       ntfs       win_maybe                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1   ext4                                     
/dev/sda6        7e348006-396b-4195-9faf-5bd70df13a48   swap                                     
/dev/sda7        df185c8c-8465-47d8-8447-b2d167ab61ab   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sr0         /media/Parted Magic      iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c2d40f3f-0bea-4a83-ba61-402c6c8c5ee1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=df185c8c-8465-47d8-8447-b2d167ab61ab /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=7e348006-396b-4195-9faf-5bd70df13a48 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 113.7GB: boot/grub/core.img
 117.9GB: boot/grub/grub.cfg
 105.8GB: boot/initrd.img-2.6.35-22-generic
 105.8GB: boot/initrd.img-2.6.35-23-generic
 113.7GB: boot/vmlinuz-2.6.35-22-generic
 113.8GB: boot/vmlinuz-2.6.35-23-generic
 105.8GB: initrd.img
 105.8GB: initrd.img.old
 113.8GB: vmlinuz
 113.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  89 5d f4 89 75 f8 89 7d  fc e8 59 f4 f6 ff 81 c3  |.]..u..}..Y.....|
00000010  e6 73 34 00 8b 55 0c 8b  75 10 89 f7 b8 00 00 00  |.s4..U..u.......|
00000020  00 b9 ff ff ff ff f2 ae  f7 d1 c7 02 00 00 00 00  |................|
00000030  c7 44 24 1c 01 00 00 00  8b 45 14 89 44 24 18 89  |.D$......E..D$..|
00000040  54 24 14 89 4c 24 10 89  74 24 0c c7 44 24 08 01  |T$..L$..t$..D$..|
00000050  00 00 00 c7 44 24 04 04  00 00 00 8b 45 08 89 04  |....D$......E...|
00000060  24 e8 c0 fe ff ff 8b 5d  f4 8b 75 f8 8b 7d fc 89  |$......]..u..}..|
00000070  ec 5d c3 55 89 e5 83 ec  38 89 5d f4 89 75 f8 89  |.].U....8.]..u..|
00000080  7d fc e8 e0 f3 f6 ff 81  c3 6d 73 34 00 8b 75 0c  |}........ms4..u.|
00000090  8b 7d 10 89 3c 24 e8 27  0f 01 00 c7 06 00 00 00  |.}..<$.'........|
000000a0  00 c7 44 24 1c 01 00 00  00 8b 55 14 89 54 24 18  |..D$......U..T$.|
000000b0  89 74 24 14 8d 44 00 02  89 44 24 10 89 7c 24 0c  |.t$..D...D$..|$.|
000000c0  c7 44 24 08 01 00 00 00  c7 44 24 04 00 00 00 00  |.D$......D$.....|
000000d0  8b 45 08 89 04 24 e8 4b  fe ff ff 8b 5d f4 8b 75  |.E...$.K....]..u|
000000e0  f8 8b 7d fc 89 ec 5d c3  55 89 e5 83 ec 48 89 5d  |..}...].U....H.]|
000000f0  f4 89 75 f8 89 7d fc e8  6b f3 f6 ff 81 c3 f8 72  |..u..}..k......r|
00000100  34 00 8b 7d 14 8b 75 18  8b 45 10 c7 00 00 00 00  |4..}..u..E......|
00000110  00 85 f6 0f 84 47 01 00  00 8b 55 1c 89 54 24 08  |.....G....U..T$.|
00000120  89 7c 24 04 8b 45 0c 89  04 24 e8 7b eb ff ff 85  |.|$..E...$.{....|
00000130  c0 74 0e 83 c7 01 83 fe  ff 0f 95 c0 0f b6 c0 29  |.t.............)|
00000140  c6 f6 45 1c 01 74 3f 83  fe ff 74 18 d1 ee 89 74  |..E..t?...t....t|
00000150  24 04 89 3c 24 e8 b0 0e  01 00 39 f0 83 d0 00 8d  |$..<$.....9.....|
00000160  34 00 eb 0c 89 3c 24 e8  56 0e 01 00 8d 74 00 02  |4....<$.V....t..|
00000170  81 fe ff ff 0f 00 76 2d  8d 83 54 74 f9 ff 89 04  |......v-..Tt....|
00000180  24 e8 93 6b 01 00 83 fe  ff 75 1a e8 bc d7 f6 ff  |$..k.....u......|
00000190  c7 00 16 00 00 00 be 00  00 00 00 90 8d 74 26 00  |.............t&.|
000001a0  e9 bb 00 00 00 83 e6 fe  c7 44 24 1c 01 00 00 00  |.........D$.....|
000001b0  8d 45 ec 89 44 24 18 8d  45 f0 89 44 24 14 00 fe  |.E..D$..E..D$...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 e2 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  e2 04 00 58 19 01 00 00  |...........X....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 


```

Thanks for your time,

---

### Post by jtarin on 2010-12-04
I would try to boot with the ubuntu CD in the try mode and use Gparted to delete all partitions but the extended and Win7. Then change the extended to a primary partition and format as NTFS. Boot into Win7 and check the validity of this action and also the file system type. If things are good then reboot with the ubuntu CD try mode and Gparted and divide your recently formatted partition into your desired /,/home /swap. Make sure that you check that it is not active. Then do your re-install.
Where did you install Grub? The MBR of your drive or the / of the extended partition? I see by the script there is something odd.
```
Unknown BootLoader  on sda2
```Which is the beginning of your extended partition????? Could you shed some light on that before you do anything?
Also what is name and number of your drive?

---

### Post by Robert.Thompson on 2010-12-16
Hello:

My pc is defective - I sent it to the Acer shop for repairs.

The network card died and the on/off button couldn't make up its mind.

Perhaps the disk was ill as well - I'll know after the 48 hours of diagnostics is completed.

Thanks to all for your time,

---

### Post by srs5694 on 2010-12-17
> **Robert.Thompson said:**
> [CODE]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sda2         204,804,094 1,953,523,711 1,748,719,618   5 Extended
/dev/sda5         204,804,096   286,724,095    81,920,000  83 Linux
/dev/sda6         286,726,144   305,162,239    18,436,096  82 Linux swap / Solaris
/dev/sda7         305,164,288 1,953,520,064 1,648,355,777  83 Linux


This looks like a bug that's generating a false-alarm warning message to me. First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with *some* types of RAID arrays and *some* types of new hard disks (those with 4096-byte physical sectors). See [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for details. If you've got a conventional disk that does not use the Advanced Format (4096-byte physical sector) setup, partition alignment is irrelevant, no matter what any warning message in a disk utility might say. If you've got an Advanced Format disk, proper disk alignment is important, but see below....

All of your primary and logical partitions are properly aligned on 2048-sector boundaries, so they're all fine. The extended partition (/dev/sda2) that houses your logical partitions, though, starts just two sectors (1024 KiB) before your first logical partition. Thus, in some sense that partition is 1024 KiB misaligned. That's the value reported by the warning, which makes me think the warning is referring to that partition. This is *100% irrelevant*, though. The reason is that the partition alignment matters because of filesystem data structures within partitions; however, filesystem data structures are aligned relative to *logical* partitions (or primary partitions), not to the extended partition that houses logical partitions. My suspicion is that the program checks for partition alignment but is overzealous and checks the alignment of the extended partition, which it shouldn't be doing. If so, this is a bug.

---

### Post by yadadamean on 2011-01-01
Hello, I have a similar problem. I just recently bought an HP pavillion and I wanted to dabble with ubuntu, so I went about partitioning my hard drive. Its weird because HP ships so that I pretty much can't partition it, with 4 primaries already being used 1 for SYSTEM, 1 for windows 7, 1 for HP tools and 1 for recovery. to install Ubuntu, I deleted HP Tools and made an extended partition then recovered windows with a recovery disk and it re-installed HP tools for me. my first partition, SYSTEM, is misaligned by 512, Windows is misalgined 3584, the Ubuntu/Swap/HP Tools partition is misaligned 1024, and HP recovery is misalligned by 2048 according to disk utility.

Ideally, I would want a Windows partition, then if possible, a partition for my files to be accessed by both OSes and one final partition for Linux. I'm trying to repartition my hard drive so that they aren't misaligned like disk utility recommends. I've already deleted my ubuntu OS two or three times and hoping to reinstall it again on the aligned partition. am I just physically just ruining my computer? I'm quite a noob at this so please forgive my ignorance, but how do I go about aligning my partitions? I tried to do what jtarin was recommending earlier, but I just don't have anymore free partitions left to create without deleting the Windows OS partition, SYSTEM or the recovery partition. Anyone have tips for me? Thank you in advance!

---

### Post by srs5694 on 2011-01-02
You only need to worry about alignment on a handful of drives, most of which are manufactured by Western Digital, that use the so-called "Advanced Format" system. This system uses 4096-byte physical sectors but presents the illusion of 512-byte sectors to the OS. See [this article I wrote on the topic,](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) or any of dozens of other Web pages, for more information on this.

I recommend you figure out what sort of disk you've got. If it's *not* an Advanced Format disk, then don't worry about it; just use whatever partition alignment is convenient. If you *do* have an advanced format drive, then you might start by using the DOS/Windows utilities provided by the disk manufacturer to ensure that your Windows partitions are properly aligned. You can then use Linux tools to create Linux partitions that are properly aligned -- but the details of how to do this vary with the tool and even the version of the tool, since Linux partitioning tools have been changing rapidly over the past year on how they handle alignment.

As to making room for Linux, your best bet is probably to use the Windows tools to make a backup of the recovery partition (a ~20 GiB partition that holds an installable copy of Windows that the computer manufacturer should have given you on one or more DVDs). You can then delete it, move and resize your partitions as required, and install Linux. (If you've got an Advanced Format hard disk, be sure to check and, if necessary, adjust alignment *after* you move/resize your Windows partitions.) There are many many many many posts on this topic in these forums if you need more details.

---

### Post by srs5694 on 2011-01-02
The forum software is flaking out and producing bogus multiple posts.

---

### Post by srs5694 on 2011-01-02
The forum software is flaking out and producing bogus multiple posts today.

---

### Post by yadadamean on 2011-01-04
thank you so much! i will delve more into this problem of mine with the tools you have suggested. thank you once agian

---

### Post by mastablasta on 2011-01-04
Western digital has a link to a 3rd party programme that aligns the disks propperly. however i think that programme works in windows only.
 
edit: if you use Western digital disk: [http://support.wdc.com/product/download.asp?groupid=805](http://support.wdc.com/product/download.asp?groupid=805)

---

### Post by yadadamean on 2011-01-09
Thank you all for all the help, but sorry to keep bombarding you all with more noob questions, but I have a few more.

So, I followed what srs5694 recommended and went on to find out whether or not my drive was advanced format. Through the disk utility on Ubuntu, I found the model name/no. it was a ToshibaMK7559GSM. I looked at the specs online, and found out that this particular line of HDD were Advanced Format. Although my hard disc is Toshiba, i followed mastablasta's advice and booted to windows and installed the WD Paragon disc alignment utility after searching online for other programs that might be more geared towards Toshiba fearing that the WD website would only supply something compatible only for WD hard drives. Upon installing it and running the program, it had noted that my hard drive was not able to be aligned. So, I ran msinfo32 on windows then checked the specs of my hard drive and it said that it was split up into 512 sectors, not 4096. 

I'm assuming msinfo32 knows more about my hard drive than the stuff i've found online, and perhaps this is why the WD program doesn't work on my hard drive. OR does anyone know if the WD program only works on WD hard drives? thus, it won't work on my Toshiba? and is this the illusion that srs5694 was talking about and is msinfo32 wrong? 

I'm sorry if this has already been posted out there in one of the other forums, but figured this is the easiest place for me to post. Thank you in advance!

---

### Post by srs5694 on 2011-01-09
You may want to read [this article I wrote for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) on the topic. Advanced Format disks use 4096-byte sectors internally, but they've got firmware that "translates" each sector into eight 512-byte sectors; the OS sees the disk as having the more common 512-byte sector size. This creates performance problems if the partitions aren't properly aligned because many filesystem data structures are 4096 bytes in size, resulting in read/write cycles instead of a simple write when changing these data structures.

Because Advanced Format drives present the illusion of 512-byte sectors, some disk utilities give incorrect information about them. I don't know anything about msinfo32 or the Toshiba MK7559GSM specifically; however, if Toshiba's specs say it's an Advanced Format drive, I'd trust those specs rather than the output of msinfo32.

I don't know if the utility you can get from WD would work on non-WD disks. It's possible it's coded to work only on WD disks. It's also possible it's seeing a filesystem that it can't handle. (I don't recall offhand if it'll work with Linux filesystems, for instance.)

I recommend you post the output of the following command:

```

sudo fdisk -lu

```

Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings; this will preserve the columns in the output, improving legibility.

The output will enable us to judge whether your partitions are properly aligned; and if they aren't, to tell you which partition(s) might need adjustment, and perhaps how to do it.

---

### Post by yadadamean on 2011-01-12
Thank. I have been reading your article. it is really quite informative. I hope this helps

```

Disk /dev/sda: 750 GB, 750153761280 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465144065 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1              63      401624      200781    7  HPFS/NTFS
/dev/sda2          401625   411570393   205583805    7  HPFS/NTFS
Warning: Partition 2 does not end on cylinder boundary.
/dev/sda3   *  1220169726  1426250699   103032877    5  Extended
/dev/sda7      1220169728  1230708735     5269320   82  Linux swap
Warning: Partition 7 does not end on cylinder boundary.
/dev/sda6      1230710784  1426024447    97651102   83  Linux
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda5      1426025853  1426250699      104422    7  HPFS/NTFS
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda4      1426250700  1465144064    19438650    7  HPFS/NTFS

```

---

### Post by srs5694 on 2011-01-12
Of your partitions, only /dev/sda7 and /dev/sda6 are properly aligned. If this is an Advanced Format disk, this means that all your NTFS partitions (presumably holding a Windows installation) are improperly aligned and you won't get good performance from them. I've seen test results of improperly aligned NTFS partitions on Advanced Format disks. IIRC, write performance suffered by about 3x -- that is, a write operation that took 10 seconds on a properly-aligned partition took about 30 seconds on an improperly aligned partition. This was from Windows; I don't know how performance from Linux would be impacted.

Unfortunately, Windows can be picky about its boot partition; you can't change its start point and preserve its ability to boot, at least not with GParted or other Linux utlities. This fact closes the door on some possible solutions to the problem. My recommendations for how to proceed depend on what other utilities you've got on hand, how experienced you are, how much you need to get good disk performance from Windows, how much effort you're willing to put into it, and of course whether the disk really is an Advanced Format drive. Googling the drive's model number produced a PDF from Toshiba that clearly states the drive is an Advanced Format model, so if you're positive of the model number you posted, I'd say it's safe to conclude it really is that and will therefore suffer if the partitions aren't properly aligned.

I see several possible options for dealing with this:


[list]
[*]Ignore the issue. This is safe in the sense that you won't be risking your data, but of course you'll get poor NTFS performance.
[*]Back up, repartition, and restore. If you've got adequate Windows backup and recovery tools and suitable media, you can go this route. This is fairly safe if you're familiar with the tools, but it'll be time-consuming. You must be very careful when dealing with the repartitioning so that you create partitions that are properly aligned.
[*]Repartition (without backing up) and re-install Windows. This is fairly straightforward, but if you've got significant data in NTFS partitions already, it may not be practical.
[*]Check Toshiba's site for alignment-fixing tools. The WD tool might be written to work only on WD disks, which could explain its failure. If you find a suitable tool, repair could take hours, and there's a risk of doing damage, so I recommend backing up first.
[*]Use the Windows disk utilities to resize/move your NTFS partitions. As with using a Toshiba tool, this poses some risk of data loss, so I recommend backing up first.
[*]Use GParted or some other tool to resize/move your NTFS partitions. Again, there's a chance of data loss, so back up first. If you do this to the Windows boot partition, Windows will almost certainly refuse to boot, so you'll need to repair it (FWIW, I've never succeeded in doing this) or re-install Windows. Thus, I recommend this approach only on data partitions.
[/list]


You can mix and match these solutions. For instance, you might decide to re-install Windows to its boot partition(s) and move/resize your NTFS data partitions.

You do *not* need to adjust the Linux partitions (/dev/sda6 and /dev/sda7), nor do you need to adjust the extended partition (/dev/sda3), despite the fact that its starting sector number is not a multiple of 8; the extended partition is just a placeholder for the logical partitions it contains, and it's *their* alignment that's important, not the extended partition itself.

Sorry to not have better news.

---

### Post by yadadamean on 2011-01-17
Success!!!....for now. but regardless, thank you for all the help and advice!
So, what I did was after hours of scouring the internet for disk alignment tools, I finally found one. And it was one that I already had, the Paragon Alignment Tool originally found on the WD support site. I found one that was compatible with other brands. and it worked! the program had to restart, when aligning my windows partition, so i believe it wiped out the MBR and booted into grub rescue. I just looked these forums how to restore windows 7 from grub rescue and it worked! so now i boot into windows, but i believe that there's away to restore grub2 so i can dual boot, but since I want to upgrade to ubuntu 10.10 and I backed everything up from my ubuntu and there was not much on it, I don't mind wiping it out and just installing a fresh 10.10. 

Now, I'm just doing a lot of research on how to partition up my hard drive to have a shared data partition. and wow there is a lot of material out there on this! However, I recently discovered that my windows partition has gotten screwey. when i hibernate it, it'll instead restart. this is a good 2 or 3 days after I went through with the align and it didn't happen the first 2 or 3 days as i recall. only noticed it now. Anyway, more work to do before i leave here with my perfect partition, but thank you so much for all the help!

---

### Post by gareththomasnz on 2011-09-03
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.


sigh just installed natty on my new wd hdd

i want an xp partition too

---

### Post by scruffyeagle on 2011-09-03
My 2 cents:

Start by creating a little chart of how you want your partitioning to be when you've finished. This chart should show how many partitions, their approximate size, the types (primary, extended, or logical), the intended final format, and intended usage of each.

Begin by using Gparted from a Live session, to wipe the entire drive's partition table. Then, create just one partition for the Windows OS. Install Windows there, then check the partition's boundaries. If & only if the inspection finds no misalignment, then proceed to creating the next partition. If a misalignment is found, then start over and do it differently.

Proceed going each Windows partition separately for the sake of inspection, only proceeding after that newest partition has been verified as not having any boundary errors. If errors are found, then go back and do ONLY that one partition over.

Once you've finished the Windows installation, use Gparted from a Live session to create all the Ubuntu partitions in one fell swoop. And, proceed to installing Ubuntu.

NOTE: The partitioning of space for the Ubuntu installation can be done from within the installation procedure by selecting the custom partitioning option instead of "side by side", etc.

Installation of Grub for the sake of dual-booting will be done automatically by the Ubuntu installation script.

---

### Post by srs5694 on 2011-09-03
> **gareththomasnz said:**
> Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.


sigh just installed natty on my new wd hdd

i want an xp partition too

It's generally best to begin your own thread rather than "hijack" an existing one, since two interleaved discussions can be very difficult to follow. Since this thread is so old, though, I'll reply here:

The Ubuntu installer, for reasons I don't know, defaults to create a GUID Partition Table (GPT) on disks over a certain size. (The cutoff is in the 1 TB to 2 TB range, but I don't know its precise value.) This is what you're seeing. The "does not start on physical sector boundary" message is unimportant in this case, and you're *not* seeing the actual GPT disks.

The most important problem with this is that Windows XP cannot read GPT disks; it reads only Master Boot Record (MBR; aka "MSDOS" and various other names) disks. If you were installing Windows Vista or 7 64-bit, and if your computer is a new one with UEFI firmware, you might be able to install them using UEFI mode; but with XP, this isn't an option.

Your best option, short of installing XP to another physical disk, is to convert to MBR form. There are several ways to do this, the simplest two being:


[list]
[*]Use GParted, parted, or some other libparted-based tool to create a fresh MBR partition table on the disk. (These tools call this an "msdos disklabel.") In GParted, you'd select Device->Create Partition Table; in parted, you'd type "mklabel msdos". Either method will erase your current partitions, so you'll need to re-install Linux. If you go this route, I recommend creating all your partitions (for Windows and Linux) in parted or GParted with 1 MiB alignment, since Windows XP will create its partitions with cylinder alignment, which will degrade performance.
[*]Use gdisk to convert the disk from GPT to MBR form, as described [here.](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) This will preserve your existing Ubuntu installation, although it will be rendered unbootable until you re-install your boot loader. Also, it's not clear how your partitions are aligned, so you might end up having to re-align them. If you've just installed, it might be easier to re-install with properly-aligned partitions than to re-align your partitions. Post the output of "sudo parted /dev/sda print", between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags, if you want to know if your current GPT partitions are properly aligned.
[/list]


No matter how you do this, be aware that Windows XP overwrites the MBR's boot loader with its own boot loader. This will render Linux unbootable until you re-install GRUB to the MBR.

---

### Post by Blindekinder on 2011-10-28
Hi,
I have a new WD AF hard disk, and the same problem. Don't know if this is correct:
```
~$ sudo parted /dev/sda print
Modèle: ATA WDC WD7500BPKT-6 (scsi)
Disque /dev/sda : 750GB
Taille des secteurs (logique/physique) : 512o/4096o
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      32,3kB  236GB  236GB   extended
 5      64,5kB  117GB  117GB   logical   ext4
 6      117GB   236GB  119GB   logical   ext4
 2      236GB   361GB  126GB   primary   ext4
 3      361GB   746GB  385GB   primary   ext4
 4      746GB   750GB  3891MB  primary   linux-swap(v1)

```Thank you

---

### Post by Blindekinder on 2011-10-28
maybe this helps too:
```
sudo fdisk -lu

Disque /dev/sda: 750.2 Go, 750156374016 octets
255 têtes, 63 secteurs/piste, 91201 cylindres, total 1465149168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identifiant de disque : 0x000af5d8

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1              63   460053404   230026671    5  Etendue
Partition 1 does not start on physical sector boundary.
/dev/sda2       460053405   705301694   122624145   83  Linux
Partition 2 does not start on physical sector boundary.
/dev/sda3       705301695  1457545319   376121812+  83  Linux
Partition 3 does not start on physical sector boundary.
/dev/sda4      1457545320  1465144064     3799372+  82  Linux swap / Solaris
/dev/sda5             126   228187259   114093567   83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6       228187323   460053404   115933041   83  Linux
Partition 6 does not start on physical sector boundary.

```
I'm in big panic, as I crashed my HD and I have big troubles to reinstall: Oneiric is unusable (doesn't boot), Natty I don't want, Maverick .iso is corrupted, so I installed Lucid and the upgrade to maverick, which I had before crash and works pretty well. Then I noticed this warning in Disk Utility, and re-partitionated HD... I'm on live session now...
Thank you for your help

---

### Post by Blindekinder on 2011-10-28
Ok,
I started on live-oneiric, then I re-partitionated all with gparted, letting it choose the start point ('align on Mo'), which I changed in the first install...
On oneiric every partitions was clean in Disk Utilities, and now in Maverick, only the extended one seems wrong (same warning). 
```
Disque /dev/sda: 750.2 Go, 750156374016 octets
255 têtes, 63 secteurs/piste, 91201 cylindres, total 1465149168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Identifiant de disque : 0x00036fe4

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        4094   462989311   231492609    5  Etendue
Partition 1 does not start on physical sector boundary.
/dev/sda2       462989312   689477631   113244160   83  Linux
/dev/sda3       689477632  1455841279   383181824   83  Linux
/dev/sda4      1455841280  1465147391     4653056   82  Linux swap / Solaris
/dev/sda5            4096   228720639   114358272   83  Linux
/dev/sda6       228722688   462989311   117133312   83  Linux

Disque /dev/sdb: 250.1 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres, total 488397168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x000bf923

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1              63   488392064   244196001   83  Linux

```
Is that a problem?
Thank's

---

### Post by jackhill99 on 2011-12-20
Hey everyone

I had problems formatting my new 2TB WD drive in Ubuntu 10.04. I kept on getting misaligned warnings but eventually found a working solution using parted

This is what I did to remove the alignment warnings and successfully format my drive

[COLOR=Gray][COLOR=Black]From the shell as root[/COLOR][/COLOR][I][COLOR=Gray]

parted -a opt /dev/sde [COLOR=Black](replace with your device) [/COLOR]
(parted) u MiB 
(parted) rm 1 
(parted) mkpart primary 1 100%
(parted) quit[/COLOR][/I]

I then used the disk utility to format my drive, no errors!! :P

Hope this helps

---

### Post by hardisty on 2012-01-06
Sorry to revive this again, but I'm having the same problem and I find many of the comments to be confusing to my newbie brain. 

Is this really damaging my performance significantly? I only use Ubuntu, I only have Windows on there as a backup. (Hey, I had to pay for the damn OS, might as well have it in case! :P)

```
hardisty@TARDIS:~$ sudo fdisk -lu
[sudo] password for hardisty: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd7ad165c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          411646  1217595391   608591873    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3      1217595392  1250050047    16227328    7  HPFS/NTFS
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)
/dev/sda5          411648    23846911    11717632   82  Linux swap / Solaris
/dev/sda6        53145600  1217595391   582224896   83  Linux
/dev/sda7        23848960    53143881    14647461   83  Linux

Partition table entries are not in disk order
hardisty@TARDIS:~$ 

```

Disk utility says /dev/sda2 is the one that is off by 1024

Thanks for all replies!

---

### Post by flashback_rtk on 2012-03-06
I had similar misalignment issues with a Werstern Digital drive over 1,5TB, though I didn't have to worry with any Windows partition. I got the solution by reading the article posted by user srs5694 ([http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/#tools](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/#tools)) and using GParted. If anyone is facing a similar situation just be sure to leave 1MiB before the first partition (Works OK for Ubuntu I don't know if it does for Windows) and untick the "round to cylinders" option for every partition.

Thanks a lot to user srs5694 for sharing his/her knowledge

---

### Post by growingneeds on 2012-04-23
The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for newer installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignment issue.

Hope this helps.

---

### Post by updatelee on 2012-04-25
> **growingneeds said:**
> The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for newer installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignment issue.

Hope this helps.

Thanks for the tip, got me past the install issue as well.

Chris Lee

---

### Post by dakota34 on 2012-10-17
thanks for this thread and links, used gdisk interactive command line to create new GPT & start new partition at 2048, now all is good. was previously getting 'misaligned' warning on disks.

---

