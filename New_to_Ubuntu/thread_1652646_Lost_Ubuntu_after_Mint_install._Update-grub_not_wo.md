---
title: "Lost Ubuntu after Mint install. Update-grub not working."
date: 2010-12-25
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-12-25
Hello:

I resized my original Ubuntu partition to allow space for a Mint install. I installed Mint.

PC boots only into Mint.

I booted with my Ubuntu Netbook Live CD and tried to update the grub menu:

roblinux@roblinux:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I don't know what to do.

Thanks for any assistance with this.

---

### Post by karthick87 on 2010-12-25
You have to reinstall grub i guess..

---

### Post by karthick87 on 2010-12-25
Boot from a live cd,mount your root partition
```
sudo mount /dev/sdaX /mnt
```
where X is your root partition
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Now unmount
```
sudo umount /mnt
```
Reboot your computer and run
```
sudo update-grub
```

---

### Post by Robert.Thompson on 2010-12-25
> **karthick87 said:**
> You have to reinstall grub i guess..

I used the script and got:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  MEPIS Linux 8.5
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             976,896    40,038,399    39,061,504  83 Linux
/dev/sda3          40,038,400    52,733,951    12,695,552  82 Linux swap / Solaris
/dev/sda4          52,735,998   312,580,095   259,844,098   5 Extended
/dev/sda5          52,741,458   182,675,114   129,933,657  83 Linux
/dev/sda6         182,675,178   223,978,229    41,303,052  83 Linux
/dev/sda7         223,978,293   312,576,704    88,598,412  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c9431973-1ce3-4ea2-b534-bd1a91ed9821   ext4                                     
/dev/sda2        7c52db16-b609-49ad-986d-bdb2e4a1db05   ext4                                     
/dev/sda3        688a545d-5f47-4a7b-8e6b-9727b64222b8   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d3b32c53-c123-4f71-bf47-85a12f9eb739   ext4                                     
/dev/sda6        79e326e3-89a3-4b46-9661-35a424b11a85   ext4                                     
/dev/sda7        fce61376-732e-4fd3-af97-04a911ffdfbd   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/7c52db16-b609-49ad-986d-bdb2e4a1db05 ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7c52db16-b609-49ad-986d-bdb2e4a1db05
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	linux	/vmlinuz-2.6.35-24-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	linux	/vmlinuz-2.6.35-23-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/vmlinuz-2.6.35-23-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	linux	/vmlinuz-2.6.35-22-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-2.6.35-23-generic
    .1GB: initrd.img-2.6.35-24-generic
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-23-generic
    .0GB: vmlinuz-2.6.35-24-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c9431973-1ce3-4ea2-b534-bd1a91ed9821 /boot           ext4    defaults        0       2
/dev/sda5       /home           ext4    defaults        0       2
/dev/sda3       none            swap    sw              0       0

=========================== sda6/boot/grub/menu.lst: ===========================

timeout 10
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sda6, newest kernel
root (hd0,5)
kernel /boot/vmlinuz root=/dev/sda6 nomce quiet splash vga=789 
initrd /boot/initrd.img
boot

title MEPIS at sda6, kernel 2.6.32-1-mepis-smp
root (hd0,5)
kernel /boot/vmlinuz-2.6.32-1-mepis-smp root=/dev/sda6 nomce quiet splash vga=789 
initrd /boot/initrd.img-2.6.32-1-mepis-smp
boot


title MEMTEST
kernel /boot/memtest86+.bin

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.32-1-mepis-smp Default
root		(hd0,5)
kernel		/boot/vmlinuz root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro 
initrd		/boot/initrd.img

title		Debian GNU/Linux, kernel 2.6.32-1-mepis-smp Default (single-user mode)
root		(hd0,5)
kernel		/boot/vmlinuz root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro single
initrd		/boot/initrd.img

title		Debian GNU/Linux, kernel 2.6.32-1-mepis-smp
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-1-mepis-smp root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro 
initrd		/boot/initrd.img-2.6.32-1-mepis-smp

