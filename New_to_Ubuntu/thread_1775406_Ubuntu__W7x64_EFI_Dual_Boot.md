---
title: "Ubuntu / W7x64 EFI Dual Boot"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by Oodar on 2011-06-04
Hi all,

I've been attempting for the past day or so to get Grub to boot into my W7 EFI installation. I've followed several of the threads/guides on the forums but to no avail :(

The thread I've followed the most closely is this one: [http://ubuntuforums.org/showthread.php?t=1719851&page=9](http://ubuntuforums.org/showthread.php?t=1719851&page=9)

My setup is different from the one used in the thread, I just have W7 and Ubuntu installed to seperate partitions on the same drive.

As far as I can tell, the setup on the EFI partition is correct. Windows has placed all the files in the correct place (as shown at the post in the top of the link I gave above). In post #84 in the link above, skodabenz recommends attempting to boot using the EFI shell, this actually worked fine for me and windows booted without issue.

I have added an entry for windows into my 40_custom file Grub, identical to the example shown here: [https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

However, when I select this option from the Grub boot menu, I am simply left staring at a purple-y screen :(

I have ran the boot_info_script shown in other posts, its results are as follows:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400087375360 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781420655 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   781,420,654   781,420,654  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648   246,171,647   245,760,000 Data partition (Windows/Linux)
/dev/sda3     246,171,648   491,931,647   245,760,000 Data partition (Windows/Linux)
/dev/sda4     491,931,648   492,193,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5     492,193,792   494,193,792     2,000,001 Swap partition (Linux)
/dev/sda6     494,193,793   781,420,355   287,226,563 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D2DD-3BFF                              vfat       
/dev/sda2        3C76FED476FE8DC0                       ntfs       
/dev/sda3        04B6B1ABB6B19E1C                       ntfs       
/dev/sda4        ea28158b-27cb-3737-a8c1-04399673d5d6   hfsplus    
/dev/sda5        5dc3a8b1-839d-4bed-b24c-3d31e40a4b44   swap       
/dev/sda6        73f02739-e666-416e-9305-40db069aac2a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/WIN_7_X64_UEFI_ISO9660 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=73f02739-e666-416e-9305-40db069aac2a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=73f02739-e666-416e-9305-40db069aac2a

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
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        73f02739-e666-416e-9305-40db069aac2a
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=73f02739-e666-416e-9305-40db069aac2a ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        73f02739-e666-416e-9305-40db069aac2a
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=73f02739-e666-416e-9305-40db069aac2a ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, memtest86+
uuid        73f02739-e666-416e-9305-40db069aac2a
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt6)'
search --no-floppy --fs-uuid --set=root 73f02739-e666-416e-9305-40db069aac2a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt6)'
search --no-floppy --fs-uuid --set=root 73f02739-e666-416e-9305-40db069aac2a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt6)'
    search --no-floppy --fs-uuid --set=root 73f02739-e666-416e-9305-40db069aac2a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=73f02739-e666-416e-9305-40db069aac2a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt6)'
    search --no-floppy --fs-uuid --set=root 73f02739-e666-416e-9305-40db069aac2a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=73f02739-e666-416e-9305-40db069aac2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt6)'
    search --no-floppy --fs-uuid --set=root 73f02739-e666-416e-9305-40db069aac2a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt6)'
    search --no-floppy --fs-uuid --set=root 73f02739-e666-416e-9305-40db069aac2a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Windows 7"

