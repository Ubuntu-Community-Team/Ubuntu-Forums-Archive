---
title: "Grub 2 for ubuntu 11.04 and XP on different drives"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by stonecold913 on 2011-07-08
hello i just recently installed Ubuntu 11.04 on one of my HD's. I have WIN XP on another hard drive completely. When i turn on my computer i do not get a grub menu and it goes straight to Ubuntu. I want to know how to get the grub menu to appear and how to get it to see my win XP drive. pls help.

---

### Post by drs305 on 2011-07-08
If everything is installed properly, once you boot into Ubuntu run:
```
sudo update-grub
```

By default, Grub 2 won't display the menu if it thinks there is only one OS. Running this command should force Grub to search for and find your Windows installation and include it in the Grub2 menu. 

Once another OS is found, the Grub menu should display so you have time to select the non-default OS.

---

### Post by stonecold913 on 2011-07-08
when i run the update grub command this is the output

sudjames@james-desktop:~$ sudo update-grub
[sudo] password for james: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Adding Windows
Found memtest86+ image: /boot/memtest86+.bin
done
james@james-desktop:~$ 


but i rebooted and it did not give me a menu and windows did not boot. 

p.s. i used this page before coming here [http://linux.koolsolutions.com/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://linux.koolsolutions.com/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

---

### Post by drs305 on 2011-07-08
Although Grub found Windows, rather than guess why it isn't displaying it would be better to take a look at your boot files.

Please download/extract/run the boot info script from the following site. Post the contents of the RESULTS.txt file it generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

I note that update-grub found Windows before memtest, which is a bit odd since the 'prober' that would normally find Windows would run after the memtest script.

You might try running this just to make sure the os-prober is installed, executable, and working:
```
sudo apt-get install --reinstall os-prober
sudo chmod +x /etc/grub.d/30_os-prober
sudo update-grub
```

---

### Post by stonecold913 on 2011-07-08
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 151276039 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /grub.cfg

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   174,955,141   174,955,079  83 Linux
/dev/sdb2         204,796,681   488,263,544   283,466,864   f W95 Extended (LBA)
/dev/sdb5         204,796,683   488,263,544   283,466,862   7 NTFS / exFAT / HPFS
/dev/sdb3         174,956,544   178,954,239     3,997,696  82 Linux swap / Solaris
/dev/sdb4         178,954,240   204,795,903    25,841,664  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DC907DAF907D90AE                       ntfs       
/dev/sdb1        641e0b5a-7e42-4516-9d36-ee2ece4ab289   ext4       
/dev/sdb3        84c545c9-6010-46d0-9a70-395bffb54935   swap       
/dev/sdb4        63dd08d4-a648-4c01-9a8f-e717b043b05f   ext4       
/dev/sdb5        DCD4EEB4D4EE8FD6                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb4        /home                    ext4       (rw,commit=0)
/dev/sdb5        /media/DCD4EEB4D4EE8FD6  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 641e0b5a-7e42-4516-9d36-ee2ece4ab289
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 641e0b5a-7e42-4516-9d36-ee2ece4ab289
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
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 641e0b5a-7e42-4516-9d36-ee2ece4ab289
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=641e0b5a-7e42-4516-9d36-ee2ece4ab289 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 641e0b5a-7e42-4516-9d36-ee2ece4ab289
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=641e0b5a-7e42-4516-9d36-ee2ece4ab289 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows XP" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 641e0b5a-7e42-4516-9d36-ee2ece4ab289
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 641e0b5a-7e42-4516-9d36-ee2ece4ab289
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=641e0b5a-7e42-4516-9d36-ee2ece4ab289 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=63dd08d4-a648-4c01-9a8f-e717b043b05f /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=84c545c9-6010-46d0-9a70-395bffb54935 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.136008739 = 77.455449600   boot/grub/core.img                             1
   8.336116314 = 8.950836736    boot/grub/grub.cfg                             1
   1.281280041 = 1.375763968    boot/initrd.img-2.6.38-8-generic               2
  72.132335186 = 77.451505152   boot/vmlinuz-2.6.38-8-generic                  1
   1.281280041 = 1.375763968    initrd.img                                     2
  72.132335186 = 77.451505152   vmlinuz                                        1

================================ sdb5/grub.cfg: ================================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940
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
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6a087a8b-7ba5-4ea8-a3c4-aaeee125c940 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6a087a8b-7ba5-4ea8-a3c4-aaeee125c940 ro single 
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
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6a087a8b-7ba5-4ea8-a3c4-aaeee125c940
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

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub.cfg                                       1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```
this is the result.txt

---

### Post by drs305 on 2011-07-08
If sda1 is your normal Windows installation, it is missing all the boot folders/files. 

First, make sure Grub2 is set up properly on sdb. It appears that at least once you tried installing it on the partition instead of the sdb MBR. This is generally not a desirable option. After booting normally into Ubuntu:

Reinstall Grub2 to the MBR of sdb (not on the partition):
```
sudo grub-install /dev/sdb
sudo update-grub
```

Grub2 should now be set up in the sdb MBR. 

Next you will need to use a Windows repair CD to restore the boot files/folders. When you do this, it will remove Grub2 from the sda MBR, which is ok. Once you have repaired Windows, reboot. 

If you BIOS is set up to boot sda first, you should get the Windows bootloader and it will boot only to Windows (which is ok).

If you change the BIOS setup to boot sdb first, you should get Grub/Ubuntu. The first time you boot, you won't see Windows in the menu. After booting, run "sudo update-grub". With the correct Windows boot files in sda1, Grub should now correctly find and include Windows in the menu.

Here is one link on how to restore the Windows bootloader:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by stonecold913 on 2011-07-08
james@james-desktop:~$ sudo chmod +x /etc/grub.d/30_os-prober
james@james-desktop:~$ sudo chmod +x /etc/grub.d/30_os-prober
james@james-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Adding Windows
Found memtest86+ image: /boot/memtest86+.bin
done
james@james-desktop:~$ 


thats also what i got after reinstalling Os prober

---

### Post by drs305 on 2011-07-08
> **stonecold913 said:**
> james@james-desktop:~$ sudo chmod +x /etc/grub.d/30_os-prober
james@james-desktop:~$ sudo chmod +x /etc/grub.d/30_os-prober
james@james-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Adding Windows
Found memtest86+ image: /boot/memtest86+.bin
done
james@james-desktop:~$ 


thats also what i got after reinstalling Os prober

Those are normal returns, but we posted simultaneously. See my previous post, which explains why os-prober isn't 'finding' Windows and how to fix it.

---

### Post by stonecold913 on 2011-07-09
Well now my system won't boot at all. I move the windows drive up in the boot order and it gets stuck at a screen telling me 

Error:no such device : (too much letters and numbers)

Edit: I went back and did fixboot and fixmbr again and now it says NTLDR is missing press CTRL + ALT + DEL to restart
And it is stuck on the boot screen wen I try to boot to the Linux HD

Edit:Edit: i used the link you provided to bring my self back into the linux install drive.

---

### Post by drs305 on 2011-07-09
> **stonecold913 said:**
> Well now my system won't boot at all. I move the windows drive up in the boot order and it gets stuck at a screen telling me 

Error:no such device : (too much letters and numbers)

Edit: I went back and did fixboot and fixmbr again and now it says NTLDR is missing press CTRL + ALT + DEL to restart
And it is stuck on the boot screen wen I try to boot to the Linux HD

Edit:Edit: i used the link you provided to bring my self back into the linux install drive.

I am not a Windows guy so I can't give you precise instructions on how to repair Windows. Normally the way we get both systems working is to concentrate on getting Windows to boot via its own bootloader. Once that is accomplished, it's fairly easy to reinstall Grub2 and get it to take over booting both OS's.

It sounds like you have returned control to sdb and have Grub/Ubuntu working again. Someone with Windows repair experience may happen upon this thread and be able to help you, or you can go to a Windows forum to seek advice on the missing NTLDR issue. You won't be able to get Grub to boot Windows until Windows is capable of booting itself, since all Grub does is transfer control to the Windows bootloader.

---

### Post by oldfred on 2011-07-09
These are the files you need in your windows root sda1 that grub has to find to add it to the boot menu and windows needs to boot.

WinXP
/boot.ini /ntldr /NTDETECT.COM

Windows also needs a valid NTFS partition boot sector which the fixboot command should repair.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by stonecold913 on 2011-07-10
i have successfully fixed the xp bootloader by using 
COPY [CDDRIVE]:\I386\NTLDR C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM C:\

now i just have to figure out how to get grub to pop up with Windows XP. it said that i had a bad boot.ini so i think i may have to fix that.

---

### Post by drs305 on 2011-07-10
> **stonecold913 said:**
> i have successfully fixed the xp bootloader by using 
COPY [CDDRIVE]:\I386\NTLDR C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM C:\

now i just have to figure out how to get grub to pop up with Windows XP. it said that i had a bad boot.ini so i think i may have to fix that.

If you can't figure out the boot.ini issue it's contents are in the boot info script. If you rerun the script and post the results one of the forumites familiar with Windows can probably help you see what's wrong.

---

### Post by drs305 on 2011-07-10
> **stonecold913 said:**
> i have successfully fixed the xp bootloader by using 
COPY [CDDRIVE]:\I386\NTLDR C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM C:\

now i just have to figure out how to get grub to pop up with Windows XP. it said that i had a bad boot.ini so i think i may have to fix that.

If you can't figure out the boot.ini issue it's contents are in the boot info script. If you rerun the script and post the results one of the forumites familiar with Windows can probably help you see what's wrong.

---

### Post by oldfred on 2011-07-10
Boot script normally shows the contents of boot.ini, but there was no boot.ini found by the script.

This windows command should rebuild it.
BOOTCFG  /rebuild  # rebuilds boot.ini

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

meierfra. - How to fix XP when the boot files are missing (has basic boot.ini that you can edit, but you can copy any one and edit to your drive & partition)
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by stonecold913 on 2011-07-10
> **oldfred said:**
> Boot script normally shows the contents of boot.ini, but there was no boot.ini found by the script.

[U]This windows command should rebuild it.
BOOTCFG  /rebuild  # rebuilds boot.ini
[/U]
How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

meierfra. - How to fix XP when the boot files are missing (has basic boot.ini that you can edit, but you can copy any one and edit to your drive & partition)
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

when i enter the underlined command in your post it says that it could not detect any windows installations and to run CHKDSK to find and solve any problems. i ran a full checkdisk today and it still returns the same error. i don't think i have a boot.ini file at all because when i use the Microsoft page you give me it says that it could not find the specified path because it does not exist. i don't entirely know why this is happening.

---

### Post by oldfred on 2011-07-10
Boot.ini is just a text file not like Vista/7 BCD which is a hive that you can only edit with bcdEdit.

You should just be able to copy any boot.ini and edit to be correct drive & partition. Most boot scripts posted here have boot.ini in boot script and most windows are in sda1 or rdisk0 and partition 1..

This is my boot.ini in sda1. Be sure if you use a Linux edit that you save in windows format. 

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```

---

### Post by stonecold913 on 2011-07-10
wer do i save the file too to get it to boot

---

### Post by oldfred on 2011-07-10
In windows it is the root of C:, or top level of sda1. The same place the other boot files are.

---

### Post by stonecold913 on 2011-07-10
It all works now so thank you all for your help. This will be my first place for answers in the future

---

