---
title: "ms-sys corrupted my partition or bootsector! can't boot"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by jpmutanguha on 2009-12-04
Yesterday, i tried removing GRUB but i didn't have the windows recovery cd, so i tried using ms-sys because its said to have the same functionality. i ran this on 7.10 LiveCD
```

ms-sys -p /dev/sda1
ms-sys -m /dev/sda1

```
i didn't notice the error that comes when you run this! i restarted, but it went black n refused to shutdown, i forced shutdown and when i switched it on, windows wouldn't boot!i went back n now ran
```

ms-sys -p /dev/sda1
ms-sys -m /dev/sda

```
which gave a "successful" message. but windows still won't boot. i then went on to try and fix it using testdisk, ultimate boot cd, MBRfix, all in vain, and each time i used them either through LiveCD or UBCD, the computer wouldn't shutdown properly!after a 2-day struggle, i decided to format my windows partition with my windows xp cd(doesn't have recovery option), but even xp install wouldn't complete cause it still can't boot!NOw my last hope is gone!
In the end, i found a way to load the recovery console through USB, but neither fixboot nor fixmbr fixed it! I'm not sure what exactly is wrong with my windows partition!i've installed ubuntu 9.10, n Grub recognises Windows but selecting it just brings a black screen.i can access all my partitions on ubuntu,but when i run the ubuntu partition manager in the LiveCD, the NTFS partions don't load properly.i really need to fix it!and my harddisk wasn't showing any failure before yesterday.

---

### Post by ST3ALTHPSYCH0 on 2009-12-04
Download a copy of Super Grub Disk [here](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso). Boot from it. It has an option to restore the windows MBR.

---

### Post by jpmutanguha on 2009-12-04
thanks. i currently don't have an blank cd, but i'm gonna try the USB option i've found on their website!

---

### Post by jpmutanguha on 2009-12-04
i used the Fix Boot of Windows, after the Compaq(manufacturer) logo, there's a blinking cursor in a black background...before i run super grub disk, the same would happen if i selected windows in the grub menu.

An odd thing is, when i run Windows(Advanced)->Boot Partition of Window, and select the first partition, which i'm definitely positive it contains the NTLDR, it tells me NTLDR missing. When i select the partition that has the "Windows" folder, i get "disk read error"! when i selected the third partition just out of curiousity i got NTLDR missing.

---

### Post by Some Penguin on 2009-12-04
Can you list your partitions via fdisk?

And possibly mount the partition that's supposed to contain the Windows boot drive (where NTLDR should reside), or list the error that mounting gives you if it fails?

---

### Post by jpmutanguha on 2009-12-04
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x040e040d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1898    14346013+   7  HPFS/NTFS
/dev/sda2            1898        2710     6136830    7  HPFS/NTFS
/dev/sda3            2710        5168    18587205    f  W95 Ext'd (LBA)
/dev/sda5            2711        4335    12281692+   7  HPFS/NTFS
/dev/sda6            4336        4475     1052226   82  Linux swap / Solaris
/dev/sda7            4475        5168     5245191   83  Linux

Disk /dev/sdb: 131 MB, 131072000 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00152aa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      127968+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(14, 254, 63) logical=(15, 238, 31)
jp@jp-desktop:~$ 

```i can mount the disk, its the first partition of my hard-disk, here are its contents:
```

jp@jp-desktop:/media/sda1$ ls /media/sda1
AUTOEXEC.BAT            MAGIX            Sean Paul - The Trinity
boot.ini                MSDOS.SYS        Sig6
CONFIG.SYS              My Documents     Sig6.bin
Documents and Settings  NTDETECT.COM     System Volume Information
Downloads               ntldr            ubuntu-9.10-desktop-i386.iso
Drivers                 Program Files    Ubuntu Programs
Eminem                  RECYCLER         WINDOWS
IO.SYS                  restore mbr.rtf  YServer.txt

```

---

### Post by jpmutanguha on 2009-12-04
the microsoft folders you see are just empty residues of the installation that used to be their, but i made sda2 for windows.

---

### Post by jpmutanguha on 2009-12-04
can anyone please help me?

---

### Post by jpmutanguha on 2009-12-05
major breakthrough: I was really desperate to know what's really wrong with the boot process so i deleted my NTLDR to check if its loaded...usually if everything was goin fine i'd get a "NTLDR missing" but nothing happened! its as if i didn't change anything! so wats wrong? why isn't my computer running the windows bootloader?

---

### Post by jpmutanguha on 2009-12-05
From [this]("http://ubuntuforums.org/showthread.php?t=1325873") thread, i found a link to a Boot Info Script...the persons seems to have a slightly similar problem as mine. I ran the script and this is what i got
```

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x445a445a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,692,089    28,692,027   7 HPFS/NTFS
/dev/sda2          28,692,090    40,965,749    12,273,660   7 HPFS/NTFS
/dev/sda3          40,981,815    65,545,199    24,563,385   7 HPFS/NTFS
/dev/sda4          65,545,200    78,156,224    12,611,025   f W95 Ext d (LBA)
/dev/sda5          65,545,263    67,649,714     2,104,452  82 Linux swap / Solaris
/dev/sda6          67,649,778    78,140,159    10,490,382  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="88F2EB10CD0EB400" TYPE="ntfs" 
/dev/sda2: UUID="000008A707CF1A96" TYPE="ntfs" 
/dev/sda3: UUID="28D01D25D01CFAB0" TYPE="ntfs" 
/dev/sda5: UUID="734192b7-ef9f-4f35-97b2-6f4976b76eb3" TYPE="swap" 
/dev/sda6: UUID="133571ef-befd-49fb-859f-fada787d755f" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jp)
/dev/sr1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=jp)
/dev/sr2 on /media/rwandatel data   type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=60 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 133571ef-befd-49fb-859f-fada787d755f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 133571ef-befd-49fb-859f-fada787d755f
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=133571ef-befd-49fb-859f-fada787d755f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 133571ef-befd-49fb-859f-fada787d755f
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=133571ef-befd-49fb-859f-fada787d755f ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 133571ef-befd-49fb-859f-fada787d755f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=133571ef-befd-49fb-859f-fada787d755f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 133571ef-befd-49fb-859f-fada787d755f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=133571ef-befd-49fb-859f-fada787d755f ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 88f2eb10cd0eb400
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=133571ef-befd-49fb-859f-fada787d755f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=734192b7-ef9f-4f35-97b2-6f4976b76eb3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  34.6GB: boot/grub/grub.cfg
  34.6GB: boot/initrd.img-2.6.31-14-generic
  34.6GB: boot/initrd.img-2.6.31-15-generic
  34.6GB: boot/vmlinuz-2.6.31-14-generic
  34.6GB: boot/vmlinuz-2.6.31-15-generic
  34.6GB: initrd.img
  34.6GB: initrd.img.old
  34.6GB: vmlinuz
  34.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  33 c0 8e 4e 54 46 53 20  20 20 20 00 02 08 00 00  |3..NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 09 75 13 83  3a ce b5 01 00 00 00 00  |.....u..:.......|
