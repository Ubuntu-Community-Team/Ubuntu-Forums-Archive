---
title: "Can't boot to windows."
date: 2011-03-10
forum: New to Ubuntu
---

### Post by guilleme on 2011-03-10
Hi. Well, I recently bought a netbook, and was happily making stuff with it. It used to have windows 7. I took a usb drive, and installed the Ubuntu netbook remix on it. I messed up with it, and now there's not much left of windows. 
Small version:
 Bought, configured windows, installed ubuntu, could not boot windows, messed the partitions really hard, lost them all,  recovered some with disktest, and still can't boot to windows. It complains it can't get the file "winloader.exe", but I have proves that it exists, and that exists where (I suppose) it is being lookd for.
Here's the complete story.
I bought the computer, then I turned it on, and configured windows. Then I took a real OS, and installed Ubuntu. There were 3 partitions on the disk. A medium one with something like 12 gb., a small one, that's just a couple hundred megabytes, and a large one, with 200 and something Gb. The small was dubbed "windows vista (loader)", the 12 GB one was the "windows 7 (loader)", and the large one was Windows 7 itself. I said, no problem, and deleted the "windows vista (loader)" partition, resized the biggest one to a hundred GB, made a 2 GB swamp, and installed on what was left. Rebooted. I was almost shocked when I saw GRUB listing ubuntu and Win. vista (loader), I had deleted that partition. Tested Ubu, no problem. Reboot, and test Windows. It took me to a "Recovery (stuff)", and so, whit no other choice, I clicked next, reboot, and redirected to /dev/null/ on a GRUB>Rescue incarnation. Took the live USB out again, and rebooted. Reinstalled many times, and made some weird stuff. I was finally exhausted at 2-3 AM, and redirected windows to where it belongs, and where it had sent me, right to /dev/null/, and installed Ubu on the whole disk. 
At the next day, I regretted it, so I booted (again), with the USB, and tried to fix it with "testdisk", testdisk did a great job, and I could get back the big partition and the win 7 loader one, reinstalled, rebooted, and, god is merciful, GRUB listed ubuntu, the memory tests, and windows 7. Ubu. had no problems at all. Went to try win 7, and it  told me it couldn't load. It just couldn't. It tells me that the file "Winload.exe" was missing or corrupted. It searched for it on "/windows/system32/winload.exe", but when booting ubu, you can lively see it, there it is, alive, safe and sound, so I don't know what's going on. The thing that boots, whatever it is, lets me navigate though 2 screens, one for selecting the windows 7 "repair/boot" or memory tests, and one for complaining and instructions. The memory tests work, and then drop me again on the 2cond screen I mentioned. Now it's a little exasperating. 
Thanks for any help, Any advice is appreciated.

---

### Post by wilee-nilee on 2011-03-10
That information all in one paragraph is just to convoluted. This will give us the what is where.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Rubi1200 on 2011-03-11
wilee-nilee is right; if you want us to help you, please post the results of the boot info script.

I hope wilee-nilee won't mind, but here are step-by-step instructions:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by fabricator4 on 2011-03-11
> **guilleme said:**
> There were 3 partitions on the disk. A medium one with something like 12 gb., a small one, that's just a couple hundred megabytes, and a large one, with 200 and something Gb. The small was dubbed "windows vista (loader)", the 12 GB one was the "windows 7 (loader)", and the large one was Windows 7 itself. I said, no problem, and deleted the "windows vista (loader)" partition,

As near as I can figure, that 12 GB partition was the OEM windows recovery partition.  Since you subsequently erased this partition and then used the whole disk for Ubuntu, It seems likely that it has been overwritten.  Testdisk probably tried to get the partition and it's contents back, apparently, but a bit like an old 'B' horror movie, what you got back from the grave wasn't quite what you expected.

If you want Windows back, you might have to ask the OEM manufacturer for a copy of the installation disks for that model.  Of course, they will want some money for this service.


Chris

---

### Post by guilleme on 2011-03-11
Here are the "boot_info_scrip055.sh" results:

 ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4011 MB, 4011851776 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7835648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             62     7,834,071     7,834,010   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    27,265,023    27,262,976   7 HPFS/NTFS