menuentry "Windows UEFI" {
    search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=73f02739-e666-416e-9305-40db069aac2a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D2DD-3BFF  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda5 during installation
UUID=5dc3a8b1-839d-4bed-b24c-3d31e40a4b44 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 311.788670063 = 334.780535296  boot/grub/grub.cfg                             1
 275.827782154 = 296.167825920  boot/grub/menu.lst                             1
 237.177814960 = 254.667739648  boot/initrd.img-2.6.38-8-generic               1
 269.782780170 = 289.677054464  boot/vmlinuz-2.6.38-8-generic                  1
 237.177814960 = 254.667739648  initrd.img                                     1
 269.782780170 = 289.677054464  vmlinuz                                        1


```

Any help would be great, as I'm at my wits end!

---

### Post by srs5694 on 2011-06-04
Have you tried using [rEFIt](http://refit.sourceforge.net) for selecting between Linux and Windows? There's an Ubuntu package for it, but you'll need to copy the rEFIt files over to the EFI System Partition (which is probably mounted at /boot/efi in Linux) and telling your EFI to use it as the primary boot loader. I can't promise it'll work, since I don't currently have a working Windows installation in EFI, but for many things it seems more reliable than GRUB 2.

---

### Post by Oodar on 2011-06-04
> **srs5694 said:**
> Have you tried using [rEFIt]("http://refit.sourceforge.net") for selecting between Linux and Windows? There's an Ubuntu package for it, but you'll need to copy the rEFIt files over to the EFI System Partition (which is probably mounted at /boot/efi in Linux) and telling your EFI to use it as the primary boot loader. I can't promise it'll work, since I don't currently have a working Windows installation in EFI, but for many things it seems more reliable than GRUB 2.

I'll have a look at rEFIt but I was really hoping to get Grub working. Its so frustrating knowing that both OSs boot fine from the EFI shell but I cannot get Grub to call the appropriate commands to get Windows to boot :(

edit: I can't find the Ubuntu package for rEFIt. I tried sudo apt-get install refit (which also installed gptsync). I couldn't find anything else about how to actually install rEFIt as the bootloader.

edit2: So I found the files installed with the refit package when i did apt-get install and found that I'm going to need to bless the refit installation from OSX - which I am loathe to do right now. I would really rather fix grub to boot Windows!

Is there anything extra debug-wise I can get from Grub? It just sits on the purple screen when booting from the Windows UEFI option I added. Running the commands manually from Grub's prompt produces what appears to be an error message that says /EndEntire with a lot of other stuff mentioned.

---

### Post by Oodar on 2011-06-05
I created another entry in my 40_custom file, out of curiosity:

menuentry "Ubuntu EFI Test" {
    search --file --no-floppy --set=root /efi/ubuntu/grubx64.efi
    chainloader (${root})/efi/ubuntu/grubx64.efi
}

This works fine and just loops me back into grub. When I attempt to do the same with the windows efi location, it says something of the format:

```

/EndEntire
/ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)
/HD<a load of alphanumeric>
/EndEntire

```Any ideas? I am just guessing, but is this the windows bootloader complaining when grub attempts to handover to it?

---

### Post by Oodar on 2011-06-05
Ok, so I set debug=all and watched Grub attempt to boot my W7 EFI installation. It seems to be stuck in a loop attempting different file systems. I gave up watching it after about 20 minutes but it attempted the following:

zfs, ufs1, ufs2, xfs, udf, tarfs, squash4, sfs.

Each time it attempted a new fs, it would loop back through all the previous ones attempting them again.

I have no idea what is considered normal behaviour, so I'm unsure if this provides any further insight for anyone who might chance upon my thread.

---

### Post by Oodar on 2011-06-07
Update:

I've stuck refit on my efi partition. I attempted to add it to the efi boot list using efibootmgr:

```
sudo efibootmgr -v -c -L "refit" -l /boot/efi/refit/refit.efi
```This added it to the list that efibootmgr sees and I could see an option in the firmware (shown when I pressed DEL to load it during boot).

However, choosing it causes grub to load. I thought this was perhaps because something is wrong with the way I installed refit, so I rebooted and launched an EFI shell:

```

fs0:
cd EFI/refit/
refit.efi

```This launched refit, but with all the icons missing. It complains about not being able to find /Volumes. This is, afaik, where stuff tends to get mounted for OSX.

I rebooted my PC and attempted to chainload refit in Grub but recieved the same message I got previously when attempted to chainload the windows boot loader:

```

/EndEntire 
/ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12) 
/HD<a load of alphanumeric> 
/EndEntire

```I cannot find a reference as to what /EndEntire signals or what UnknownMessaging(12) is anywhere by googling.

I think I am fairly stuck from here onwards. Grub seems to not be interested in chainloading anything except itself. I guess if I could make rEFIt launch without having to go into an EFI shell it would be fine (as it successfully scans, finds and allows me to boot everything on my system). However, every boot loader I add using efibootmgr just fails and Grub ends up loading instead. I guess this could be to do with the command I'm issuing to efibootmgr, so if anyone could enlighten me on its proper use I would be grateful.

---

### Post by srs5694 on 2011-06-07
First, your efibootmgr command was just a little bit off. You've got to use the EFI's method of referring to files when you tell it what file to load, and that method uses backslashes rather than slashes to separate directory components. Because the Linux shell uses the backslash as a "quote" character, you've got to double them up in Linux. You must also refer to the file relative to the EFI System Partition's (ESP's) root, not the Linux system's root. Thus, your efibootmgr command should look something like this:

```

sudo efibootmgr -v -c -L "rEFIt" -L \\EFI\\refit\\refit.efi

```

This assumes that the file is identified as what Linux would call /boot/efi/EFI/refit/refit.efi -- in the "refit" subdirectory of the "EFI" directory in the ESP. Your earlier command looks like you placed it in the "refit" directory in the ESP, but boot loaders normally go in their own subdirectories of the "EFI" directory. The commands you typed at the EFI shell make it look like it's in the conventional place. The convention of mounting the ESP at /boot/efi in Linux makes this a bit confusing, since you've got references that double up on names (/boot/efi/EFI or /boot/efi/efi).

Second, as a reference, here's how I chainload to rEFIt from GRUB 2 on one of my VirtualBox test installations:

```