00000030  00 00 0c 00 00 00 00 00  b2 13 27 00 00 00 00 00  |..........'.....|
00000040  f6 00 00 00 01 00 00 00  00 b4 0e cd 10 eb f2 88  |................|
00000050  00 00 00 00 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |.....s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  44 52 20 69 73 20 63 6f  |.....,DcDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  30 31 77 4e 54 46 53 20  20 20 20 00 02 08 00 00  |01wNTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 7a ce b5 01  |........?...z...|
00000020  00 00 00 00 10 00 00 00  fb 47 bb 00 00 00 00 00  |.........G......|
00000030  00 00 04 00 00 00 00 00  7f b4 0b 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  96 1a cf 07 a7 08 00 00  |................|
00000050  00 00 00 00 10 00 00 00  46 23 cf 07 50 01 00 00  |........F#..P...|
00000060  30 30 64 63 00 00 00 00  9e 24 cf 07 9b 00 00 00  |00dc.....$......|
00000070  30 31 77 62 10 00 00 00  42 25 cf 07 20 01 00 00  |01wb....B%.. ...|
00000080  30 31 77 62 10 00 00 00  6a 26 cf 07 80 01 00 00  |01wb....j&......|
00000090  30 30 64 63 00 00 00 00  f2 27 cf 07 69 0d 00 00  |00dc.....'..i...|
000000a0  30 31 77 62 10 00 00 00  64 35 cf 07 80 01 00 00  |01wb....d5......|
000000b0  30 31 77 62 10 00 00 00  ec 36 cf 07 50 01 00 00  |01wb.....6..P...|
000000c0  30 30 64 63 00 00 00 00  44 38 cf 07 af 00 00 00  |00dc....D8......|
000000d0  30 31 77 62 10 00 00 00  fc 38 cf 07 20 01 00 00  |01wb.....8.. ...|
000000e0  30 30 64 63 00 00 00 00  24 3a cf 07 3e 0c 00 00  |00dc....$:..>...|
000000f0  30 31 77 62 10 00 00 00  6a 46 cf 07 50 01 00 00  |01wb....jF..P...|
00000100  30 31 77 62 10 00 00 00  c2 47 cf 07 20 01 00 00  |01wb.....G.. ...|
00000110  30 30 64 63 10 00 00 00  ea 48 cf 07 01 3c 00 00  |00dc.....H...<..|
00000120  30 31 77 62 10 00 00 00  f4 84 cf 07 20 01 00 00  |01wb........ ...|
00000130  30 31 77 62 10 00 00 00  1c 86 cf 07 20 01 00 00  |01wb........ ...|
00000140  30 30 64 63 00 00 00 00  44 87 cf 07 7e 0d 00 00  |00dc....D...~...|
00000150  30 31 77 62 10 00 00 00  ca 94 cf 07 50 01 00 00  |01wb........P...|
00000160  30 31 77 62 10 00 00 00  22 96 cf 07 50 01 00 00  |01wb...."...P...|
00000170  30 30 64 63 00 00 00 00  7a 97 cf 07 35 02 00 00  |00dc....z...5...|
00000180  30 31 77 62 10 00 00 00  b8 99 cf 07 50 01 00 00  |01wb........P...|
00000190  30 30 64 63 00 00 00 00  10 9b cf 07 6a 0d 00 00  |00dc........j...|
000001a0  30 31 77 62 10 00 00 00  82 a8 cf 07 50 01 00 00  |01wb........P...|
000001b0  30 31 77 62 10 00 00 00  da a9 cf 07 80 01 00 00  |01wb............|
000001c0  30 30 64 63 00 00 00 00  62 ab cf 07 27 01 00 00  |00dc....b...'...|
000001d0  30 31 77 62 10 00 00 00  92 ac cf 07 50 01 00 00  |01wb........P...|
000001e0  30 31 77 62 10 00 00 00  ea ad cf 07 80 01 00 00  |01wb............|
000001f0  30 30 64 63 00 00 00 00  72 af cf 07 df 19 55 aa  |00dc....r.....U.|
00000200