/dev/sdb2         485,752,832   488,396,799     2,643,968  82 Linux swap / Solaris
/dev/sdb3          27,469,824   247,469,823   220,000,000   7 HPFS/NTFS
/dev/sdb4    *    247,470,080   485,751,329   238,281,250  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       8cbca5e5-c624-4f45-ade3-321f907227a3   ext3                                     
/dev/sda1        B4A7-146A                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c4c5ddbb-cee2-4162-825e-16009b891474   ext3                                     
/dev/sdb2        d7a9a922-eb3e-4c30-88d4-d026e9cb1c67   swap                                     
/dev/sdb3        0A728F44728F340B                       ntfs       Acer                          
/dev/sdb4        82fe875a-4976-4c6c-bd23-89018016fde5   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos4)'
search --no-floppy --fs-uuid --set 82fe875a-4976-4c6c-bd23-89018016fde5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos4)'
search --no-floppy --fs-uuid --set 82fe875a-4976-4c6c-bd23-89018016fde5
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set 82fe875a-4976-4c6c-bd23-89018016fde5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82fe875a-4976-4c6c-bd23-89018016fde5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set 82fe875a-4976-4c6c-bd23-89018016fde5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=82fe875a-4976-4c6c-bd23-89018016fde5 ro single 
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
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set 82fe875a-4976-4c6c-bd23-89018016fde5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set 82fe875a-4976-4c6c-bd23-89018016fde5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 0a728f44728f340b
    chainloader +1
}
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

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=82fe875a-4976-4c6c-bd23-89018016fde5 /               ext3    errors=remount-ro 0       1
# /windows was on /dev/sdb3 during installation
UUID=0A728F44728F340B /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb2 during installation
UUID=d7a9a922-eb3e-4c30-88d4-d026e9cb1c67 none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


 150.2GB: boot/grub/core.img
 150.3GB: boot/grub/grub.cfg
 150.2GB: boot/initrd.img-2.6.35-22-generic
 150.2GB: boot/vmlinuz-2.6.35-22-generic
 150.2GB: initrd.img
 150.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  9a 89 77 00 d8 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 6a 14 a7 b4 20  20 20 20 20 20 20 20 20  |..)j...         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 a0 f9 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
Thanks.

---

### Post by wilee-nilee on 2011-03-11
Some red flags such as sdb1 information.
sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is supposed to be here? To be honest even if we can get it to boot MS and Ubuntu this does not mean it is fixed you have had a bit of a process to get to this point. you might consider backing up what you need and reinstalling.

At this point though windows on sdb3 needs the boot flag use gparted to move it there. Put the sdb drive first to be read in the bios, and if you get in Ubuntu run.
sudo update-grub
to see if windows shows.

---

### Post by Rikeshar on 2011-03-11
Hello, I hope you don't mind me jumping in. I'm having a similar issue. It first started a few nights ago, and after booting from the live cd and reading around, I saw it mentioned somewhere that it might help to update GRUB. I did this using sudo update-grub. This took care of the issue, with an unexpected, but not altogether unwanted result: instead of having to choose a temporary boot device to boot on to the external drive Ubuntu is on, I got a grub menu which showed the the OSs for both HDDS.

