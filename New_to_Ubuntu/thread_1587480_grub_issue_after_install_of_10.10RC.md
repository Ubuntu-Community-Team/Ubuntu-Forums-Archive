---
title: "grub issue after install of 10.10RC"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by crashbang on 2010-10-03
So I have a computer with two sata hard drives. One has windoze and the other had Linux mint. I chose between them at boot with the BIOS. So I installed 10.10 last night over Linux mint and when it told me to reboot I did and picked that hard drive. All I got was a black screen that was unresponsive. So I ran the install again and got the same black unresponsive screen. So I gave up for the night. This morning I booted into the windoze hard drive and there was grub! I chose windoze and immediately checked the disk properties. No missing space taken up by Ubuntu. So I rebooted and chose Ubuntu this time. Checked free space and it was definitely on the correct hard drive separate from windoze. So as far as I can tell that drive has Ubuntu but no boot loader of any kind plus grub is on my windoze drive. How did this happen? How do I fix this? I wasn't planning on always having both these disks together in this computer so something needs to be done. I would appreciate some advice. I don't think this is a bug is it?

---

### Post by jtarin on 2010-10-03
Download and run the BootInfo Script linked in my signature. I have a suspicion you have installed Grub2 in the wrong location.
You could try disconnecting each drive in turn and repairing. Win Loader(MBR) and Grub2.

---

### Post by crashbang on 2010-10-03
Will do as soon as I get home. Thanks!

---