title		Debian GNU/Linux, kernel 2.6.32-1-mepis-smp (single-user mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-1-mepis-smp root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro single
initrd		/boot/initrd.img-2.6.32-1-mepis-smp

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# Pluggable devices are handled by uDev, they are not in fstab
/dev/sda6 / ext4 defaults,noatime 1 1
/dev/sda3 swap swap sw,pri=1 0 0
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sda1 /mnt/sda1 ext4 noauto,users,exec,relatime 0 0
/dev/sda2 /mnt/sda2 ext4 noauto,users,exec,relatime 0 0
/dev/sda5 /mnt/sda5 ext4 noauto,users,exec,relatime 0 0
/dev/sda7 /mnt/sda7 ext4 noauto,users,exec,relatime 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/hda /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0

=================== sda6: Location of files loaded by Grub: ===================


 110.8GB: boot/grub/menu.lst
 110.8GB: boot/grub/stage2
 111.6GB: boot/initrd.img
 111.6GB: boot/initrd.img-2.6.32-1-mepis-smp
 111.6GB: boot/vmlinuz
 111.6GB: boot/vmlinuz-2.6.32-1-mepis-smp


```
I don't know if there are any "obvious discrepancies" or problems, do you?

Thanks,

---

### Post by gtpitch on 2010-12-25
You shouldn't need to use the live CD. Just boot into mint and update grub in the terminal. Should find the Ubuntu image and solve the problem.

---

### Post by sandyd on 2010-12-25
> **Robert.Thompson said:**
> I used the script and got:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
 **   Operating System:  MEPIS Linux 8.5**
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             976,896    40,038,399    39,061,504  83 Linux
/dev/sda3          40,038,400    52,733,951    12,695,552  82 Linux swap / Solaris
/dev/sda4          52,735,998   312,580,095   259,844,098   5 Extended
/dev/sda5          52,741,458   182,675,114   129,933,657  83 Linux
/dev/sda6         182,675,178   223,978,229    41,303,052  83 Linux
/dev/sda7         223,978,293   312,576,704    88,598,412  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c9431973-1ce3-4ea2-b534-bd1a91ed9821   ext4                                     
/dev/sda2        7c52db16-b609-49ad-986d-bdb2e4a1db05   ext4                                     
/dev/sda3        688a545d-5f47-4a7b-8e6b-9727b64222b8   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d3b32c53-c123-4f71-bf47-85a12f9eb739   ext4                                     
/dev/sda6        79e326e3-89a3-4b46-9661-35a424b11a85   ext4                                     
/dev/sda7        fce61376-732e-4fd3-af97-04a911ffdfbd   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/7c52db16-b609-49ad-986d-bdb2e4a1db05 ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7c52db16-b609-49ad-986d-bdb2e4a1db05
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    linux    /vmlinuz-2.6.35-24-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro  quiet vga=795  quiet splash
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /vmlinuz-2.6.35-24-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro single  quiet vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    linux    /vmlinuz-2.6.35-23-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro  quiet vga=795  quiet splash
    initrd    /initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /vmlinuz-2.6.35-23-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro single  quiet vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    linux    /vmlinuz-2.6.35-22-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro  quiet vga=795  quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 ro single  quiet vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c9431973-1ce3-4ea2-b534-bd1a91ed9821
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-2.6.35-23-generic
    .1GB: initrd.img-2.6.35-24-generic
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-23-generic
    .0GB: vmlinuz-2.6.35-24-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=7c52db16-b609-49ad-986d-bdb2e4a1db05 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c9431973-1ce3-4ea2-b534-bd1a91ed9821 /boot           ext4    defaults        0       2
/dev/sda5       /home           ext4    defaults        0       2
/dev/sda3       none            swap    sw              0       0

=========================== sda6/boot/grub/menu.lst: ===========================

timeout 10
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sda6, newest kernel
root (hd0,5)
kernel /boot/vmlinuz root=/dev/sda6 nomce quiet splash vga=789 
initrd /boot/initrd.img
boot

title MEPIS at sda6, kernel 2.6.32-1-mepis-smp
root (hd0,5)
kernel /boot/vmlinuz-2.6.32-1-mepis-smp root=/dev/sda6 nomce quiet splash vga=789 
initrd /boot/initrd.img-2.6.32-1-mepis-smp
boot


title MEMTEST
kernel /boot/memtest86+.bin

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.32-1-mepis-smp Default
root        (hd0,5)
kernel        /boot/vmlinuz root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro 
initrd        /boot/initrd.img

title        Debian GNU/Linux, kernel 2.6.32-1-mepis-smp Default (single-user mode)
root        (hd0,5)
kernel        /boot/vmlinuz root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro single
initrd        /boot/initrd.img

title        Debian GNU/Linux, kernel 2.6.32-1-mepis-smp
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.32-1-mepis-smp root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro 
initrd        /boot/initrd.img-2.6.32-1-mepis-smp

title        Debian GNU/Linux, kernel 2.6.32-1-mepis-smp (single-user mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.32-1-mepis-smp root=UUID=79e326e3-89a3-4b46-9661-35a424b11a85 ro single
initrd        /boot/initrd.img-2.6.32-1-mepis-smp

title        Debian GNU/Linux, kernel memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# Pluggable devices are handled by uDev, they are not in fstab
/dev/sda6 / ext4 defaults,noatime 1 1
/dev/sda3 swap swap sw,pri=1 0 0
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/sda1 /mnt/sda1 ext4 noauto,users,exec,relatime 0 0
/dev/sda2 /mnt/sda2 ext4 noauto,users,exec,relatime 0 0
/dev/sda5 /mnt/sda5 ext4 noauto,users,exec,relatime 0 0
/dev/sda7 /mnt/sda7 ext4 noauto,users,exec,relatime 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/hda /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0

=================== sda6: Location of files loaded by Grub: ===================


 110.8GB: boot/grub/menu.lst
 110.8GB: boot/grub/stage2
 111.6GB: boot/initrd.img
 111.6GB: boot/initrd.img-2.6.32-1-mepis-smp
 111.6GB: boot/vmlinuz
 111.6GB: boot/vmlinuz-2.6.32-1-mepis-smp


```I don't know if there are any "obvious discrepancies" or problems, do you?

Thanks,
BIS says that Grub looks for stuff on /dev/sda6.
However, /dev/sda6 is not linux mint, but mepis?

---

