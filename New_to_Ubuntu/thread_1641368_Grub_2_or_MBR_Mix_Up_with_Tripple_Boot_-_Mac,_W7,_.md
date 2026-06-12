---
title: "Grub 2 or MBR Mix Up with Tripple Boot - Mac, W7, Ubuntu 10.10"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by dreiercarr on 2010-12-08
I was running Mac OS 10.6 along with Windows 7 and Karmic Koala on a MacBookPro3,1 using rEFIt and everything was running smoothly.  I tried to install gnuradio and something went wrong with a dependency and after getting frustrated I decided to install Lucid Lynx fresh over my Linux partition and try again.

I remember that the MBR and Grub were really picky when I first got this setup running, but I can't remember any solution details.  I first tried installing 10.10 over Karmic and installed the bootloader on the Windows partition (because in my old setup rEFIt would give the option to launch Mac or Windows, and Windows would point to grub where you could select linux or w7 - this was the picky part).  Now going into the Windows option from rEFIt launches grub rescue which spits back the error "unknown filesystem".

Do I need to reinstall my W7 and/or Ubuntu partition?  Is there a way to fix/repair/boot my grub/mbr?

Here is what the bootinfo script returns:
```
Boot Info Script 0.55    dated February 15th, 2010                     
 ============================= Boot Info Summary: ==============================   
=> Grub 2 is installed in the MBR of /dev/sda and looks at sector 861787240      of the same hard drive for core.img, core.img is at this location on      /dev/sda and looks on partition #3 for /boot/grub.  
sda1: _________________________________________________________________________      
File system:       vfat     
Boot sector type:  BSD4.4: Fat32     
Boot sector info:  According to the info in the boot sector, sda1 starts at sector 0. But according to the info from fdisk,        sda1 starts at sector 40.     
Operating System:       
Boot files/dirs:     
sda2: _________________________________________________________________________      
File system:       hfsplus     
Boot sector type:  -     
Boot sector info:       
Operating System:       
Boot files/dirs:     
sda3: _________________________________________________________________________      
File system:       swap     
Boot sector type:  -     
Boot sector info:    
sda4: _________________________________________________________________________      
File system:       ntfs     
Boot sector type:  Grub 2     
Boot sector info:  Grub 2 is installed in the boot sector of sda4 and looks at sector 880974992 of the same hard drive for core.img, but core.img can not be found at this location. No errors found in the Boot Parameter Block.     
Operating System:  Windows 7     
Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  
sda5: _________________________________________________________________________      
File system:       ext3     
Boot sector type:  -     
Boot sector info:       
Operating System:  Ubuntu 10.10     
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  

=========================== Drive/Partition Info: =============================  
Drive: sda ___________________ _____________________________________________________  
Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  
Partition  Boot         Start           End          Size  Id System  /dev/sda1                   1       409,639       409,639  ee GPT /dev/sda2             409,640   839,209,991   838,800,352  af HFS /dev/sda3         839,211,008   841,209,855     1,998,848  82 Linux swap / Solaris /dev/sda4    *    897,808,590   976,511,024    78,702,435   7 HPFS/NTFS   GUID Partition Table detected.  
Partition           Start           End          Size System /dev/sda1              40       409,639       409,600 System/Boot Partition /dev/sda2         409,640   839,209,991   838,800,352 HFS+ /dev/sda3     839,211,008   841,209,855     1,998,848 Linux Swap /dev/sda4     897,808,590   976,511,024    78,702,435 Linux or Data /dev/sda5     841,209,856   897,808,383    56,598,528 Linux or Data  blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/sda1        3F3C-1AF6                              vfat       EFI                            /dev/sda2        3434826d-ec45-3d37-a8e9-5454a870062b   hfsplus    Macintosh HD                   /dev/sda3        e6a3156f-be40-4269-ac9d-b1a2a5bc82f7   swap                                      /dev/sda4        9AC4A4A5C4A484DB                       ntfs       BOOTCAMP                       /dev/sda5        c5181bf0-b3d2-4482-9541-aa840aa7fb2c   ext3                                      /dev/sda: PTTYPE="gpt"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sr0         /cdrom                   iso9660    (ro,noatime) /dev/loop0       /rofs                    squashfs   (ro,noatime)   =========================== sda5/boot/grub/grub.cfg: ===========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_gpt insmod ext2 set root='(hd0,gpt5)' search --no-floppy --fs-uuid --set c5181bf0-b3d2-4482-9541-aa840aa7fb2c if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_gpt insmod ext2 set root='(hd0,gpt5)' search --no-floppy --fs-uuid --set c5181bf0-b3d2-4482-9541-aa840aa7fb2c set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod part_gpt     insmod ext2     set root='(hd0,gpt5)'     search --no-floppy --fs-uuid --set c5181bf0-b3d2-4482-9541-aa840aa7fb2c     linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c5181bf0-b3d2-4482-9541-aa840aa7fb2c ro   quiet splash     initrd    /boot/initrd.img-2.6.35-23-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod part_gpt     insmod ext2     set root='(hd0,gpt5)'     search --no-floppy --fs-uuid --set c5181bf0-b3d2-4482-9541-aa840aa7fb2c     echo    'Loading Linux 2.6.35-23-generic-pae ...'     linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c5181bf0-b3d2-4482-9541-aa840aa7fb2c ro single      echo    'Loading initial ramdisk ...'     initrd    /boot/initrd.img-2.6.35-23-generic-pae } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" {     insmod part_gpt     insmod ext2     set root='(hd0,gpt5)'     search --no-floppy --fs-uuid --set c5181bf0-b3d2-4482-9541-aa840aa7fb2c     linux16    /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" {     insmod part_gpt     insmod ext2     set root='(hd0,gpt5)'     search --no-floppy --fs-uuid --set c5181bf0-b3d2-4482-9541-aa840aa7fb2c     linux16    /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Mac OS X (32-bit) (on /dev/sda2)" {     insmod part_gpt     insmod hfsplus     set root='(hd0,gpt2)'     search --no-floppy --fs-uuid --set 0e08c3b7ac6a6a7d         load_video         set do_resume=0         if [ /var/vm/sleepimage -nt10 / ]; then            if xnu_resume /var/vm/sleepimage; then              set do_resume=1            fi         fi         if [ $do_resume = 0 ]; then            xnu_uuid 0e08c3b7ac6a6a7d uuid            if [ -f /Extra/DSDT.aml ]; then               acpi -e /Extra/DSDT.aml            fi            xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid            if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then               xnu_mkext /System/Library/Extensions.mkext            else               xnu_kextdir /System/Library/Extensions            fi            if [ -f /Extra/Extensions.mkext ]; then               xnu_mkext /Extra/Extensions.mkext            fi            if [ -d /Extra/Extensions ]; then               xnu_kextdir /Extra/Extensions            fi            if [ -f /Extra/devprop.bin ]; then               xnu_devprop_load /Extra/devprop.bin            fi            if [ -f /Extra/splash.jpg ]; then               insmod jpeg               xnu_splash /Extra/splash.jpg            fi            if [ -f /Extra/splash.png ]; then               insmod png               xnu_splash /Extra/splash.png            fi            if [ -f /Extra/splash.tga ]; then               insmod tga               xnu_splash /Extra/splash.tga            fi         fi } menuentry "Mac OS X (64-bit) (on /dev/sda2)" {     insmod part_gpt     insmod hfsplus     set root='(hd0,gpt2)'     search --no-floppy --fs-uuid --set 0e08c3b7ac6a6a7d         load_video         set do_resume=0         if [ /var/vm/sleepimage -nt10 / ]; then            if xnu_resume /var/vm/sleepimage; then              set do_resume=1            fi         fi         if [ $do_resume = 0 ]; then            xnu_uuid 0e08c3b7ac6a6a7d uuid            if [ -f /Extra/DSDT.aml ]; then               acpi -e /Extra/DSDT.aml            fi            xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid            if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then               xnu_mkext /System/Library/Extensions.mkext            else               xnu_kextdir /System/Library/Extensions            fi            if [ -f /Extra/Extensions.mkext ]; then               xnu_mkext /Extra/Extensions.mkext            fi            if [ -d /Extra/Extensions ]; then               xnu_kextdir /Extra/Extensions            fi            if [ -f /Extra/devprop.bin ]; then               xnu_devprop_load /Extra/devprop.bin            fi            if [ -f /Extra/splash.jpg ]; then               insmod jpeg               xnu_splash /Extra/splash.jpg            fi            if [ -f /Extra/splash.png ]; then               insmod png               xnu_splash /Extra/splash.png            fi            if [ -f /Extra/splash.tga ]; then               insmod tga               xnu_splash /Extra/splash.tga            fi         fi } menuentry "Windows 7 (loader) (on /dev/sda4)" {     insmod part_gpt     insmod ntfs     set root='(hd0,gpt4)'     search --no-floppy --fs-uuid --set 9ac4a4a5c4a484db     chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  =============================== sda5/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 /dev/sda5       /               ext3    errors=remount-ro 0       1 /dev/sda3       none            swap    sw              0       0  =================== sda5: Location of files loaded by Grub: ===================    451.0GB: boot/grub/core.img  451.0GB: boot/grub/grub.cfg  451.0GB: boot/initrd.img-2.6.35-23-generic-pae  451.0GB: boot/vmlinuz-2.6.35-23-generic-pae  451.0GB: initrd.img  451.0GB: vmlinuz  
```Thanks a ton for any help, I have been swimming in similar topics on the forums but have been getting pretty lost and overwhelmed with all the different scenarios people have run into.

