---
title: "ANOTHER: GRUB- error: no such partition grub rescue&gt;"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by meneedhelp on 2011-03-30
Hi guys,
sorry if i joined this forum just for asking something to solve my problem.
i have problems with my pc. it won't load. before it only showed the message just like this:

GRUB- error: no such partition grub rescue>

But now, after (almost) everything possibly i could do to work this thing again.. there's only:
BLANK SCREEN.

Maybe i need to tell the chronology here:

1. I uninstalled my Ubuntu 10.10. Also, deleted all of my partition (D, E) , except C.
2. Then when i restarted the PC, the grub-error appeared. 
3.  Since, i had this problem before with my Windows XP, i thought i know  how to fix this. Then i tried running Windows 7 Live CD to enter the  command prompt. Then i typed this: FIXBOOT and FIXMBR. Restarted it,  but, nothing happened.
4. I tried also BOOTREC.EXE /FIXMBR and BOOTREC.EXE /FIXMBR. Still, nothing happened.
5.  I tried to re-install Ubuntu 10.10. It appeared, just fine. The Ubuntu  ran well. But my Windows 7 still won't load. Only blank screen.
6. I  tried to make partition out of my Unallocated memory and made it in NTFS  format. I ran GParted Live CD. Still nothing happened with my Windows  7.
6. Last, i tried another suggestion just like from [here]("http://superuser.com/questions/74017/grub-error-after-deleting-linux-partition"): BOOTSECT /NT60 ALL and now even the Ubuntu won't load too. Only gives me BLANK SCREEN.

Please, help me! I would appreciate anyone who could fix the problem.

Thanks in advance. :)

---

### Post by coffeecat on 2011-03-30
Hi and welcome to the forum.

We need to see exactly how your hard drive is configured. Fortunately, there's a utility that makes this easy. Boot up with the live Ubuntu CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file within [noparse]```
 and 
```[/noparse] tags as described on that page. Then we can take it from there.

---

### Post by meneedhelp on 2011-03-30
wow..
thanks for the response Mr Coffeecat :)
sorry for the late reply, since i was figuring out how to reconnect my PC to the internet since im new to linux and only have only 1 modem, no wifi router or so on here at my house.. :confused:

btw hopefully this is what u are asking..
pls advice. thanks a lot! :)


```

                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   105,081,164   105,081,102   7 HPFS/NTFS
/dev/sda2         105,082,878   134,377,471    29,294,594   5 Extended
/dev/sda5         105,082,880   134,377,471    29,294,592  83 Linux
/dev/sda3         134,377,472   312,580,095   178,202,624   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CBEC871217F090                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7BC2BDD16B6B3DA5                       ntfs                                     
/dev/sda5        e3e8b783-b1ee-425f-8167-4037d5a77517   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F46F-A91A                              vfat       LUCKY                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)


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
search --no-floppy --fs-uuid --set e3e8b783-b1ee-425f-8167-4037d5a77517
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set e3e8b783-b1ee-425f-8167-4037d5a77517
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e3e8b783-b1ee-425f-8167-4037d5a77517
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e3e8b783-b1ee-425f-8167-4037d5a77517 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e3e8b783-b1ee-425f-8167-4037d5a77517
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e3e8b783-b1ee-425f-8167-4037d5a77517 ro single 
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
    search --no-floppy --fs-uuid --set e3e8b783-b1ee-425f-8167-4037d5a77517
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e3e8b783-b1ee-425f-8167-4037d5a77517
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cbec871217f090
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
UUID=e3e8b783-b1ee-425f-8167-4037d5a77517 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  58.5GB: boot/grub/core.img
  62.6GB: boot/grub/grub.cfg
  64.9GB: boot/initrd.img-2.6.35-22-generic
  54.3GB: boot/vmlinuz-2.6.35-22-generic
  64.9GB: initrd.img
  54.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  01 4b 77 00 c4 1d 00 00  00 00 00 00 02 00 00 00  |.Kw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 1a a9 6f f4 4e  4f 20 4e 41 4d 45 20 20  |..)..o.NO NAME  |
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
00000110  c6 06 45 7d 00 66 b8 c0  af 00 00 66 ba 00 00 00  |..E}.f.....f....|
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

### Post by coffeecat on 2011-03-30
At the moment you have Windows code installed to the mbr, the Windows 7 boot files seem to be present in the Windows C: partition sda1, and the boot flag is set in sda1. Which all means that Windows *should* boot when you switch on. But it doesn't.

I suggest you run chkdsk on the Windows C: partition from the Windows DVD or repair CD to see if the filesystem is corrupted.

This might (or might not) fix Windows. The other problem you have is that grub is not installed to the mbr, so you don't get the grub menu and you can't boot Ubuntu. To fix this, you could boot up with the Ubuntu live CD and choose "try Ubuntu" to get the live desktop. Now open a terminal, and...

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Your grub.cfg file looks satisfactory, so that should get you booting Ubuntu again. But not necessarily Windows. The Windows grub.cfg entry is correct but until you repair whatever is affecting Windows, you won't be able to boot into Windows, whether from the Windows mbr code or from grub. However, I suggest you concentrate on trying to get  Windows booting before you reinstall grub.

I'll pm a couple of people to see if I've missed anything.

---

### Post by meneedhelp on 2011-03-30
Finally I solved it! :biggrin:

thank u mr coffeecat! :popcorn::KS :beer:
i didnt know what else to do w/out ur help!
this solves my Ubuntu problem.. :)

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```but later i found another way to solve the other problem, which was the Windows 7.
so this is what i run on the command prompt:
```


[LIST]
[*]bcdedit /export C:\BCD_Backup
[*]c:
[*]cd boot
[*]attrib bcd -s -h -r
[*]ren c:\boot\bcd bcd.old
[*]bootrec /RebuildBcd
[/LIST]
[source]("http://support.microsoft.com/kb/927392")

```i hope i could contribute something in this forum in the future :)

---

### Post by Quackers on 2011-03-30
Well done! :-)
It seems your BCD was corrupt or damaged.

---

### Post by coffeecat on 2011-03-30
@meneedhelp, I'm glad things are fixed and congratulations on finding that BCD fix.

It's ironic really. Sometimes people come on these forums complaining how complicated Linux is and how you have to use difficult terminal commands. But just compare the two lines of terminal code I gave you to fix grub, and the stuff that you had to type into the Windows command prompt to rebuild bcd. :)

---