I thought all was fine, but a few days later, same thing. Updated grub again, and all was okay. Tonight, it happened again. When I try to update grub now it says: 

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```I was hoping someone could help me resolve this issue once for and all. Here's the result of the boot info script. 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
95 heads, 54 sectors/track, 95204 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,930,175    10,928,128  27 Hidden HPFS/NTFS
/dev/sda2    *     10,930,176   488,392,695   477,462,520   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C024E03224E02D5A                       ntfs       ServiceV002                   
/dev/sda2        9216E2AC16E29111                       ntfs       SW_Preload                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        29c7bf08-f489-41a5-ba12-d69badbc5924   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9c4560ff-c3e9-431b-8ae2-11abbedbce5f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 29c7bf08-f489-41a5-ba12-d69badbc5924
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c024e03224e02d5a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9216e2ac16e29111
    chainloader +1
}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
# Commented out by Dropbox
# UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9c4560ff-c3e9-431b-8ae2-11abbedbce5f none            swap    sw              0       0
UUID=29c7bf08-f489-41a5-ba12-d69badbc5924 / ext4 errors=remount-ro,user_xattr 0 1

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  64.6GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
  64.6GB: boot/initrd.img-2.6.35-27-generic
  34.6GB: boot/vmlinuz-2.6.35-22-generic
  34.6GB: boot/vmlinuz-2.6.35-27-generic
  64.6GB: initrd.img
   1.5GB: initrd.img.old
  34.6GB: vmlinuz
  34.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  7d 6c 95 09 a1 5d 4c 69  79 aa 68 2b 29 38 48 7d  |}l...]Liy.h+)8H}|
00000010  ee 11 16 46 e2 1c 46 76  41 af 99 95 58 9e e2 36  |...F..FvA...X..6|
00000020  5d 43 4b ff 68 0c 29 12  4d 17 4d 9b ff de 1a 34  |]CK.h.).M.M....4|
00000030  b0 90 3f 2a bf bc c3 cb  53 c2 b4 a1 34 25 2b b1  |..?*....S...4%+.|
00000040  eb 23 a2 b0 9a 9f df 51  29 ec 3d 99 9d 88 f7 ad  |.#.....Q).=.....|
00000050  9b c3 ab e6 cd 46 e4 b4  8f 9f 24 4c da af df da  |.....F....$L....|
00000060  61 da e5 df 5b 1a 51 e1  3f 0f b4 f7 0d a8 e8 5c  |a...[.Q.?......\|
00000070  54 6f ea 95 60 51 7c 51  b5 85 45 86 e3 0d fa a4  |To..`Q|Q..E.....|
00000080  c3 36 1e e2 85 06 7f 18  3c b4 e5 c4 36 30 21 4b  |.6......<...60!K|
00000090  58 37 9f a0 0a 90 b7 e5  d0 da ea 8e 12 01 df c5  |X7..............|
000000a0  53 8a 6a 9b e8 be 47 10  eb 14 8c 3f 2d f5 f3 09  |S.j...G....?-...|
000000b0  7c 84 77 ac 94 03 dd bf  c8 07 a5 a2 fb 06 2c c0  ||.w...........,.|
000000c0  51 99 ca a7 24 4d bc ed  fa 1d c2 bc b5 fd 41 29  |Q...$M........A)|
000000d0  a2 eb ad 63 ef 22 5e a2  7e 55 80 a1 a0 b3 d7 34  |...c."^.~U.....4|
000000e0  0a 71 01 fd bd b9 06 d9  86 6d ab 47 34 fb 04 af  |.q.......m.G4...|
000000f0  50 b9 eb 82 64 ae 19 2c  e3 78 3d 49 d6 9c 04 cf  |P...d..,.x=I....|
00000100  42 dc ca b9 33 8b 87 0e  c2 26 d1 e2 61 8d e0 5e  |B...3....&..a..^|
00000110  0b 13 7d 17 53 28 e2 3e  a6 28 a5 2f 26 55 45 7a  |..}.S(.>.(./&UEz|
00000120  4f 10 94 6b 0e b8 6a c8  32 70 b1 87 37 02 8a 79  |O..k..j.2p..7..y|
00000130  b4 25 6e 0f b5 db 66 de  1c 83 4e d0 9e 15 af 3f  |.%n...f...N....?|
00000140  15 0c 28 e2 f6 0e 12 e1  8d 4b e1 3f bd 41 23 2c  |..(......K.?.A#,|
00000150  40 a3 c3 5a 71 34 d2 f6  33 8b 8d 62 17 3b 96 a5  |@..Zq4..3..b.;..|
00000160  02 f6 37 57 f4 84 b0 7b  12 94 33 67 35 25 8a 6d  |..7W...{..3g5%.m|
00000170  de f9 e1 16 6a 70 a6 98  f1 72 b1 16 6e 14 69 6a  |....jp...r..n.ij|
00000180  b6 f8 da 99 98 9d bc 3d  41 f7 91 c8 f6 25 71 a4  |.......=A....%q.|
00000190  79 e7 c9 1c 2d a1 1b 22  4f d5 8d ea c5 e6 7a 4e  |y...-.."O.....zN|
000001a0  87 72 3d b0 ee af 24 b3  7e 78 28 70 b8 67 2b 2d  |.r=...$.~x(p.g+-|
000001b0  c8 3c 44 79 fb c3 00 17  b5 09 87 e3 47 69 00 fe  |.<Dy........Gi..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

It looks like the problem is that there's no boot loader on the drive Ubuntu's installed on. Any ideas?

**UPDATE** So remove grub-pc and reinstalled legacy grub. I then did sudo apt-get install grub-pc and it's at a screen asking me which devices I want to install grub to. I choose both sda and sdb and it comes up saying it failed to install to both. On the terminal I get 

```
Setting up grub-pc (1.98+20100804-5ubuntu3) ...
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
```

---

### Post by wilee-nilee on 2011-03-11
Rikeshar if you can post all that in your own thread it would be great we try to keep this stuff separate, due to the complexity it is just easier.;) Send me a pm and I will give you fixing the commands.

Run a new version of the script I see no grub legacy in it when you have switched.

---

### Post by Rikeshar on 2011-03-12
Will do :)

---

### Post by guilleme on 2011-03-13
Just tried, didn't help. :(. 
Tried on different ways: with gparted, the disk utility, and the instalation program. None could make it work. :(.

---

### Post by guilleme on 2011-03-20
I think I've found a solution, because the problem there appears to be the exact same one that I'm having, it's the black screen at somewhere at the middle of the page. I'm going to try the solution listed there and post the results here.

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