---

### Post by oldfred on 2010-12-09
I do not know about REfit and Mac's but this is a problem as windows has to have its code in the partition boot sector.

```
File system:       ntfs     
Boot sector type:  Grub 2     
Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda4[/COLOR] and looks at sector 880974992 of the same hard drive for core.img, but core.img can not be found at this location. No errors found in the Boot Parameter Block.     
Operating System:  Windows 7     
Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  
s

```

For standard MBR (msdos) partitions testdisk or using a windows repair CD and running BootRec.exe /FixBoot will replace the windows code in the partition boot sector.

You may have a gpt partitioning so this may not work.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by dreiercarr on 2010-12-09
Thanks oldgreg, I'll run testdisk to fix grub on the windows partition and report the results tonight.

I am still a little unclear about what the proper configuration should be though.  Should grub be on the windows partition (where it is now) or the linux partition or both?  Is my main/only problem that grub is installed in the correct place but is broken (because I installed Ubuntu last)?

I'd love to learn about what is supposed to happen and what the correct config should be, but with all the different scenarios out there, I have gotten really confused reading up on the forums.

Also, is there a config that would allow rEFIt to see all three systems at bootup (mac, ubuntu, and w7) instead of just mac and windows (which launches grub where you select either ubuntu or windows)?

Thanks again

---

### Post by oldfred on 2010-12-09
I am not familar with Mac and rEFIt. You would do better to ask in  the Apple forum on exactly how to set it up. I have seen many posts but have not followed all the details on triple booting in the Apple forum.

On non-Apple systems you just install grub to the MBR and it finds all the other OS's on the computer. With Apple I think it is different.

[http://ubuntuforums.org/search.php?searchid=77976767](http://ubuntuforums.org/search.php?searchid=77976767)

---

