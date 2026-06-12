---
title: "Can not boot WinXP"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by bj218 on 2010-04-03
Can't Boot WinXP
I have WinXP on 160 GB HD @ /dev/sda1.
I have Ubuntu 9.10 on a 250GB HD @ /dev/sdb1.
I have Mint 7 on the 250 GB HD @ /dev/sdb4.
After I installed Ubuntu 9.10 I can no longer boot to WinXP.
I hope the following maybe be  of some help in solving my problem!! It looks to me like the MBR
has been changed but I don't have enough knowhow to really know what is going on?

Hard drive data

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ============================== 

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=8ad1dfcf-0842-4381-a10c-0fcd58398a56)/boot/grub. 
 => Windows is installed in the MBR of /dev/sdb 

sda1: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Grub 2 
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 271303 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks for 
                       (UUID=da6c0604-0b41-49cd-b226-a309fd7a1d5f)/boot/grub. 
                       No errors found in the Boot Parameter Block. 
    Operating System:  Windows XP 
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 

sda2: _________________________________________________________________________ 

    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:  

sda5: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows XP 
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. 
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows XP 
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63. 
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows XP 
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63. 
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________ 

    File system:       ext4 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  Ubuntu 9.10 
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 

sdb2: _________________________________________________________________________ 

    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:  

sdb5: _________________________________________________________________________ 

    File system:       swap 
    Boot sector type:  - 
    Boot sector info:  

sdb6: _________________________________________________________________________ 

    File system:       ext4 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________ 

    File system:       ext4 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   
 
sdb8: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________ 

    File system:       ext4 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia 
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab 

=========================== Drive/Partition Info: ============================= 

Drive: sda ___________________ _____________________________________________________ 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x761c12f3 

Partition  Boot         Start           End          Size  Id System 

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS 
/dev/sda2         102,398,310   312,576,704   210,178,395   f W95 Ext d (LBA) 
/dev/sda5         102,398,373   225,279,494   122,881,122   7 HPFS/NTFS 
/dev/sda6         225,279,558   266,245,244    40,965,687   7 HPFS/NTFS 
/dev/sda7         266,245,308   312,576,704    46,331,397   7 HPFS/NTFS 


Drive: sdb ___________________ _____________________________________________________ 

Disk /dev/sdb: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x95dc719e 

Partition  Boot         Start           End          Size  Id System 

/dev/sdb1    *             63    48,837,599    48,837,537  83 Linux 
/dev/sdb2          78,140,160   209,262,689   131,122,530   f W95 Ext d (LBA) 
/dev/sdb5          78,140,223    80,196,479     2,056,257  82 Linux swap / Solaris 
/dev/sdb6          80,196,543   131,411,699    51,215,157  83 Linux 
/dev/sdb7         131,411,763   151,894,574    20,482,812  83 Linux 
/dev/sdb8         151,894,638   192,860,324    40,965,687  83 Linux 
/dev/sdb9         192,860,388   209,262,689    16,402,302  83 Linux 
/dev/sdb3         209,262,690   209,278,754        16,065  83 Linux 
/dev/sdb4          48,837,600    78,140,159    29,302,560  83 Linux 


blkid -c /dev/null: ____________________________________________________________ 

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1475ECE9C353C869                       ntfs       Win160                        
/dev/sda5        5E500F31500F1007                       ntfs       Win 160 BU                    
/dev/sda6        48A45674A456650A                       ntfs       Data 160                      
/dev/sda7        9694CA3794CA1A1F                       ntfs       Data 160 BU                   
/dev/sdb1        8ad1dfcf-0842-4381-a10c-0fcd58398a56   ext4       ubuntu                        
/dev/sdb3        084b2522-2715-4e70-b73b-724a116110d5   ext4                                     
/dev/sdb4        fc0bf745-24e4-47bf-b80e-d6187774b849   ext3       mint                          
/dev/sdb5        c07ed73d-c919-4a5d-9c04-b3148b49dda0   swap                                     
/dev/sdb6        14a14e16-2e77-4912-aff9-dc11ecf80f85   ext4       /homeu                        
/dev/sdb7        ab489b4a-5f84-4a9d-9d1d-a062e29ce442   ext4       /miscu                        
/dev/sdb8        4bfdf54d-ffe9-49ce-9d06-5ae1bbc7995f   ext3       /homem                        
/dev/sdb9        555e23cc-0208-4f11-a4cc-cfa8137b9f04   ext3       /miscm                        

============================ "mount | grep ^/dev  output: =========================== 

Device           Mount_Point              Type       Options 
 
/dev/sdb1        /                        ext4       (rw,errors=remount-ro) 
/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) 


