---
title: "Grub Is Gone, Feels Like A Big Mess, How To Get It Back???"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-30
I've gotten myself into a biiig mess. ^^;; Where to start, let's see...

So I'd pretty much given up on fixing Ubuntu. So I installed Linux Mint. Then I logged into Windows in order to delete the partition I'd created for Ubuntu, thinking that I could add that now free space back to my regular hard drive.

Didn't work. Even with Eaesus Partitioner, it didn't work. And I thought that if I deleted Ubuntu, I'd still at least have grub on Linux Mint.

That's where I was wrong.

Turns out that when I deleted Ubuntu, grub seems to have gone with it. And so, all I get when I restart the computer is a couple of lines of text (one of which says "grub" and asks for input, but I don't know what sort of code to input). The only way I can get into any OS now is via Live CD's/DVD's (I'm in Ubuntu 10.10 Live CD right now).

I tried installing grub via the Live CD but I don't think it sticks. I'm not sure really what I'm doing. Heeelp! ^^;; Thank you. x__x;;

---

### Post by oldfred on 2011-04-30
Use windows tools for windows & Linux tools for Linux.

If you installed Mint last its boot loader should have been in the MBR and controlled booting, unless you did not install it. But it seems like you are using the grub boot loader that is looking for the missing Ubuntu partition.

To see what is where, from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by unknowngal on 2011-04-30
> **oldfred said:**
> Use windows tools for windows & Linux tools for Linux.

If you installed Mint last its boot loader should have been in the MBR and controlled booting, unless you did not install it. But it seems like you are using the grub boot loader that is looking for the missing Ubuntu partition.

To see what is where, from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Unfortunately, this is all I got. :(

ubuntu@ubuntu:~$ ~/Downloads/boot_info_script055*.sh
bash: /home/ubuntu/Downloads/boot_info_script055.sh: Permission denied

---

### Post by unknowngal on 2011-04-30
Wait!! I got it!! I needed to move the file to my desktop. Here's the results!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden HPFS/NTFS
/dev/sda2    *     29,362,176    29,566,975       204,800   7 HPFS/NTFS
/dev/sda3          29,566,976   623,919,352   594,352,377   7 HPFS/NTFS
/dev/sda4         623,921,150   976,771,071   352,849,922   5 Extended
/dev/sda5         623,921,152   811,741,183   187,820,032  83 Linux
/dev/sda6         811,743,232   819,795,967     8,052,736  82 Linux swap / Solaris
/dev/sda7         970,291,200   976,771,071     6,479,872  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4C68DD3068DD1A12                       ntfs       PQSERVICE                     
/dev/sda2        8ED00E3DD00E2C51                       ntfs       SYSTEM RESERVED               
/dev/sda3        D0E0102CE0101B74                       ntfs       eMachines                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        91a7cb4e-38c7-456f-a568-75ddfb8d9e67   ext4                                     
/dev/sda6        1a6b4895-f8fb-4f66-81a2-79c378696b31   swap                                     
/dev/sda7        bc31d42c-8091-456c-bfb1-b14b1231b9bd   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt/temp                ext4       (rw)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda7)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=91a7cb4e-38c7-456f-a568-75ddfb8d9e67 ro  vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda7) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=91a7cb4e-38c7-456f-a568-75ddfb8d9e67 ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 91a7cb4e-38c7-456f-a568-75ddfb8d9e67
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c68dd3068dd1a12
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8ed00e3dd00e2c51
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41fb6590-08f1-4093-b44a-f4a5ae0366c0
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=41fb6590-08f1-4093-b44a-f4a5ae0366c0 ro vga=792 splash quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41fb6590-08f1-4093-b44a-f4a5ae0366c0
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=41fb6590-08f1-4093-b44a-f4a5ae0366c0 ro single vga=792 splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41fb6590-08f1-4093-b44a-f4a5ae0366c0
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=41fb6590-08f1-4093-b44a-f4a5ae0366c0 ro vga=792 splash quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41fb6590-08f1-4093-b44a-f4a5ae0366c0
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=41fb6590-08f1-4093-b44a-f4a5ae0366c0 ro single vga=792 splash
    initrd /boot/initrd.img-2.6.35-28-generic
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
# / was on /dev/sda7 during installation
UUID=91a7cb4e-38c7-456f-a568-75ddfb8d9e67 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=1a6b4895-f8fb-4f66-81a2-79c378696b31 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 386.2GB: boot/grub/core.img
 349.6GB: boot/grub/grub.cfg
 320.7GB: boot/initrd.img-2.6.35-22-generic
 386.2GB: boot/vmlinuz-2.6.35-22-generic
 320.7GB: initrd.img
 386.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 
```

---

### Post by oldfred on 2011-04-30
The grub in the MBR is looking to boot from sda7 which is now a swap partition.

You need to reinstall grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by unknowngal on 2011-04-30
> **oldfred said:**
> The grub in the MBR is looking to boot from sda7 which is now a swap partition.

You need to reinstall grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

I'm really sorry if I did this wrong, I've only been at all this for less than a month. *sheepish* But I basically followed the instructions of both the links, and unfortunately I got the following when I rebooted:

```
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

grub>_
```Now, here's where I'm wondering if I went wrong. Instead of choosing sda7, I chose sda5. Everything seemed to install correctly though, no errors found. Should I have followed the above steps for sda7 instead? Sorry if I sound confused.

And just now, I ran sudo update-grub and got this:

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

```Thank you for your patience. ^^;;

---

### Post by oldfred on 2011-04-30
No your install is now in sda5.

since your were at Ubuntu@ubuntu you were still on liveCD. You cannot run the sudo update-grub until you have rebooted. Have you rebooted and still gotten errors? Were you using the same liveCD as Mint. Different versions may be an issue, but liveCD will use the actual install and should work.

If so you need to try the full chroot method.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by unknowngal on 2011-04-30
> **oldfred said:**
> No your install is now in sda5.

since your were at Ubuntu@ubuntu you were still on liveCD. You cannot run the sudo update-grub until you have rebooted. Have you rebooted and still gotten errors? Were you using the same liveCD as Mint. Different versions may be an issue, but liveCD will use the actual install and should work.

If so you need to try the full chroot method.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Hmm...no, actually, when I went to reboot, the computer ejected my disk and asked me to take it out. I did that, and pressed enter. It rebooted and gave me that text I posted above, plus that **grub>_** line to enter code into. Should I restart with the Live DVD of Mint and run sudo update-grub there? I could try that now. :O If I still get issues, I'll follow the instructions on the links you gave me. :) *goes off to try*

---

### Post by unknowngal on 2011-04-30
It worked!! :) Thank you! :D

This was the specific part that helped:

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

Just one more question: Should I follow the Post-Restoration Commands? I did sudo update-grub again this time, and it went through alright. :) Should I do the other commands shown there?

Thanks a lot!! :D

---

### Post by Quackers on 2011-04-30
Well done :-)
If everything is working well you should be ok as it is.

---

### Post by unknowngal on 2011-04-30
Alright. :) *won't touch a thing then* :P Thanks!

---

