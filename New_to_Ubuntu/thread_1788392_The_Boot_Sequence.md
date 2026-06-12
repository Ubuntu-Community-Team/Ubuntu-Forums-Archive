---
title: "The Boot Sequence"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by LittleGyko on 2011-06-22
My boot sequence has the following order:

1. External hard drive
2. CD
3. Hard drive

When I had switched my computer on, there was an external hard drive plugged into it which contained only movies. Thus, I was getting the error "BOOTMGR IS MISSING". After some time and searching on the internet, I realised that the computer was not finding the boot file on the hard drive. On removing the hard drive and restarting, everything worked absolutely fine.

This brings me to the following question. Since the boot file was not found in the external hard drive, why did the computer stop searching for it there. Why did it not go on to check in the other places. Is there some way this can be arranged?

Thanks in advance.

---

### Post by jerrrys on 2011-06-22
change your boot order.  internal hdd #1; cd #2; usb #3

---

### Post by Mark Phelps on 2011-06-22
What you're claiming SHOULD be the case; why it is not with your PC is a mystery.

You could also try inserting a non-bootable CD into the CD drive and seeing if the boot sequence continues past that to the hard drive without your intervention.  At least, that's what it does on all the PCs I've used.

---

### Post by LittleGyko on 2011-06-22
Thanks. I'll do some experiments and post the results.

---

### Post by oldfred on 2011-06-22
Bootmgr is missing is a windows boot error, not BIOS. So you booted.

Do you have an old Windows MBR in the external?

If you want to see what is where with everything plugged in:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jtarin on 2011-06-22
If you can still somehow fire up Linux  you can simply invoke "dd", like so:

```
dd if=/dev/zero of=/dev/sdx bs=512 count=1
```

**If in doubt, get a backup copy before by running this:**

```
dd if=/dev/sdx of=/root/mymbrbackup.img bs=512 count=1 
```

Yep, that's it. That MBR is gone. Obviously, you have to be root to do this.**_Run "oldfred's" boot script to locate exactly where the "of=/dev/sdx" part should point to_**.....which should be your MBR of your external drive....... and modify the command accordingly. For example..../dev/sda, /dev/sdb...etc.

---

### Post by LittleGyko on 2011-06-23
My laptop is on a dual boot with Windows and ubuntu 10.04. 

The external hard drive belongs to my friend who uses windows, and so it would have been a windows file system. Could that be the reason for the error? 

Thanks

---

### Post by jtarin on 2011-06-23
No....as oldfred suggested run the bootscript or just keep guessing.

---

### Post by LittleGyko on 2011-06-23
Oops! Sorry. Is it possible to delete a reply?

---

### Post by LittleGyko on 2011-06-23
The output of running the script in the link given by  oldfred is 

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       273,104       273,042  de Dell Utility
/dev/sda2    *        274,432    20,021,247    19,746,816   7 NTFS / exFAT / HPFS
/dev/sda3          20,021,248   143,986,687   123,965,440   7 NTFS / exFAT / HPFS
/dev/sda4         143,986,699   625,137,344   481,150,646   5 Extended
/dev/sda5         143,988,736   190,884,329    46,895,594  83 Linux
/dev/sda6         190,884,393   619,273,619   428,389,227  83 Linux
/dev/sda7         619,273,683   625,137,344     5,863,662  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B643-1278                              vfat       
/dev/sda2        52B44479B4446219                       ntfs       RECOVERY
/dev/sda3        2C2A46692A462FDE                       ntfs       OS
/dev/sda5        8bd64e6b-73e6-482c-9ce4-d830c96cc66b   ext4       
/dev/sda6        f86f588f-4496-4057-ae76-c5d85d375471   ext4       
/dev/sda7        cf1e34da-8fb9-471d-bb2b-46947cf749ff   swap       
/dev/sdb1        407ABA2E7ABA2118                       ntfs       ADATA CH11

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw,user_xattr)
/dev/sdb1        /media/ADATA CH11        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b ro   
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b ro   
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b ro   
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8bd64e6b-73e6-482c-9ce4-d830c96cc66b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 52b44479b4446219
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8bd64e6b-73e6-482c-9ce4-d830c96cc66b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=f86f588f-4496-4057-ae76-c5d85d375471 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=cf1e34da-8fb9-471d-bb2b-46947cf749ff none            swap    sw              0       0
UUID=f86f588f-4496-4057-ae76-c5d85d375471 /home ext4 defaults,user_xattr 0 2
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  70.784206390 = 76.003962880   boot/grub/core.img                             1
  71.737407684 = 77.027454976   boot/grub/grub.cfg                             2
  74.498828888 = 79.992508416   boot/initrd.img-2.6.32-23-generic-pae          1
  74.506202698 = 80.000425984   boot/initrd.img-2.6.32-24-generic-pae          1
  74.336795807 = 79.818526720   boot/initrd.img-2.6.32-26-generic-pae          1
  71.088787079 = 76.331003904   boot/vmlinuz-2.6.32-23-generic-pae             1
  74.194313049 = 79.665537024   boot/vmlinuz-2.6.32-24-generic-pae             1
  74.069313049 = 79.531319296   boot/vmlinuz-2.6.32-26-generic-pae             1
  74.336795807 = 79.818526720   initrd.img                                     1
  74.506202698 = 80.000425984   initrd.img.old                                 1
  74.069313049 = 79.531319296   vmlinuz                                        1
  74.194313049 = 79.665537024   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 04 f4 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  92 2a 04 00 06 02 00 00  00 00 00 00 02 00 00 00  |.*..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 78 12 43 b6 4e  4f 20 4e 41 4d 45 20 20  |..)x.C.NO NAME  |
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