================================ sda1/boot.ini: ================================ 

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: =========================== 

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
set root=(hd1,1) 
search --no-floppy --fs-uuid --set 8ad1dfcf-0842-4381-a10c-0fcd58398a56 
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" { 
        recordfail=1 
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi 
	set quiet=1 
	insmod ext2 
	set root=(hd1,1) 
	search --no-floppy --fs-uuid --set 8ad1dfcf-0842-4381-a10c-0fcd58398a56 
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=8ad1dfcf-0842-4381-a10c-0fcd58398a56 ro   quiet splash 
	initrd	/boot/initrd.img-2.6.31-20-generic 
} 
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" { 
        recordfail=1 
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi 
	insmod ext2 
	set root=(hd1,1) 
	search --no-floppy --fs-uuid --set 8ad1dfcf-0842-4381-a10c-0fcd58398a56 
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=8ad1dfcf-0842-4381-a10c-0fcd58398a56 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic 
} 
menuentry "Ubuntu, Linux 2.6.31-14-generic" { 
        recordfail=1 
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi 
	set quiet=1 
	insmod ext2 
	set root=(hd1,1) 
	search --no-floppy --fs-uuid --set 8ad1dfcf-0842-4381-a10c-0fcd58398a56 
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8ad1dfcf-0842-4381-a10c-0fcd58398a56 ro   quiet splash 
	initrd	/boot/initrd.img-2.6.31-14-generic 
} 
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" { 
        recordfail=1 
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi 
	insmod ext2 
	set root=(hd1,1) 
	search --no-floppy --fs-uuid --set 8ad1dfcf-0842-4381-a10c-0fcd58398a56 
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8ad1dfcf-0842-4381-a10c-0fcd58398a56 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic 
} 
### END /etc/grub.d/10_linux ### 

### BEGIN /etc/grub.d/20_memtest86+ ### 
menuentry "Memory test (memtest86+)" { 
	linux16	/boot/memtest86+.bin 
} 
menuentry "Memory test (memtest86+, serial console 115200)" { 
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 
} 
### END /etc/grub.d/20_memtest86+ ### 

### BEGIN /etc/grub.d/30_os-prober ### 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" { 
	insmod ntfs 
	set root=(hd0,1) 
	search --no-floppy --fs-uuid --set 1475ece9c353c869 
	drivemap -s (hd0) ${root} 
	chainloader +1 
} 
menuentry "Linux Mint 6, kernel 2.6.27-7-generic (on /dev/sdb4)" { 
	insmod ext2 
	set root=(hd1,4) 
	search --no-floppy --fs-uuid --set fc0bf745-24e4-47bf-b80e-d6187774b849 
	linux /boot/vmlinuz-2.6.27-7-generic root=/dev/sdb4 ro quiet splash 
	initrd /boot/initrd.img-2.6.27-7-generic 
} 
menuentry "Linux Mint 6, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb4)" { 
	insmod ext2 
	set root=(hd1,4) 
	search --no-floppy --fs-uuid --set fc0bf745-24e4-47bf-b80e-d6187774b849 
	linux /boot/vmlinuz-2.6.27-7-generic root=/dev/sdb4 ro single 
	initrd /boot/initrd.img-2.6.27-7-generic 
} 
menuentry "Linux Mint 6, memtest86+ (on /dev/sdb4)" { 
	insmod ext2 
	set root=(hd1,4) 
	search --no-floppy --fs-uuid --set fc0bf745-24e4-47bf-b80e-d6187774b849 
	linux /boot/memtest86+.bin 
} 
### END /etc/grub.d/30_os-prober ### 

### BEGIN /etc/grub.d/40_custom ### 
# This file provides an easy way to add custom menu entries.  Simply type the 
# menu entries you want to add after this comment.  Be careful not to change 
# the 'exec tail' line above. 
### END /etc/grub.d/40_custom ### 

=============================== sdb1/etc/fstab: =============================== 

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sdb1 during installation 
UUID=8ad1dfcf-0842-4381-a10c-0fcd58398a56 /               ext4    errors=remount-ro 0       1 
# /windows was on /dev/sda1 during installation 
UUID=1475ECE9C353C869 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0 
# swap was on /dev/sdb5 during installation 
UUID=c07ed73d-c919-4a5d-9c04-b3148b49dda0 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 

=================== sdb1: Location of files loaded by Grub: =================== 


    .7GB: boot/grub/core.img 
   3.9GB: boot/grub/grub.cfg 
    .6GB: boot/initrd.img-2.6.31-14-generic 
    .8GB: boot/initrd.img-2.6.31-20-generic 
    .6GB: boot/vmlinuz-2.6.31-14-generic 
    .7GB: boot/vmlinuz-2.6.31-20-generic 
    .8GB: initrd.img 
    .8GB: initrd.img.old 
    .7GB: vmlinuz 
    .7GB: vmlinuz.old 
 
