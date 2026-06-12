---
title: "Can't load Windows"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Edward in CT on 2011-06-03
Hello Ubuntu people:
 
After installing 11.04 successfully, I tried to enter the windows partition and I get this screen.

"Windows failed to start.  A recent hardware or software change might be the cause.

To fix the problem
1. Insert your Windows installation disc and restart the computer.
2. Choose your language setup and then click "next"
3. Click repair your computer.

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

Status OxcOOOOOO

Info: The boot selection failed because a requried device is inaccessible.

When I'm in Ubuntu, I can mount the Windows partition and look at the files in it.  Can I rescue the partition?  I'm a total beginner.

Thanks,
Ed

---

### Post by munzerelli on 2011-06-03
what windows are you running?

---

### Post by JohnBonne on 2011-06-03
If you have Vista and above press f9 or esc at bootup to find your recovery options. XP has other recovery methods such as a recovery boot disk. (floppy drive) as well

When I installed Ubuntu I was warned in the instructions to Back Windows up. The install was a success. I used the Wubi installer. You may want that tool next time you install beside Windows.

I am also very new at this. 

Regards,

---

### Post by Edward in CT on 2011-06-03
Windows 7 starter on an Acer Aspire One netbook.  There is no recovery disk.

---

### Post by Rubi1200 on 2011-06-03
Hi,

if Ubuntu is booting normally, please do the following from within the Ubuntu install:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Edward in CT on 2011-06-03
[COLOR=Red][COLOR=Black]  OK Here it is in red (I couldn't figure out how to find the # sign on the toolbar)[/COLOR]




   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

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
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda4 and looks at sector 1 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    25,173,854    25,173,792   7 NTFS / exFAT / HPFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 NTFS / exFAT / HPFS
/dev/sda3          25,382,700   103,521,364    78,138,665   7 NTFS / exFAT / HPFS
/dev/sda4         103,522,303   312,576,681   209,054,379   f W95 Extended (LBA)
/dev/sda5         103,522,304   310,550,527   207,028,224  83 Linux
/dev/sda6         310,552,578   312,576,681     2,024,104  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A2EC8548EC8517A5                       ntfs       PQSERVICE
/dev/sda2        FA7485B074856FE5                       ntfs       SYSTEM RESERVED
/dev/sda3        7E6486DA64869515                       ntfs       Acer
/dev/sda5        cd38a0ae-66b5-473b-8b99-5cf3e35e3700   ext4       
/dev/sda6        7b3be3f3-3427-468d-93e7-78319b4d5dcd   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cd38a0ae-66b5-473b-8b99-5cf3e35e3700 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cd38a0ae-66b5-473b-8b99-5cf3e35e3700 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=cd38a0ae-66b5-473b-8b99-5cf3e35e3700 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=cd38a0ae-66b5-473b-8b99-5cf3e35e3700 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cd38a0ae-66b5-473b-8b99-5cf3e35e3700
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root A2EC8548EC8517A5
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root FA7485B074856FE5
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
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 141.511878967 = 151.947223040  boot/grub/core.img                             1
  70.484504700 = 75.682160640   boot/grub/grub.cfg                             1
  51.228343964 = 55.006015488   boot/initrd.img-2.6.35-28-generic              2
  71.753860474 = 77.045121024   boot/initrd.img-2.6.38-8-generic               3
 144.629699707 = 155.294957568  boot/vmlinuz-2.6.35-28-generic                 1
  54.730773926 = 58.766721024   boot/vmlinuz-2.6.38-8-generic                  1
  71.753860474 = 77.045121024   initrd.img                                     3
  51.228343964 = 55.006015488   initrd.img.old                                 2
  54.730773926 = 58.766721024   vmlinuz                                        1
 144.629699707 = 155.294957568  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

[/COLOR]

---

### Post by Rubi1200 on 2011-06-03
Thanks for posting the results.

I think you should try reinstalling GRUB using the LiveCD. Somehow, GRUB appears to have gotten on to the extended partition and this may be causing issues.

From a terminal:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

Once completed you can reboot taking out the CD.

Back in Ubuntu, run this to add Windows to the boot menu:

```
sudo update-grub
```

Let me know what happens and if this resolves the issue.

---

### Post by Edward in CT on 2011-06-04
Tried the first part except I used the term sudo grub install --*[COLOR=Red]r[/COLOR]*oot-directory=/mnt/boot /dev/sda.  It worked but now when I reboot with the Live CD out, I get into some Grub editing program that says at the top of the screen:  " GNU GRUB version 1.98 1ubuntu10 "

I can't now event get to Ubuntu, let alone to the terminal.

Help!

---

### Post by Rubi1200 on 2011-06-04
You have 11.04 installed according to the boot script and there is a reason why I gave you the command with boot not root:
 > 
n Grub 1.99, introduced with Ubuntu 11.04, Natty Narwhal, a new switch is available which more clearly defines where the *grub*  folder is placed. The command above will still work with Grub 1.99, but  the following command is preferred by the developers. The target  directory in the command is the command into which the grub folder will  be installed. By default, and without the switch, the location is */boot/grub*. In these instructions, since the Ubuntu partition is mounted on /mnt, the target would be */mnt/boot/grub*.  

[LIST]
[*]sudo grub-install --boot-directory=/mnt/boot /dev/sdXExample:  *sudo grub-install --**b**oot-directory=/mnt /dev/sd**a***
[/LIST]
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

I do find it odd that it said 1.98, but that is possible because this is an upgraded Ubuntu install.

Can I suggest you run the commands again and this time the way I gave it please?

---

### Post by Edward in CT on 2011-06-04
Ooops my bad.  Let me try and get back to you.

---

### Post by Edward in CT on 2011-06-04
OK I did what you said using "boot" (not root) directory and then doing "sudo update grub."  It got me my Ubuntu back (thanks) but  when I try to get into the Windows 7 partition, I still get that same screen I opened this thread with.  

When I did "sudo update-grub," it seemed to identify every partition and reported no problems so I'm lost.  Do you think this is a problem with Windows?  Thanks for all your help.

---

### Post by Rubi1200 on 2011-06-05
Okay, well obviously I am pleased that you can boot Ubuntu again.

As for the error booting Windows, yes I think that is likely a Windows issue.

I few things to check are BIOS settings and make sure nothing was inadvertently changed. 

Did this by any chance happen after resuming from suspend or hibernation?

You could also try booting the recovery partition on sda1 and running a chkdsk on the Windows partition from a command prompt:
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

I would wait on using the startup repair option until you have tried a chkdsk because the repair will overwrite the MBR and put the Windows bootloader back there.

On the other hand, you know now how to reinstall GRUB.

If I find more information, I will let you know.

---

