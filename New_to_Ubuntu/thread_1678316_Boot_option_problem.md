---
title: "Boot option problem"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by praveenig on 2011-01-30
I have windows 7 installed on primary partition. I recently installed ubuntu 10.10 on a logical partition of the same harddisk(I have only one hard disk of 320gb).
After completion of ubutnu installation it asked for a reboot and cd came out.At that time some input output error was shown(I could not read it. It was bit fast).When the pc restarted i see no options to boot from ubuntu and pc automatically boots to windows 7.Even in boot options(msconfig) i see only windows 7.please help me with this.

Thanks in advance

---

### Post by sikander3786 on 2011-01-30
Welcome to the forums :-)

For diagnosing your problem, we want you to boot Ubuntu Live CD once more and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would let us know about any problems related to your Ubuntu boot loader and thus we'll be able to advise more efficiently.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Rubi1200 on 2011-01-30
+1 to the boot script.

It will really help us to help you.

Thanks.

---

### Post by praveenig on 2011-01-30
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 18. But according to the info from fdisk, 
                       sda6 starts at sector 168024258.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 4. But according to the info from fdisk, 
                       sda7 starts at sector 272881444.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
18 heads, 4 sectors/track, 8682534 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848    63,166,463    62,959,616   7 HPFS/NTFS
/dev/sda3          63,166,525   625,137,344   561,970,820   f W95 Ext d (LBA)
/dev/sda5          63,166,527   168,023,834   104,857,308   7 HPFS/NTFS
/dev/sda6         168,024,258   272,881,439   104,857,182   7 HPFS/NTFS
/dev/sda7         272,881,444   356,764,535    83,883,092   7 HPFS/NTFS
/dev/sda8         377,736,408   482,592,599   104,856,192   7 HPFS/NTFS
/dev/sda9         482,592,663   625,137,344   142,544,682   7 HPFS/NTFS
/dev/sda10        362,735,616   377,735,167    14,999,552  83 Linux
/dev/sda11        356,765,696   362,733,567     5,967,872  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       0c71d137-c3b2-4009-8401-911d47fad3fa   ext4                                     
/dev/sda11       a92d6aee-9b1a-4abc-969c-c170b8ca5cde   swap                                     
/dev/sda1        E02CCA882CCA58E4                       ntfs       System Reserved               
/dev/sda2        4278818578817905                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        BAE8B126E8B0E235                       ntfs       virtual                       
/dev/sda6        86646FB0646FA1A3                       ntfs       movies                        
/dev/sda7        2C84B8AB84B87942                       ntfs       New Volume                    
/dev/sda8        DE187B9F187B757D                       ntfs       dono                          
/dev/sda9        0C94809194807F48                       ntfs       softy                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda8        /media/dono              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set 0c71d137-c3b2-4009-8401-911d47fad3fa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set 0c71d137-c3b2-4009-8401-911d47fad3fa
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 0c71d137-c3b2-4009-8401-911d47fad3fa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0c71d137-c3b2-4009-8401-911d47fad3fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 0c71d137-c3b2-4009-8401-911d47fad3fa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0c71d137-c3b2-4009-8401-911d47fad3fa ro single 
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
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 0c71d137-c3b2-4009-8401-911d47fad3fa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 0c71d137-c3b2-4009-8401-911d47fad3fa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e02cca882cca58e4
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 4278818578817905
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

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda10      /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=a92d6aee-9b1a-4abc-969c-c170b8ca5cde none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 190.6GB: boot/grub/core.img
 190.6GB: boot/grub/grub.cfg
 188.8GB: boot/initrd.img-2.6.35-22-generic
 186.8GB: boot/vmlinuz-2.6.35-22-generic
 188.8GB: initrd.img
 186.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  24 d3 5f 31 ff 7a 99 6a  36 f1 70 a6 bf f1 8e 52  |$._1.z.j6.p....R|
