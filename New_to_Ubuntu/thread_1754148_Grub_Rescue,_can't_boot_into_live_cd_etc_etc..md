---
title: "Grub Rescue, can't boot into live cd etc etc."
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Magrek on 2011-05-09
Alright. 

I have a notebook (HP 8510p). On this unit is Windows 7 64bit installed on a partition, on another partition I had an old version of ubuntu. 

I decided to install the latest version of ubuntu by using a usb stick, and overwriting the old ubuntu install (following the installer).

I succesfully installed, was asked to reboot and ended up with "error: no such partition. grub rescue>"

For some strange reason, I cant boot ununtu from the usb stick (I get stuck at the graphical loading screen.) so I basicly can't do any of the answers that are posted in the average grub rescue thread. I don't have a cd/dvd drive in my notebook. Reinstalling ubuntu on the usb stick and trying again on my notebook also doens't work.

Help? 

Thanks!

---

### Post by jtarin on 2011-05-09
> **Magrek said:**
> Alright. 

I have a notebook (HP 8510p). On this unit is Windows 7 64bit installed on a partition, on another partition I had an old version of ubuntu. 

I decided to install the latest version of ubuntu by using a usb stick, and overwriting the old ubuntu install (following the installer).

I succesfully installed, was asked to reboot and ended up with "error: no such partition. grub rescue>"

For some strange reason, I cant boot ununtu from the usb stick (I get stuck at the graphical loading screen.) so I basicly can't do any of the answers that are posted in the average grub rescue thread. I don't have a cd/dvd drive in my notebook. Reinstalling ubuntu on the usb stick and trying again on my notebook also doens't work.

Help? 

Thanks!

What does this graphical loading screen look like?

---

### Post by wilee-nilee on 2011-05-09
So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

If the thumb is booting the setup grub was put in its mbr. sounds like the perfect set up for a special 3rd party bootloader I will let jtarin suggest.;) Let me say I wont argue with jtarin, that is, is what I mean.

Post the script it will help them and all of us.

---

### Post by jtarin on 2011-05-09
> **wilee-nilee said:**
> So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

If the thumb is booting the setup grub was put in its mbr. sounds like the perfect set up for a special 3rd party bootloader I will let jtarin suggest.;) Let me say I wont argue with jtarin, that is, is what I mean.

Post the script it will help them and all of us.Good idea...the boot script. I just want to get an idea of what the "graphical loading screen" is, but agreed Grub can't find something.

---

### Post by Magrek on 2011-05-09
Sadly enough, I can't boot from a thumbdrive. Everything goes fine until I get to the loading screen posted below. it keeps "loading". Waited 30minutes or so before rebooting and giving up hope in mankind.

[IMG]http://dl.dropbox.com/u/1175523/DSC_1373.jpg[/IMG]

As you can see, besides fixing the bootloader, I also need to clean my screen.

---

### Post by wilee-nilee on 2011-05-09
Argh laddy we be ah waitin for thee bootscript, now walk the plank.;)

---

### Post by jtarin on 2011-05-09
You say the latest version of Ubuntu.....do you mean 11.04 and what was your older version that worked with this computer?

[Possibly a verbose output would help define the snag.]("http://ubuntuforums.org/showthread.php?t=416604")

---

### Post by Magrek on 2011-05-09
I think there is some sort of mixup due to my lack of paying any attention during english at school. Or i'm just confused, in which case you can ignore this.

-Booting my computer from harddisk results in "error: no such partition. grub rescue>"
-Booting my computer from usb thumdrive into a "live demo" or however you call it, results in staring at the posted screen for eternal time. 

I can however load into the setup to install ubuntu from the thumbdrive. 

On the usb thumbdrive and somewhere on a partition on my computer harddisk is 11.04 standing. The previous version on my computer hard drive was 10.10.

---

### Post by Magrek on 2011-05-09
Somehow i managed to boot on a live thumdrive iso.

