---
title: "help with muliboot please."
date: 2011-04-27
forum: New to Ubuntu
---

### Post by georgelappies on 2011-04-27
I have ubuntu installed on my laptop. On a seperate partition I installed openSuSE. The problem now is that my ubuntu is no longer listed when the pc starts up. How can I fix this so that I am able to start ubuntu or openSuSE?

I have ubuntu bootable pendrive to use should I need it.

---

### Post by oldfred on 2011-04-27
Reinstall Ubuntu's grub2 boot loader. It will see openSuSE after an update to grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

After booting into Ubuntu

sudo update-grub

---

### Post by georgelappies on 2011-04-27
> **oldfred said:**
> Reinstall Ubuntu's grub2 boot loader. It will see openSuSE after an update to grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

After booting into Ubuntu

sudo update-grub

Thank you so much, all is well now again
 ;)

---

### Post by georgelappies on 2011-04-27
Great I could boot into ubuntu now and work in it. But when I try to boot into suse it gives an error saying it cannot find the device and that I need to load the kernel first...

Although it list the default and failsafe values for the suse kernel...

Any help will be much appreciated please.

---

### Post by oldfred on 2011-04-27
Post this to see if we can see what is missing:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by georgelappies on 2011-04-28
> **oldfred said:**
> Post this to see if we can see what is missing:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Thank you, will do so as soon as I get back from work and post it here.

---

### Post by georgelappies on 2011-04-29
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for +etb.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 813712328 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.4 
                       "Celadon" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              80,325    36,944,324    36,864,000   7 HPFS/NTFS
/dev/sda3          36,944,325   761,754,104   724,809,780   7 HPFS/NTFS
/dev/sda4    *    761,754,166   976,771,071   215,016,906   f W95 Ext d (LBA)
/dev/sda5         761,754,168   792,454,319    30,700,152  83 Linux
/dev/sda6         792,455,168   843,653,119    51,197,952  83 Linux
/dev/sda7         843,655,168   960,841,727   117,186,560  83 Linux
/dev/sda8         960,843,776   976,771,071    15,927,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8166 MB, 8166309888 bytes
212 heads, 51 sectors/track, 1475 cylinders, total 15949824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,195    15,949,823    15,941,629   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        B278DFC178DF8311                       ntfs       RECOVERY                      
/dev/sda3        BA94E1E794E1A65B                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        28e67d7d-bdca-4ea6-af59-fb3ce365fe92   ext4                                     
/dev/sda6        0924175b-4c40-4629-b542-47c43775f189   ext4                                     
/dev/sda7        2b8bbec5-568d-415c-9c0a-54f478a7a1f4   ext4                                     
/dev/sda8        fac6ea1a-9f40-4966-98b8-d96e75b3973e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        012B-D8AB                              vfat       BLACKBERRY                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sdb1        /media/BLACKBERRY        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28e67d7d-bdca-4ea6-af59-fb3ce365fe92
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28e67d7d-bdca-4ea6-af59-fb3ce365fe92
set locale_dir=($root)/boot/grub/locale
set lang=en_ZA
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28e67d7d-bdca-4ea6-af59-fb3ce365fe92
linux/boot/vmlinuz-2.6.38-8-generic root=UUID=28e67d7d-bdca-4ea6-af59-fb3ce365fe92 ro   quiet splash vt.handoff=7
initrd/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28e67d7d-bdca-4ea6-af59-fb3ce365fe92
echo'Loading Linux 2.6.38-8-generic ...'
linux/boot/vmlinuz-2.6.38-8-generic root=UUID=28e67d7d-bdca-4ea6-af59-fb3ce365fe92 ro single 
echo'Loading initial ramdisk ...'
initrd/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28e67d7d-bdca-4ea6-af59-fb3ce365fe92
linux16/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 28e67d7d-bdca-4ea6-af59-fb3ce365fe92
linux16/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root B278DFC178DF8311
chainloader +1
}
menuentry "Desktop -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 116f8dfd-eacd-48d5-b97b-07cfefe9433e
linux /boot/vmlinuz-2.6.37.1-1.2-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part7 resume=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 splash=silent quiet showopts vga=0x317
initrd /boot/initrd-2.6.37.1-1.2-desktop
}
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 116f8dfd-eacd-48d5-b97b-07cfefe9433e
linux /boot/vmlinuz-2.6.37.1-1.2-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part7 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
initrd /boot/initrd-2.6.37.1-1.2-desktop
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
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=2b8bbec5-568d-415c-9c0a-54f478a7a1f4 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=fac6ea1a-9f40-4966-98b8-d96e75b3973e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 396.8GB: boot/grub/core.img
 401.0GB: boot/grub/grub.cfg
 391.2GB: boot/initrd.img-2.6.38-8-generic
 396.9GB: boot/vmlinuz-2.6.38-8-generic
 391.2GB: initrd.img
 396.9GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Wed Apr 27 18:35:01 SAST 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.4 - 2.6.39-rc4-11
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.39-rc4-11-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 resume=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part8 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.39-rc4-11-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.39-rc4-11
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.39-rc4-11-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.39-rc4-11-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,2)
    chainloader +1

=============================== sda6/etc/fstab: ===============================

