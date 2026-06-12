---
title: "Booting from ubuntu installation on external hdd"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Falc7 on 2011-02-21
Hi
I have installed ubuntu to my hard drive on an old laptop, then took the hdd out, put it into a caddy and attached it via usb to my new computer. Now i want to boot into the ubuntu installation in this hdd in the caddy. I did sudo update-grub, and grub finds the installations, and lists them. But when i try and boot from the partitions i get the error: no such partition. What can i do?

---

### Post by deconstrained on 2011-02-21
Have you enabled booting to a removable USB device in BIOS? Is the CPU architecture of the computer you want to run it on compatible with that of the Ubuntu kernel/system you installed on the hard drive? (i.e. is it i386 or x86_64?)

These things aside, here's what would most likely be the issue: 

Making Ubuntu (or Linux, for that matter) bootable from a USB drive may require running special hooks when building the initial ramdisk a.k.a. Linux image. This way, when it starts up, the kernel has all the utilities it needs ready to go, copied into memory, so that it can perform all the necessary mounting and device initialization.

So far here's the best thing I can find on the topic:
[http://manpages.ubuntu.com/manpages/lucid/man7/live-initramfs.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/live-initramfs.7.html)

Related: Ubuntu's startup disk creator does all this stuff to install Ubuntu on a bootable USB drive.

---

### Post by Falc7 on 2011-02-21
> **deconstrained said:**
> Have you enabled booting to a removable USB device in BIOS? Is the CPU architecture of the computer you want to run it on compatible with that of the Ubuntu kernel/system you installed on the hard drive? (i.e. is it i386 or x86_64?)

These things aside, here's what would most likely be the issue: 

Making Ubuntu (or Linux, for that matter) bootable from a USB drive may require running special hooks when building the initial ramdisk a.k.a. Linux image. This way, when it starts up, the kernel has all the utilities it needs ready to go, copied into memory, so that it can perform all the necessary mounting and device initialization.

So far here's the best thing I can find on the topic:
[http://manpages.ubuntu.com/manpages/lucid/man7/live-initramfs.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/live-initramfs.7.html)

Related: Ubuntu's startup disk creator does all this stuff to install Ubuntu on a bootable USB drive.



I selected boot options and then pressed usb storage, the CPU is an i3, so it should be able to run 64 or 32 bit as far as my understanding goes.

About your other suggestion, i resize one of the partitions, then installed ubuntu into the free space on the HDD in the caddy, and selected the boot loader to be installed to the HDD in the caddy as well. Then i selected usb storage from boot options again, but grub didn't load this time.

---

### Post by deconstrained on 2011-02-21
Okay, so it doesn't work via USB in the caddy. Is there absolutely no way you can try just using the drive's native interface?

---

### Post by oldfred on 2011-02-21
This may show if something installed in the wrong place:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Falc7 on 2011-02-22
I guess i could take it apart, i have the screw drivers, but i've never done such a big operation before, i have only done small things like changing the RAM ect. The strange thing is I can ubuntu boot fine from a usb stick

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 HPFS/NTFS
/dev/sda3          30,926,848   235,726,847   204,800,000   7 HPFS/NTFS
/dev/sda4         235,728,894   976,771,071   741,042,178   5 Extended
/dev/sda5         235,728,896   244,576,255     8,847,360  82 Linux swap / Solaris
/dev/sda6         244,578,304   299,610,111    55,031,808  83 Linux
/dev/sda7         299,612,160   666,634,239   367,022,080  83 Linux
/dev/sda8         666,636,288   976,771,071   310,134,784   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               4,094   464,662,527   464,658,434   5 Extended
/dev/sdb5               4,096   199,113,642   199,109,547  83 Linux
/dev/sdb6         199,114,752   464,662,527   265,547,776  83 Linux
/dev/sdb2    *    464,664,060   594,923,519   130,259,460   7 HPFS/NTFS
/dev/sdb3         613,024,335   625,137,344    12,113,010  82 Linux swap / Solaris
/dev/sdb4         594,923,520   613,023,743    18,100,224  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DELLUTILITY                   
/dev/sda2        CC70378A703779F2                       ntfs       Recovery                      
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        560138ed-9b24-4c89-bc3e-c18e0953b256   swap                                     
/dev/sda6        07a29cc2-d8a3-4743-abcb-a356f3ed6909   ext4                                     
/dev/sda7        fbd0baf0-43e0-4ad3-b90f-42da8458ec9f   ext4                                     
/dev/sda8        B6208C24208BEA27                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        0A9C61789C615EE7                       ntfs                                     
/dev/sdb3        1f9bc00e-2002-462e-8375-a43ca9756e90   swap                                     
/dev/sdb4        7e6f724f-9725-4607-a08b-5f4a02fb356b   ext4                                     
/dev/sdb5        d14d9f09-2775-4222-8333-aae1d49bb7e0   ext4                                     
/dev/sdb6        9af3021e-32c8-4bd4-9c10-2a79cd16f383   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set cc70378a703779f2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set ac7c4ec27c4e86d4
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 0a9c61789c615ee7
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos4)'
	search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7e6f724f-9725-4607-a08b-5f4a02fb356b ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb4)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos4)'
	search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7e6f724f-9725-4607-a08b-5f4a02fb356b ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro vga=792 quiet quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro single vga=792 quiet
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro single
	initrd /boot/initrd.img-2.6.32-23-generic
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=fbd0baf0-43e0-4ad3-b90f-42da8458ec9f /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 125.5GB: boot/grub/core.img
 126.0GB: boot/grub/grub.cfg
 130.5GB: boot/initrd.img-2.6.35-25-generic
 125.5GB: boot/vmlinuz-2.6.35-25-generic
 130.5GB: initrd.img
 125.5GB: vmlinuz

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
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
search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro  vga=792 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro single  vga=792 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0a9c61789c615ee7
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6f07980b-100e-4f0c-8034-ced92f90c926
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=6f07980b-100e-4f0c-8034-ced92f90c926 ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6f07980b-100e-4f0c-8034-ced92f90c926
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=6f07980b-100e-4f0c-8034-ced92f90c926 ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6f07980b-100e-4f0c-8034-ced92f90c926
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6f07980b-100e-4f0c-8034-ced92f90c926 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 6f07980b-100e-4f0c-8034-ced92f90c926
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6f07980b-100e-4f0c-8034-ced92f90c926 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=1f9bc00e-2002-462e-8375-a43ca9756e90 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
  78.8GB: boot/grub/grub.cfg
   6.5GB: boot/initrd.img-2.6.32-22-generic
  79.1GB: boot/vmlinuz-2.6.32-22-generic
   6.5GB: initrd.img
  79.1GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0a9c61789c615ee7
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro vga=792 quiet quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro single vga=792 quiet
	initrd /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=1f9bc00e-2002-462e-8375-a43ca9756e90 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 183.6GB: boot/grub/core.img
 226.9GB: boot/grub/grub.cfg
 183.8GB: boot/initrd.img-2.6.32-23-generic
 191.3GB: boot/initrd.img-2.6.32-24-generic
 183.7GB: boot/vmlinuz-2.6.32-23-generic
 183.8GB: boot/vmlinuz-2.6.32-24-generic
 191.3GB: initrd.img
 183.8GB: initrd.img.old
 183.8GB: vmlinuz
 183.7GB: vmlinuz.old

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
set root='(hd2,msdos4)'
search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos4)'
search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
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
	set root='(hd2,msdos4)'
	search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e6f724f-9725-4607-a08b-5f4a02fb356b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos4)'
	search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e6f724f-9725-4607-a08b-5f4a02fb356b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos4)'
	search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos4)'
	search --no-floppy --fs-uuid --set 7e6f724f-9725-4607-a08b-5f4a02fb356b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set cc70378a703779f2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set ac7c4ec27c4e86d4
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 07a29cc2-d8a3-4743-abcb-a356f3ed6909
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=07a29cc2-d8a3-4743-abcb-a356f3ed6909 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Windows 7 (loader) (on /dev/sdc2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd2,msdos2)'
	search --no-floppy --fs-uuid --set 0a9c61789c615ee7
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sdc5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro vga=792 quiet quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sdc5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set d14d9f09-2775-4222-8333-aae1d49bb7e0
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=d14d9f09-2775-4222-8333-aae1d49bb7e0 ro single vga=792 quiet
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sdc6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos6)'
	search --no-floppy --fs-uuid --set 9af3021e-32c8-4bd4-9c10-2a79cd16f383
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9af3021e-32c8-4bd4-9c10-2a79cd16f383 ro single
	initrd /boot/initrd.img-2.6.32-23-generic
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
# / was on /dev/sdc4 during installation
UUID=7e6f724f-9725-4607-a08b-5f4a02fb356b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=560138ed-9b24-4c89-bc3e-c18e0953b256 none            swap    sw              0       0
# swap was on /dev/sdc3 during installation
UUID=1f9bc00e-2002-462e-8375-a43ca9756e90 none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


 311.4GB: boot/grub/core.img
 311.4GB: boot/grub/grub.cfg
 307.2GB: boot/initrd.img-2.6.35-22-generic
 311.4GB: boot/vmlinuz-2.6.35-22-generic
 307.2GB: initrd.img
 311.4GB: vmlinuz