Per request the results.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for cbdc4.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,771,119   976,771,057  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   913,856,511   913,649,664   7 HPFS/NTFS
/dev/sdb3         913,858,558   976,771,071    62,912,514   5 Extended
/dev/sdb5         913,858,560   968,517,631    54,659,072  83 Linux
/dev/sdb6         968,519,680   976,771,071     8,251,392  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          1,128     7,831,551     7,830,424   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        68009BF5009BC888                       ntfs       System Reserved               
/dev/sdb2        7854A5F354A5B472                       ntfs       Local Disk                    
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        1a6f04dd-bd25-4ce6-afc0-92fc981619b0   ext4                                     
/dev/sdb6        b75091ff-bccf-4311-b69a-4da378a59b50   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0915-2E37                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 1a6f04dd-bd25-4ce6-afc0-92fc981619b0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 1a6f04dd-bd25-4ce6-afc0-92fc981619b0
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
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a6f04dd-bd25-4ce6-afc0-92fc981619b0
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a6f04dd-bd25-4ce6-afc0-92fc981619b0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a6f04dd-bd25-4ce6-afc0-92fc981619b0
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a6f04dd-bd25-4ce6-afc0-92fc981619b0 ro single 
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
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a6f04dd-bd25-4ce6-afc0-92fc981619b0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 1a6f04dd-bd25-4ce6-afc0-92fc981619b0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 68009BF5009BC888
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=1a6f04dd-bd25-4ce6-afc0-92fc981619b0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b75091ff-bccf-4311-b69a-4da378a59b50 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 474.5GB: boot/grub/core.img
 493.8GB: boot/grub/grub.cfg
 476.8GB: boot/initrd.img-2.6.38-8-generic
 474.5GB: boot/vmlinuz-2.6.38-8-generic
 476.8GB: initrd.img
 474.5GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 68 04 00 00  |........?...h...|
00000020  98 7b 77 00 83 3b 00 00  00 00 00 00 02 00 00 00  |.{w..;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 37 2e 15 09 4e  4f 20 4e 41 4d 45 20 20  |..)7...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 2a  77 00 00 66 ba 00 00 00  |..E}.f.*w..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-05-09
Yay, taker away jtarin.;)

---

### Post by jtarin on 2011-05-09
> **wilee-nilee said:**
> Yay, taker away jtarin.;)
Ha,ha!! Yea thanks wilee. :p 
What was originally installed on this computer when it had one drive?

---

### Post by Magrek on 2011-05-09
A nightmare called Windows Vista.

---

### Post by jtarin on 2011-05-09
Are you still able to boot into Windows at all? If yes look to my signature and download the newest version of EasyBCD. Once you have that downloaded and installed let me know.

---

### Post by Magrek on 2011-05-10
Can't boot into windows. :(

---

### Post by jtarin on 2011-05-10
Why can you not boot into Windows?
Did you change the boot order of devices in the bios to enable USB boot?

---

### Post by Magrek on 2011-05-10
If i try to boot, i get to grub rescue, unless there is a way to force me to my windows 7 install. 

Boot order on my BIOS is:

1 - USB Hard Disk
2 - Notebook Hard disk
3 - CD drive (that's the second Hard Disk in my case)
4- USB CD drive

---

### Post by jtarin on 2011-05-10
Your going to have to get a bootable medium to reach one of your operating systems.
Where did you get your instructions for Ubuntu USB stick?
Here's one for Windows?

---

### Post by Magrek on 2011-05-10
To create a ubuntu on a thumbdrive i followed the instructions that are on the [URL="http://www.ubuntu.com/download/ubuntu/download"]ubuntu
[/URL] website.

I recreated the thumbdrive, and now I'm back able to boot from it.

---

### Post by jtarin on 2011-05-10
> **Magrek said:**
> To create a ubuntu on a thumbdrive i followed the instructions that are on the [URL="http://www.ubuntu.com/download/ubuntu/download"]ubuntu
[/URL] website.

I recreated the thumbdrive, and now I'm back able to boot from it.Now that you can boot into an Ubuntu desktop you can try to reinstall Grub. This would be a good time to decide if you want to leave Grub on the MBR location or on your Linux partition and use something like your Windows boot manager to chain load Grub. To do either all you need is to reinstall Grub properly. To do the latter you will need boot medium to boot Windows.

---