=========================== sdb4/boot/grub/menu.lst: =========================== 

# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-legacy-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default		0 

## Graphical boot menu location 
gfxmenu=/boot/gfxmenu/default.message 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		15 

# Pretty colours 
color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 

# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 

# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 

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
# kopt=root=/dev/sdb4 ro 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd1,3) 

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
# defoptions=quiet splash 

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
# altoptions=(recovery mode) single 

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

title		Linux Mint 6, kernel 2.6.27-7-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Linux Mint 6, kernel Last successful boot 
root		(hd1,3) 
kernel		/boot/last-good-boot/vmlinuz root=/dev/sdb4 ro quiet splash  last-good-boot 
quiet 

title		Linux Mint 6, memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.27-7-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
#title		Ubuntu 8.10, kernel 2.6.24-19-generic (on /dev/sdb1) 
#root		(hd1,0) 
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-19-generic 
#savedefault 
#boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
#title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1) 
#root		(hd1,0) 
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
#initrd		/boot/initrd.img-2.6.24-19-generic 
#savedefault 
#boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb5 
#title		Windows NT/2000/XP 
#root		(hd1,4) 
#savedefault 
#makeactive 
#map		(hd0) (hd1) 
#map		(hd1) (hd0) 
#chainloader	+1 


=============================== sdb4/etc/fstab: =============================== 
 
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sdb4 
UUID=fc0bf745-24e4-47bf-b80e-d6187774b849 /               ext3    relatime,errors=remount-ro 0       1 
# /dev/sdb8 -- Home Directories 
/dev/sdb8	/home		ext3	none		0	2 
# /dev/sdb3 
UUID=e2c057b4-5682-4789-b564-d2369e769c9e none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 

=================== sdb4: Location of files loaded by Grub: =================== 


  38.5GB: boot/grub/menu.lst 
  38.5GB: boot/grub/stage2 
  38.5GB: boot/initrd.img-2.6.27-7-generic 
  38.5GB: boot/vmlinuz-2.6.27-7-generic 
  38.5GB: initrd.img 
  38.5GB: vmlinuz
The above is what I got when  I ran the “boot info script055.sh.
The following is how my disks are partitioned. As of now I can only run Ubuntu & Mint. I am unable 
to boot to WinXP. I sure would like to be able to run WinXP.

 bill@bill-desktop:~$ sudo su 
[sudo] password for bill: 
root@bill-desktop:/home/bill# fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x761c12f3 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS   this is WinXP
/dev/sda2            6375       19457   105089197+   f  W95 Ext'd (LBA) 
/dev/sda5            6375       14023    61440561    7  HPFS/NTFS is Win BU
/dev/sda6           14024       16573    20482843+   7  HPFS/NTFS is my Data
/dev/sda7           16574       19457    23165698+   7  HPFS/NTFS is BU of my Data

Disk /dev/sdb: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x95dc719e 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        3040    24418768+  83  Linux  this is Ubuntu
/dev/sdb2            4865       13026    65561265    f  W95 Ext'd (LBA) 
/dev/sdb3           13027       13027        8032+  83  Linux  un used
/dev/sdb4            3041        4864    14651280   83  Linux this is Mint 
/dev/sdb5            4865        4992     1028128+  82  Linux swap / Solaris 
/dev/sdb6            4993        8180    25607578+  83  Linux this is homeu where I would to put bill
 if knew how
/dev/sdb7            8181        9455    10241406   83  Linux  this is miscu
/dev/sdb8            9456       12005    20482843+  83  Linux  this is homem where I would like to put bill
/dev/sdb9           12006       13026     8201151   83  Linux  this is miscm

---

### Post by audiomick on 2010-04-03
Hallo.
I am afraid I cant tell you definitely how to fix it, but I think this is what is wrong