```I think the problem is the boot sectors of sda1 & sda2 appear as "Unknown" but they're supposed to be "Windows XP", and it doesn't recognise my windows operating system...so what do i do now?

---

### Post by jpmutanguha on 2009-12-05
using fixboot i was able to convert boot sector type for both sda1 & sda2 to "Windows XP" but it still doesn't recognise my windows operating system. Please can someone atleast reply?????

---

### Post by oldfred on 2009-12-05
If you installed multiple copies of windows it combines its boot into the copy with the boot flag on (*). That is the only way windows can boot as the boot loader in the MBR just finds the partition with the flag and jumps there (and that is why grub can do that also), The rest of the windows bootloader must be in the PBR and all the windows files ntldr, boot.ini, etc must be present for windows to work.

Your fixboot should have worked. Are any of the windows boot files missing that fixboot did not replace?

---

### Post by jpmutanguha on 2009-12-05
the boot files i know are: ntldr, NTDETECT.COM, and boot.ini...none of them were ever damaged! I even deleted them, to see if an "NTLDR missing" error on boot but nothing happened! I've put them back, but nothing seems to work! u just gave me an idea, what if i change the active partition and installed windows again! i hope this works...any other ideas that might help?

---

### Post by oldfred on 2009-12-05
When you reinstall windows you will also have to reinstall grub after you are sure windows is working.

When you ran the fixboot, did you run fixmbr. That will also require grub to be reinstalled but it may do more than just overwrite the MBR? Usually to fix windows you have to run both.

---

### Post by jpmutanguha on 2009-12-05
changing active partition didn't change anything! currently i have no active partition but Grub still load normally! testdisk says my disk is ok, but when i tried running GParted it said sda1 and sda5 have a single bad sector each and i can't do anything with it till its fixed, and Ubuntu's Disk Utility(Palimpsest) program also confirms i have 2 bad sectors in my harddisk! i think ill to run chkdsk, and then try to format the windows partition completely! don't see myself using it again anytime soon though :(, i've been on the computer for 3days non stop and the only thing i know is, my computer isn't even trying to load ntldr otherwise an error would have occurred when i tried booting windows after deleting ntldr,boot.ini,and ntdetect.com. Does anyone know why my computer isn't loading Windows Bootloader(ntldr)? Thanks to those who've tried to help so far.

---

### Post by jpmutanguha on 2009-12-07
i was able to think of a tiny solution/fix...i edited boot.ini file of the usb flash disk i was using to run the recovery console to look like this:
```

[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows

[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="1ST TRY THIS" /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\Windows="2ND TRY THIS" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS" /fastdetect
multi(0)disk(0)rdisk(1)partition(2)\Windows="4TH TRY THIS" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\Windows="5TH TRY THIS" /fastdetect
multi(0)disk(0)rdisk(1)partition(3)\Windows="6TH TRY THIS" /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\Windows="7TH TRY THIS" /fastdetect
multi(0)disk(0)rdisk(1)partition(4)\Windows="8TH TRY THIS" /fastdetect
C:\="9TH TRY THIS"
D:\="10TH TRY THIS"

```
The first entry was already there to load the recovery console, the others i added...the fourth one worked, i was able to load windows and complete the xp installation i'd started before. so my problem is my computer doesn't load ntldr to load windows, so i need the help of a flash disk to do so. now i'm going to get a floppy disk and then place the ntldr, NTDETECT.COM, boot.ini in it and will always keep it in the drive, and removing it when i want to load Grub i.e. ubuntu...i'm doing all this simply because i need windows to watch movies, they pause alot when i watch them on ubuntu, problem with my graphics card i think. i'll set the thread as solved next week because honestly i don't think its solved. if anyone knows why my computer isn't loading the ntldr on c:\ can they tell me, solution is always in the cause of the problem ;)

---

### Post by oldfred on 2009-12-07
I think it is saying it did not install the boot loaders to the partition and that you are ineffect using the USB to boot and then your windows install is ok in sda2. You had the boot flag on sda1 and that probably was the partition the fixboot repaired. Move the boot flag to sda2 and rerun the fixboot commands and see if that solves the problem. 

You can rerun the script to quickly check what is in the MBR and PBR of your windows partitions. My working windows boot looks like this from the result.txt:

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

---