### Post by crashbang on 2010-10-03
Here it is
                ```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdg1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdg5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048   299,808,767   299,806,720  83 Linux
/dev/sdg2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sdg5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1ABCD4F1BCD4C901                       ntfs       System Reserved               
/dev/sda2        9E08D6A108D677AB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdg1        39ab9e94-1460-411f-abda-e539f0de837b   ext4                                     
/dev/sdg2: PTTYPE="dos" 
/dev/sdg5        cbac6e6e-0250-4679-9e3d-d27a2ab20adf   swap                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdg1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdg1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 39ab9e94-1460-411f-abda-e539f0de837b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 39ab9e94-1460-411f-abda-e539f0de837b
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 39ab9e94-1460-411f-abda-e539f0de837b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=39ab9e94-1460-411f-abda-e539f0de837b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 39ab9e94-1460-411f-abda-e539f0de837b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=39ab9e94-1460-411f-abda-e539f0de837b ro single 
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
    search --no-floppy --fs-uuid --set 39ab9e94-1460-411f-abda-e539f0de837b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 39ab9e94-1460-411f-abda-e539f0de837b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1abcd4f1bcd4c901
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

=============================== sdg1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=39ab9e94-1460-411f-abda-e539f0de837b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cbac6e6e-0250-4679-9e3d-d27a2ab20adf none            swap    sw              0       0

=================== sdg1: Location of files loaded by Grub: ===================


  81.7GB: boot/grub/core.img
  90.3GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
  81.7GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
  81.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdg2

00000000  ba 86 e5 c5 f6 92 96 ae  b0 cd 29 69 3d 82 eb ac  |..........)i=...|
00000010  3d 72 e2 d2 d2 7b 50 a8  90 4b 27 8c 15 03 18 00  |=r...{P..K'.....|
00000020  d3 be ae 9c 06 42 bf bb  0b ba 74 1d 0e cd 7d 77  |.....B....t...}w|
00000030  4e 7d 70 e2 0c 3e 6a 56  00 00 01 17 0a 77 31 d9  |N}p..>jV.....w1.|
00000040  39 f3 8a 76 d7 fb 75 75  8e db bf bf d9 1d d6 71  |9..v..uu.......q|
00000050  db b6 c4 f2 7d e5 7e fd  85 ee dc 71 df 0f 9b 9c  |....}.~....q....|
00000060  c4 70 0f c0 67 49 57 67  dd 87 fd f1 12 9d cc 03  |.p..gIWg........|
00000070  f9 f7 1e 77 7c 73 28 49  e6 57 19 f6 c4 f6 3e 2d  |...w|s(I.W....>-|
00000080  bb ec fb 91 c8 84 e6 9c  e4 3f dc 5f ee c1 21 e0  |.........?._..!.|
00000090  6a b3 6d 98 c1 eb 70 66  ff f8 73 3b 0f c3 73 08  |j.m...pf..s;..s.|
000000a0  d8 03 b3 29 cd 59 b9 f6  12 df 7b 4b 77 cd b8 ac  |...).Y....{Kw...|
000000b0  db 71 e3 87 2c 07 f2 76  cc ec 76 53 98 04 cd 3c  |.q..,..v..vS...<|
000000c0  2c 44 9c ca 7f 8f 5f db  ef a4 ec 76 6e 29 f3 39  |,D...._....vn).9|
000000d0  1c 8a 4e a7 73 37 cc 37  f6 65 63 5c 73 3e c6 01  |..N.s7.7.ec\s>..|
000000e0  09 06 a3 65 05 7e 20 c1  51 7f b6 7e c6 a8 60 e5  |...e.~ .Q..~..`.|
000000f0  31 a1 f7 fa 3f dd 2d c0  fb b7 fb 11 c7 00 ba 3d  |1...?.-........=|
00000100  23 85 84 39 02 52 fa 89  07 bf 67 23 80 74 f4 3a  |#..9.R....g#.t.:|
00000110  2f 02 a6 77 8b 39 81 76  11 43 a4 ec fa 1d 16 e5  |/..w.9.v.C......|
00000120  f9 d8 00 73 03 e7 ff d3  bb c0 5f 30 b8 06 4f 4e  |...s......_0..ON|
00000130  f4 2a 9c ce f4 e1 74 e7  c0 3b 88 c7 4a 10 9d 3d  |.*....t..;..J..=|
00000140  3b c0 06 b0 55 3b c5 71  80 3e a7 7c e6 73 1a e1  |;...U;.q.>.|.s..|
00000150  ac 07 57 2e 87 03 99 a7  24 25 09 08 1e 96 66 eb  |..W.....$%....f.|
00000160  01 e0 2a 7f f1 f7 93 92  9d f6 71 d8 66 ff 3e 09  |..*.......q.f.>.|
00000170  1c 38 c3 88 f4 10 c8 1a  1b 94 7f c8 e9 16 46 03  |.8............F.|
00000180  72 7b 2b 7d f0 ff fa 73  87 93 c9 f0 cc fc 27 fe  |r{+}...s......'.|
00000190  3d 5f ee 02 b0 36 3a df  af ff f0 7e 7e 34 92 3d  |=_...6:....~~4.=|
000001a0  5c d0 1f d3 99 83 3e 42  53 b2 11 c7 67 fb f1 c9  |\.....>BS...g...|
000001b0  58 e3 9f 13 e4 f0 94 f5  7c cb fd 19 91 85 00 fe  |X.......|.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf
```

---

### Post by jtarin on 2010-10-03
> => Grub 2 is installed in the MBR of /dev/sda [U]and looks on the same drive in
partition #1 for (,msdos1)/boot/grub.[/U]
=> No boot loader is installed in the MBR of /dev/sdgGrubs looking in the wrong place. You can either boot the Live CD and reinstall Grub to /dev/sdg and run that disk by selection at startup or if you would like to keep Grub from the MBR of /dev/sda entirely you can use the Win 7 bootmanger to boot both Win and Linux.

---

### Post by crashbang on 2010-10-03
I'm a bit confused.  I would like to keep both of these disks separate since I tend to swap hard drives in and out.  How exactly would I install just grub to sdg?

---

### Post by jtarin on 2010-10-03
[Start Here and Read]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")...choose the method that seems best for you. I prefer Method #3 CHROOT. You should disconnect your Win drive to do this. When completed, reboot and try. If all good then reconect Win drive and now you will need to repair the Win MBR. You can use a recovery CD and boot to the recovery console or a Win7 installation disk with the recovery console available on it or EasyBCD as linked in my signature. With the first two you will only boot Win from that disk...with the third you can modify the Win7 boot manager to boot Ubuntu without overwriting your MBR with some other application.

---

### Post by crashbang on 2010-10-03
Thank you very much jtarin.  I seem to remember reading that page a good 6 months or so ago.  I used the chroot and it worked great!  Now, on to fix windoze for the wifey.:rolleyes:  Now, if I only knew why this happened.

---

### Post by jtarin on 2010-10-03
I've got mine finally using Ubuntu, as long as she can open a browser and read email and socialize...she doesn't have a clue (not much of one). I've installed MS office under Wine but can't get Adobe 9 Pro going yet.

---

### Post by oldfred on 2010-10-04
Either grub or the boot script mis identify the drive. Your install of grub in sda will boot the install in sdb. Mine says it is in partition 7 in same drive and it really is in sdc7 and I only have 3 partitions in sda.

Grub defaults to sda unless you tell it otherwise. It used to be an advanced button. I used manual install and it gave me a combo box at the bottom to choose which drive to install to, default was sda.

If you boot into your install you can then install grub2 to sdb from the working install with:

sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb

To recover your windows you will have to either install lilo which works like windows in the MBR or run from windows repair console.
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by barlaventoexpert on 2010-10-04
I have a different problem with Windows 7 Boot Loader and Grub.

Machine: Asus EEE Pc 
160Gb
1Gb Memory
Machine delivered with two partitions C & D (Window World)
Installed OS - Windows 7 Starter Pack

Saturday downloaded Ubuntu 10.10 Rc netbook edition. 

Unetbootin to USB stick, 

Rebooted and installed to D partition.

When machine now boots I get:

1) The Windows 7 boot manager - offering me both Operating Systems.

I can select either.

THEN when I select Ubuntu

2) Grub appears and then I have to again choose Ubuntu between the 2 systems before finally booting into Ubuntu. Ubuntu 10.10 is also booting slowly.

Any ideas?? 

Thanks

---

### Post by oldfred on 2010-10-04
barlaventoexpert since your problem is totally different you should start a new thread. 

It sounds like you installed the wubi version which runs from a file inside the windows NTFS partition. Not sure how much testing has been done with wubi and the release candidate. 

The wubi version uses the windows boot loader to choose which to boot then becomes Ubuntu and shows a grub menu like a normal install.

---

### Post by bcbc on 2010-10-04
> **oldfred said:**
> Either grub or the boot script mis identify the drive. 

It's bootinfoscript... we need meierfra back to update it or someone else to pick up the reigns. Whatever happened to meierfra anyway?

---

### Post by crashbang on 2010-10-08
> **oldfred said:**
> Either grub or the boot script mis identify the drive. Your install of grub in sda will boot the install in sdb.

Grub defaults to sda unless you tell it otherwise. 

BootRec.exe /fixmbr   #updates MBR master boot record 

This is what must have happened. I did not choose anything other than which hard drive to overwrite. Thanks for your help!

---

### Post by jtarin on 2010-10-08
I believe thats what I said somewhat earlier in this post. You might mark as solved.

---

### Post by crashbang on 2010-10-08
> **jtarin said:**
> I believe thats what I said somewhat earlier in this post. You migh mark as solved.

It is. I just forgot to come back and say what worked and that my issue was solved. Thanks again. You are a gentleman and a scholar.

---

### Post by jtarin on 2010-10-08
Your more than welcome. I'm glad to see you have things in order.

---

### Post by crashbang on 2011-03-10
The easiest thing to do would be to reinstall Ubuntu. You should check the md5 of your Ubuntu ISO. I had the same problem because the ISO wasn't correct. If it doesn't check right redownload Ubuntu

---