```
Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of _sda1_[/COLOR] and 
                       [COLOR=Red]looks at[/COLOR] sector 271303 of[COLOR=Red]_the same_ hard drive for 
                       core.img[/COLOR], [COLOR=Blue]core.img is at this location on _/dev/sdb_[/COLOR] and 
                       looks for 
                       [COLOR=SeaGreen](UUID=da6c0604-0b41-49cd-b226-a309fd7a1d5f)[/COLOR]/boot/grub. 
```
```

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1475ECE9C353C869                       ntfs       Win160                        
/dev/sda5        5E500F31500F1007                       ntfs       Win 160 BU                    
/dev/sda6        48A45674A456650A                       ntfs       Data 160                      
/dev/sda7        9694CA3794CA1A1F                       ntfs       Data 160 BU                   
/dev/sdb1        8ad1dfcf-0842-4381-a10c-0fcd58398a56   ext4       ubuntu                        
/dev/sdb3        084b2522-2715-4e70-b73b-724a116110d5   ext4                                     
/dev/sdb4        fc0bf745-24e4-47bf-b80e-d6187774b849   ext3       mint                          
/dev/sdb5        c07ed73d-c919-4a5d-9c04-b3148b49dda0   swap                                     
/dev/sdb6        14a14e16-2e77-4912-aff9-dc11ecf80f85   ext4       /homeu                        
/dev/sdb7        ab489b4a-5f84-4a9d-9d1d-a062e29ce442   ext4       /miscu                        
/dev/sdb8        4bfdf54d-ffe9-49ce-9d06-5ae1bbc7995f   ext3       /homem                        
/dev/sdb9        555e23cc-0208-4f11-a4cc-cfa8137b9f04   ext3       /miscm                        
```

Read the red, then the blue. Grub 2 is looking for core.img on sda, but it is on sdb.
The UUID in green does not appear in the UUID table. It might be a relic of the mint install, perhaps.

All I can suggest is to do
```
sudo update-grub
```
and see if that helps.

---

### Post by bj218 on 2010-04-03
I did the following but that did not help ie grub & grub2!

bill@bill-desktop:~$ sudo update-grub
[sudo] password for bill: 
Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.31-20-generic 
Found initrd image: /boot/initrd.img-2.6.31-20-generic 
Found linux image: /boot/vmlinuz-2.6.31-14-generic 
Found initrd image: /boot/initrd.img-2.6.31-14-generic 
Found memtest86+ image: /boot/memtest86+.bin 
ls: cannot access /media/Data: No such file or directory 
Found Microsoft Windows XP Professional on /dev/sda1 
Found Linux Mint 6 Felicia - Main Edition (6) on /dev/sdb4 
done 
bill@bill-desktop:~$ 

bill@bill-desktop:~$ sudo update-grub2 
[sudo] password for bill: 
Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.31-20-generic 
Found initrd image: /boot/initrd.img-2.6.31-20-generic 
Found linux image: /boot/vmlinuz-2.6.31-14-generic 
Found initrd image: /boot/initrd.img-2.6.31-14-generic 
Found memtest86+ image: /boot/memtest86+.bin 
ls: cannot access /media/Data: No such file or directory 
Found Microsoft Windows XP Professional on /dev/sda1 
Found Linux Mint 6 Felicia - Main Edition (6) on /dev/sdb4 
done 
bill@bill-desktop:~$

---

### Post by oldfred on 2010-04-03
That grub audiomick is pointing to is not the boot grub in the MBR but a grub installed to the partition - PBR.  Sometimes we want grub in a partition for chainbooting but normally not. 

Did you do anything to install grub to sda1 and sda? This has to be the 4th in two days that I have seen this problem. Windows has essential boot files in the windows PBR.

You need to run the fixboot command to write the windows command back to the boot sector on the partition (PBR).

I am just copying the full set of commands but you only need to run fixboot. Do not run fixmbr unless you want to directly boot windows and then reinstall grub.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by bj218 on 2010-04-04
I ran the following commands & I again have access to WinXP THANK YOU.

FIXMBR C:  No problem
FIXBOOT C:  No problem
COPY [CDDRIVE]:\I386\NTLDR C:\   Command not recognized. 
COPY [CDDRIVE]:\I386\NTDETECT.COM C:\  Command not recognized. 
BOOTCFG /rebuild  No problem
The above two  C:\  were not underlined when sent.
After sending these commands I got the following.
Add installation to boot list I sent a Y
Enter Load Identifier  I hit enter key
Enter  OS Load Options  I hit enter key
This got me the following   &#8220;Error: Failed to add the selected boot entry to the list.&#8221;
I do not understand what is going on but things seem to be working!!
When you get your final set of commands would you send  a copy to me @ [email]billjuneau@yahoo.com[/email].

---

### Post by oldfred on 2010-04-04
You did not have to run all the commands unless the fixboot did not work by itself. No harm, but you should only be booting windows. If you want ubuntu back you will have to reinstall grub to sda and run sudo update-grub to get grub to find the windows and add it to its menu.

The 2 commands that did not work were to copy files from the Windows CD if the existing files were not correct. Location may be different??

Follow directions to reinstall grub2 from liveCD. Be sure to install to sda not anything else.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