/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part7 /home                ext4       defaults              1 2
/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part3 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part5 /xubuntu             ext4       defaults              1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda6: Location of files loaded by Grub: ===================


 416.6GB: boot/grub/menu.lst
 416.6GB: boot/grub/stage2
 406.3GB: boot/initrd
 406.3GB: boot/initrd-2.6.39-rc4-11-desktop
 416.6GB: boot/vmlinuz
 416.6GB: boot/vmlinuz-2.6.39-rc4-11-desktop 
```> **oldfred said:**
> Post this to see if we can see what is missing:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Here is the printout of the requested info

---

### Post by oldfred on 2011-04-29
I am not familiar with openSUSE but as near as I can tell, you have moved partitions around.

openSUSE has recovery from part8 which is now swap sda8.

The UUID listed in Ubuntu's openSUSE entry does not exist. Your openSUSE is in sda6 so part6 looks correct put part7 does not.

/dev/sda6        0924175b-4c40-4629-b542-47c43775f189   ext4 

set root='(/dev/sda,[COLOR=Red]msdos6[/COLOR])'
search --no-floppy --fs-uuid --set=root [COLOR=Red]116f8dfd-eacd-48d5-b97b-07cfefe9433e[/COLOR]
linux /boot/vmlinuz-2.6.37.1-1.2-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-[COLOR=Red]part7[/COLOR] resume=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-[COLOR=Red]part6[/COLOR] splash=silent quiet showopts vga=0x317
initrd /boot/initrd-2.6.37.1-1.2-desktop

Copy this into 40_custom.
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

```
menuentry "Edited Desktop -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0924175b-4c40-4629-b542-47c43775f189
linux /boot/vmlinuz-2.6.37.1-1.2-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 resume=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 splash=silent quiet showopts vga=0x317
initrd /boot/initrd-2.6.37.1-1.2-desktop
}


```

---

### Post by georgelappies on 2011-04-29
> **oldfred said:**
> I am not familiar with openSUSE but as near as I can tell, you have moved partitions around.

openSUSE has recovery from part8 which is now swap sda8.

The UUID listed in Ubuntu's openSUSE entry does not exist. Your openSUSE is in sda6 so part6 looks correct put part7 does not.

/dev/sda6        0924175b-4c40-4629-b542-47c43775f189   ext4 

set root='(/dev/sda,[COLOR=Red]msdos6[/COLOR])'
search --no-floppy --fs-uuid --set=root [COLOR=Red]116f8dfd-eacd-48d5-b97b-07cfefe9433e[/COLOR]
linux /boot/vmlinuz-2.6.37.1-1.2-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-[COLOR=Red]part7[/COLOR] resume=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-[COLOR=Red]part6[/COLOR] splash=silent quiet showopts vga=0x317
initrd /boot/initrd-2.6.37.1-1.2-desktop

Copy this into 40_custom.
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

```
menuentry "Edited Desktop -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda6)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0924175b-4c40-4629-b542-47c43775f189
linux /boot/vmlinuz-2.6.37.1-1.2-desktop root=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 resume=/dev/disk/by-id/ata-ST9500420AS_5VJ7ST1G-part6 splash=silent quiet showopts vga=0x317
initrd /boot/initrd-2.6.37.1-1.2-desktop
}


```

Hi, When I do that it gives me the message below. I updated my suse kernel to 2.6.39 rc4 before ubuntu was installed so I changed those settings to reflect that (I ran it as per your exact file as well with 2.6.37 and it gave the same errors)

```
[xub-box 2] Desktop > sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found openSUSE 11.4 (x86_64) on /dev/sda6
/etc/grub.d/40_custom: 1: menuentry: not found
insmod: can't read 'part_msdos': No such file or directory
insmod: can't read 'ext2': No such file or directory
/etc/grub.d/40_custom: 5: search: not found
/etc/grub.d/40_custom: 6: linux: not found
/etc/grub.d/40_custom: 7: initrd: not found
/etc/grub.d/40_custom: 8: Syntax error: "}" unexpected
[08:50 1.10]
[xub-box 3] Desktop >
```

---

### Post by oldfred on 2011-04-29
It seems like it is not reading 40_custom correctly. Post your 40_custom. You did leave the first lines untouched?

---

### Post by georgelappies on 2011-04-29
> **oldfred said:**
> It seems like it is not reading 40_custom correctly. Post your 40_custom. You did leave the first lines untouched?

Oops... No I replaced the contents of the file with the code you gave me, lol. Will the file on the live CD suffice as a replacement to get the top lines?

---

### Post by oldfred on 2011-04-29
This is mine:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

---

### Post by georgelappies on 2011-04-29
> **oldfred said:**
> This is mine:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

Thank you so much, all is well. This is posted from within my suse install :)

---

### Post by oldfred on 2011-04-29
Glad it worked. 

You may have a couple of housekeeping issues. You can update the openSUSE grub menu, old grub also used update-grub from root. I have only used Ubuntu with sudo, so I do not know what you do in openSUSE.

Then grub2's osprobers may see the correct info and update itself to work. If not and you have to continue to use the manual entry you can turn off the os-prober in grub2 to eliminate the auto entries. You will have to manually update then with any kernel changes in openSUSE.

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

You can turn it back on if you want to have it search for other changes in the future.

---