00000010  6d d7 8f 85 b5 8c db 6c  3a e7 17 29 9b 0f 07 e2  |m......l:..)....|
00000020  09 77 dd 2d c8 76 24 87  0e 87 e2 44 97 df 4c 38  |.w.-.v$....D..L8|
00000030  10 00 e7 bf fb ef 75 97  a9 d2 eb 9f b1 e3 e2 ff  |......u.........|
00000040  7f e3 e5 74 4a ef ea cb  0b cf 0f e0 07 c0 de d1  |...tJ...........|
00000050  a5 c3 e1 26 17 db 2c e3  0f 2f 2e f7 a8 93 e5 0c  |...&..,../......|
00000060  bc 18 03 8b 8b f9 25 fc  e1 da 01 c5 ea bf 62 8b  |......%.......b.|
00000070  dc 5f a3 42 fc 24 1f 5f  cc 36 7f ed 35 d3 a2 50  |._.B.$._.6..5..P|
00000080  f4 f8 fb 5e 70 e8 c0 03  10 1c 53 38 19 cb 0d bc  |...^p.....S8....|
00000090  10 e7 c4 ab e1 ec b0 7b  d9 c6 19 7b 9e 3f 8f 35  |.......{...{.?.5|
000000a0  a9 cd fe e1 85 62 45 f5  8a d5 dc a5 ca a2 9b 97  |.....bE.........|
000000b0  b6 05 c0 c2 44 00 d0 86  10 a7 c7 f2 79 58 94 ae  |....D.......yX..|
000000c0  67 95 cb 3a a7 44 46 31  c0 c5 c5 c1 0f ca c4 8b  |g..:.DF1........|
000000d0  07 dd b5 bf 79 69 4c fa  be a8 78 7f 1a b0 81 f5  |....yiL...x.....|
000000e0  56 60 32 85 4a 95 7a fe  6a e9 e9 0a ba ae 8e 93  |V`2.J.z.j.......|
000000f0  6e 23 6c e8 96 a9 52 8c  1f 97 fb 4b b7 31 a5 3f  |n#l...R....K.1.?|
00000100  62 6b 0e 08 20 ca f2 17  da ab de 55 07 90 78 aa  |bk.. ......U..x.|
00000110  51 1b 66 e5 5e d7 d9 2c  95 fd db 1c 3e 80 d6 24  |Q.f.^..,....>..$|
00000120  48 7e cf fd 52 a8 ab d5  47 bd d9 21 5d ac bf 6e  |H~..R...G..!]..n|
00000130  91 e9 2a a1 16 47 3c 5c  5a 09 60 84 3b 6c ce 30  |..*..G<\Z.`.;l.0|
00000140  ed ab 5e 92 0d 84 c1 0c  08 89 5e c4 96 dd b5 72  |..^.......^....r|
00000150  d7 d3 81 f4 62 55 d8 07  32 71 31 37 32 ef cc 7a  |....bU..2q172..z|
00000160  56 b8 ff 5b a7 1e 1f ce  e5 bf 96 b2 4e 0c 5e 08  |V..[........N.^.|
00000170  14 ef ec c9 63 81 a8 07  70 02 e5 34 ad d0 a0 99  |....c...p..4....|
00000180  df c6 aa 26 1e 78 e5 f6  d5 59 6f a4 4d be 16 f3  |...&.x...Yo.M...|
00000190  eb b9 bc 3c 3c 0f 20 a8  8e 98 6b cf ad 06 b4 f0  |...<<. ...k.....|
000001a0  f8 d1 03 6b 41 ac cf 93  58 7d e3 e3 f9 f1 0f af  |...kA...X}......|
000001b0  e1 1b de 30 3a 07 41 8a  28 8a 06 22 c8 74 00 11  |...0:.A.(..".t..|
000001c0  c4 ff 07 11 c4 ff 02 00  00 00 dc fe 3f 06 00 11  |............?...|
000001d0  c4 ff 05 11 c4 ff 73 00  40 06 70 fe 3f 06 00 00  |......s.@.p.?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Quackers on 2011-01-30
Grub is not installed. If you boot from a live cd/usb and choose "try ubuntu" and when the desktop loads, open up a terminal. Then please copy/paste the following lines into the terminal, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda10 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If that reports no errors, reboot your system. Ubuntu should now load directly. When the desktop loads, open a terminal and run
```
sudo update-grub
```
and watch to see that the Windows Loader is picked up. If it is, reboot and choose to boot Windows from the grub menu. (You will possibly get 2 Windows entries in grub menu, see what happens when you try both).

---

### Post by praveenig on 2011-01-31
Thank you very much. It worked like a charm. Now i can boot into both win7 and ubuntu.
But for updating grub its asking password. After all this i have forgotten the password.
Now is there a way to update grub??

I have set not to ask password during boot (or some option like that which it gave during installation)

---

### Post by Quackers on 2011-01-31
No, you'll need the password, I'm afraid!
Glad that the instructions worked though :-)

---

### Post by sikander3786 on 2011-01-31
You can try resetting your password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Make sure you don't forget the new one later ;-)

---

### Post by praveenig on 2011-02-01
Thank you. Will try that.
Will remember the password this time :)

---