menuentry 'Chainload to rEFIt' {
    insmod fat
    set root='(hd0,1)'
    chainloader /EFI/rEFIt/refit.efi
}

```

I can't promise that'll work any better for you than what you've got now, but it does work for me under VirtualBox. Note that you'll need to change the "set root" line if your ESP is anything other than /dev/sda1 (in Linux terms). In theory, my method is susceptible to problems if the drive identifiers change, but fixing something later because of something that breaks is better than having something that's theoretically more robust but doesn't work at all!

Finally, if the messed-up icons and error messages bother you, you can always activate rEFIt's text mode. It's less pretty than a working GUI rEFIt, but it's less ugly than a broken rEFIt GUI. To activate text mode, edit the refit.conf file in the rEFIt directory and uncomment the "textonly" line. FWIW, the GUI icons used to work for me, but they've stopped working for some reason, and I haven't yet tracked down the cause.

---

### Post by Oodar on 2011-06-09
> **srs5694 said:**
> First, your efibootmgr command was just a little bit off. You've got to use the EFI's method of referring to files when you tell it what file to load, and that method uses backslashes rather than slashes to separate directory components. Because the Linux shell uses the backslash as a "quote" character, you've got to double them up in Linux. You must also refer to the file relative to the EFI System Partition's (ESP's) root, not the Linux system's root. Thus, your efibootmgr command should look something like this:

```

sudo efibootmgr -v -c -L "rEFIt" -L \\EFI\\refit\\refit.efi

```

This assumes that the file is identified as what Linux would call /boot/efi/EFI/refit/refit.efi -- in the "refit" subdirectory of the "EFI" directory in the ESP. Your earlier command looks like you placed it in the "refit" directory in the ESP, but boot loaders normally go in their own subdirectories of the "EFI" directory. The commands you typed at the EFI shell make it look like it's in the conventional place. The convention of mounting the ESP at /boot/efi in Linux makes this a bit confusing, since you've got references that double up on names (/boot/efi/EFI or /boot/efi/efi).

Second, as a reference, here's how I chainload to rEFIt from GRUB 2 on one of my VirtualBox test installations:

```

menuentry 'Chainload to rEFIt' {
    insmod fat
    set root='(hd0,1)'
    chainloader /EFI/rEFIt/refit.efi
}

```

I can't promise that'll work any better for you than what you've got now, but it does work for me under VirtualBox. Note that you'll need to change the "set root" line if your ESP is anything other than /dev/sda1 (in Linux terms). In theory, my method is susceptible to problems if the drive identifiers change, but fixing something later because of something that breaks is better than having something that's theoretically more robust but doesn't work at all!

Finally, if the messed-up icons and error messages bother you, you can always activate rEFIt's text mode. It's less pretty than a working GUI rEFIt, but it's less ugly than a broken rEFIt GUI. To activate text mode, edit the refit.conf file in the rEFIt directory and uncomment the "textonly" line. FWIW, the GUI icons used to work for me, but they've stopped working for some reason, and I haven't yet tracked down the cause.

Awesome, I now have refit working (without icons, sadly) and everything boots fine.

I tried to experiment with replacing the icons. The documentation states that you can override the icon by placing an .icns in the same directory as the efi file and giving it the same name. Icons still didn't load, though. 

I guessed it was something more serious and realised I didn't have the tools folder in the ESP along with refit. After putting that in the ESP, I got two icons that weren't displaying previously to show: the EFI shell and Partition Manager. Sadly, both of them don't work as the I get an error that says:

```
error: unsupported while loading (gptsync.efi/shell.efi)
```

As far as I can tell from googling, this seems to crop up when you are trying to use an efi file that is incorrect for the platform you are on.

Hopefully in the future I'll get the icons working so I can have a sexy boot screen, but this is brilliant in the mean time!

Cheers for the help!

---

### Post by srs5694 on 2011-06-10
I'm glad it's working for you now. I haven't looked into the rEFIt icons/display issues much just yet. The program was originally developed for Macs, where these problems don't crop up, so clearly there are some sort of platform-specific issues at work.

I do *not*, incidentally, recommend running the partitioning tool in rEFIt; that's actually a tool that creates a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is an ugly and dangerous hack that can get you into a lot of trouble. It is, sadly, necessary to get Windows booting on Macs, but Windows boots fine on a pure GPT configuration on UEFI-based PCs. I recommend deleting the gptsync.efi file from your EFI System Partition, just to make certain that you don't accidentally run the program.

---