Unknown BootLoader on sda4

00000000  31 54 72 61 79 20 2a 50  61 67 65 53 69 7a 65 20  |1Tray *PageSize |
00000010  45 78 65 63 75 74 69 76  65 0d 0a 2a 55 49 43 6f  |Executive..*UICo|
00000020  6e 73 74 72 61 69 6e 74  73 3a 20 2a 49 6e 70 75  |nstraints: *Inpu|
00000030  74 53 6c 6f 74 20 31 54  72 61 79 20 2a 50 61 67  |tSlot 1Tray *Pag|
00000040  65 53 69 7a 65 20 46 0d  0a 2a 55 49 43 6f 6e 73  |eSize F..*UICons|
00000050  74 72 61 69 6e 74 73 3a  20 2a 49 6e 70 75 74 53  |traints: *InputS|
00000060  6c 6f 74 20 31 54 72 61  79 20 2a 50 61 67 65 53  |lot 1Tray *PageS|
00000070  69 7a 65 20 46 6f 6c 69  6f 0d 0a 2a 55 49 43 6f  |ize Folio..*UICo|
00000080  6e 73 74 72 61 69 6e 74  73 3a 20 2a 49 6e 70 75  |nstraints: *Inpu|
00000090  74 53 6c 6f 74 20 31 54  72 61 79 20 2a 50 61 67  |tSlot 1Tray *Pag|
000000a0  65 53 69 7a 65 20 46 61  6e 46 6f 6c 64 47 65 72  |eSize FanFoldGer|
000000b0  6d 61 6e 4c 65 67 61 6c  0d 0a 2a 55 49 43 6f 6e  |manLegal..*UICon|
000000c0  73 74 72 61 69 6e 74 73  3a 20 2a 49 6e 70 75 74  |straints: *Input|
000000d0  53 6c 6f 74 20 31 54 72  61 79 20 2a 50 61 67 65  |Slot 1Tray *Page|
000000e0  53 69 7a 65 20 38 4b 61  69 0d 0a 2a 55 49 43 6f  |Size 8Kai..*UICo|
000000f0  6e 73 74 72 61 69 6e 74  73 3a 20 2a 49 6e 70 75  |nstraints: *Inpu|
00000100  74 53 6c 6f 74 20 31 54  72 61 79 20 2a 50 61 67  |tSlot 1Tray *Pag|
00000110  65 53 69 7a 65 20 31 36  4b 61 69 0d 0a 2a 55 49  |eSize 16Kai..*UI|
00000120  43 6f 6e 73 74 72 61 69  6e 74 73 3a 20 2a 49 6e  |Constraints: *In|
00000130  70 75 74 53 6c 6f 74 20  32 54 72 61 79 20 2a 50  |putSlot 2Tray *P|
00000140  61 67 65 53 69 7a 65 20  41 36 0d 0a 2a 55 49 43  |ageSize A6..*UIC|
00000150  6f 6e 73 74 72 61 69 6e  74 73 3a 20 2a 49 6e 70  |onstraints: *Inp|
00000160  75 74 53 6c 6f 74 20 33  54 72 61 79 20 2a 50 61  |utSlot 3Tray *Pa|
00000170  67 65 53 69 7a 65 20 41  36 0d 0a 2a 55 49 43 6f  |geSize A6..*UICo|
00000180  6e 73 74 72 61 69 6e 74  73 3a 20 2a 49 6e 70 75  |nstraints: *Inpu|
00000190  74 53 6c 6f 74 20 34 54  72 61 79 20 2a 50 61 67  |tSlot 4Tray *Pag|
000001a0  65 53 69 7a 65 20 41 33  0d 0a 2a 55 49 43 6f 6e  |eSize A3..*UICon|
000001b0  73 74 72 61 69 6e 74 73  3a 20 2a 49 6e 70 00 fe  |straints: *Inp..|
000001c0  ff ff 83 fe ff ff f5 07  00 00 ea 91 cb 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff df 99  cb 02 aa b3 88 19 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-06-23
Yep, you have a windows boot loader in the MBR of sdb, but no windows.

Windows is installed in the MBR of /dev/sdb.

Best to just change boot order to boot internal first. If you need CD then use one time boot key to boot a CD.

---

### Post by LittleGyko on 2011-06-23
Thanks a lot.

---