```

---

### Post by oldfred on 2011-02-22
All the installs in sdb4,5 & 6 do show in your grub.cfg when booting your internal. Were they all working installs?

Does the USB drive mount as sdb or hd1? Generally everything looks ok to me, but maybe someone else will see something?

I found with my USB flash drives the hdx setting often was wrong and the serach by UUID did not always work. I had to manually edit the drive number to the correct number to get it to boot and remove the search by UUID line. You can edit with e on grub menu and adjust drive number, control x to boot.

When you boot internal drive it will be hd0, is caddy then hd1? If not change to correct drive number:

set root='(hd[COLOR=Red]1[/COLOR],msdos4)'

---

### Post by Falc7 on 2011-02-22
sdb 4,5 and 6 were all working installs. Infact, the install on sdb4 is brand new, i booted into a liveusb stick, resized windows there, and installed a new copy of ubuntu to sdb4. And told the installer to write to the MBR to the HDD in the caddy.

I am pretty sure the USB drive mounts to sdb. I am considering trying reinstalling ubuntu to sdb4 again and tell the installer to write the MBR to the internal HDD, rekon its worth a shot?

---

### Post by oldfred on 2011-02-22
As long as you are willing to reinstall grub for the internal drive. 

If system boots USB I do not see why it will not boot external. Have you checked under hard drives not USB devices?

---

### Post by Falc7 on 2011-02-22
If i select hard drives then it takes me to the internal hard drive. 

I am looking at the places I can install grub to, here is a screenshot, do you think there are any of them in particular i should try?
[http://i.imgur.com/HIAz9.png](http://i.imgur.com/HIAz9.png)

---

### Post by oldfred on 2011-02-23
I do not know why they do present all the options at the same level.  Almost all users should be installing to the sda, sdb or the master boot record (MBR) of the drive. Not to partitions sda1, sda2, sdb1 etc. Computers only boot thru the MBR first. 

Only advanced users who understand that certain system changes will require a reinstall, should have that option.  Since grub2 is it not reliable  in a partition boot sector(PBR). And if you install to the windows PBR you overwrite essential windows boot code. If you install to a partition you have to have another boot loader in the MBR that allows you to then chainload to the grub the PBR. (this is how grub chainloads windows).

---

