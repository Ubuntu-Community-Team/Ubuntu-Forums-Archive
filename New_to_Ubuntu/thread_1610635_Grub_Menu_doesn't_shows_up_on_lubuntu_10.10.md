---
title: "Grub Menu doesn't shows up on lubuntu 10.10"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by eflix on 2010-10-31
Hello, I'm having problems with grub2. I recently installed windows on my dev/sda1 partition, and after that I reinstalled (several times trying because the menu never appeared) grub2 with the following commands:
(/dev/sda2 is my linux partition)
```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sda

```
None of the last reported errors.
After that, and because the mentioned menu doesn't show up I did update-grub2, grub-setup, grub-mkconfig, etc, still I'm having the same problem.
I can get to boot to windows from the grub console, but I couldnt guess the commands to boot linux. I can see both windows and linux installations, the question is how do I put entries for both windows xp and lubuntu If now I cant manually edit de .cfg grub file?

---

### Post by Quackers on 2010-10-31
Welcome to UF.
It will give a better idea of your disk layout if you will go to the site below and download the boot script to your desktop then run it in a terminal with the command shown on that site.
This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it into your next post using code tags. For code tags select New Reply and click on the # symbol in the toolbar.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oldfred on 2010-11-01
Run the script as suggested by Quackers, so we can see if there are other issues.

[http://ubuntuforums.org/showthread.php?p=10024685](http://ubuntuforums.org/showthread.php?p=10024685)
drs305 says osprober may not be installed with lubuntu.

sudo os-prober

If it doesn't run, install it, then run update-grub again and check the menuentries.
 
     sudo apt-get install os-prober

---

### Post by eflix on 2010-11-01
Here I post the RESULTS.txt file: 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros, 160836480 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    78,125,055    78,123,008   7 HPFS/NTFS
/dev/sda2          78,125,056   117,186,559    39,061,504  83 Linux
/dev/sda3         117,188,606   160,835,583    43,646,978   5 Extended
/dev/sda5         117,188,608   120,117,247     2,928,640  83 Linux
/dev/sda6         120,119,296   160,835,583    40,716,288  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   310,472,189   310,472,127  83 Linux
/dev/sdb2         310,472,190   312,576,704     2,104,515  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ACC803B2C8037A3A                       ntfs                                     
/dev/sda2        b7acf0fe-35a9-4f8e-aca0-c5f371856b4d   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9b229fd1-fb9b-446b-938a-05711c1604a6   ext4                                     
/dev/sda6        b940bc73-1cfa-4c21-a705-b438127ee82f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         062f0bd1-8930-4d3c-8d0f-1cf01371210b   reiserfs                                 
/dev/sdb1        627ca2bc-f2fc-4d0d-96ee-d15d20aeaadb   reiserfs                                 
/dev/sdb2        087340db-19c1-4eef-a139-ff93f9b80cc4   swap                                     
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda2/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b7acf0fe-35a9-4f8e-aca0-c5f371856b4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set b7acf0fe-35a9-4f8e-aca0-c5f371856b4d
set locale_dir=($root)/boot/grub/locale
set lang=es
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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
UUID=b7acf0fe-35a9-4f8e-aca0-c5f371856b4d /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=9b229fd1-fb9b-446b-938a-05711c1604a6 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=b940bc73-1cfa-4c21-a705-b438127ee82f /home           ext4    defaults        0       2
# /media/sdb1 was on /dev/sdb1 during installation
UUID=627ca2bc-f2fc-4d0d-96ee-d15d20aeaadb /media/sdb1     reiserfs defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=087340db-19c1-4eef-a139-ff93f9b80cc4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  50.8GB: boot/grub/core.img
  50.8GB: boot/grub/grub.cfg

============================= sda5/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set b7acf0fe-35a9-4f8e-aca0-c5f371856b4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 9b229fd1-fb9b-446b-938a-05711c1604a6
	linux	/vmlinuz-2.6.35-22-generic root=UUID=b7acf0fe-35a9-4f8e-aca0-c5f371856b4d ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 9b229fd1-fb9b-446b-938a-05711c1604a6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=b7acf0fe-35a9-4f8e-aca0-c5f371856b4d ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 9b229fd1-fb9b-446b-938a-05711c1604a6
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 9b229fd1-fb9b-446b-938a-05711c1604a6
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

=================== sda5: Location of files loaded by Grub: ===================


  60.1GB: grub/core.img
  60.1GB: grub/grub.cfg
  60.1GB: initrd.img-2.6.35-22-generic
  60.1GB: vmlinuz-2.6.35-22-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by oldfred on 2010-11-01
You also have other problems.

You have part of grub installed to your windows partition.You should delete this folder /boot. Check to make sure there are not any windows files, there should not be any as it is a grub folder.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

Your grub in the MBR is booting sda2, but the grub.cfg shows no systems. Your fstab says you have a /boot, but it looks like you tried to reinstall grub without mounting the /boot also. (part of why for standard desktops I do not recommend separate /boot partitions). Your systems are in the /boot partition sda5.

You either need to reinstall without the /boot as a separate partition or reinstall grub but mount both the /boot partition & the root partition before installing grub to sda.

If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda5 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

More info here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by eflix on 2010-11-01
> **oldfred said:**
> Run the script as suggested by Quackers, so we can see if there are other issues.

[http://ubuntuforums.org/showthread.php?p=10024685](http://ubuntuforums.org/showthread.php?p=10024685)
drs305 says osprober may not be installed with lubuntu.

sudo os-prober

If it doesn't run, install it, then run update-grub again and check the menuentries.
 
     sudo apt-get install os-prober

I ran os-prober from the live cd, this is the output:
```
ubuntu@ubuntu:/mnt/sda2$ sudo os-prober 
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sda2:Ubuntu 10.10 (10.10):Ubuntu:linux
ubuntu@ubuntu:/mnt/sda2$ 

```
After that, I ran update-grub, (I had to chroot to /mnt/sda2) 
```
root@ubuntu:/# update-grub
Generating grub.cfg ...
done

```
After that an ls -l shows us that grub.cfg has changed two minutes ago.
I cant run os-prober after I chroot /mnt/sda2.

---

### Post by eflix on 2010-11-01
> **oldfred said:**
> You also have other problems.

You have part of grub installed to your windows partition.You should delete this folder /boot. Check to make sure there are not any windows files, there should not be any as it is a grub folder.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

Your grub in the MBR is booting sda2, but the grub.cfg shows no systems. Your fstab says you have a /boot, but it looks like you tried to reinstall grub without mounting the /boot also. (part of why for standard desktops I do not recommend separate /boot partitions). Your systems are in the /boot partition sda5.

You either need to reinstall without the /boot as a separate partition or reinstall grub but mount both the /boot partition & the root partition before installing grub to sda.

If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda5 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

More info here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Mounting the boot partition was the part I had missing, after doing that I could boot into lubuntu, and then I did this:
```
l(root@ubuntu)-(0)-(02:31 AM Mon Nov 01)->
m-(~)-(56 files, 2.1Gb)--> os-prober 
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/bin/ls: cannot access .gvfs: Permission denied

l(root@ubuntu)-(0)-(02:31 AM Mon Nov 01)->
m-(~)-(56 files, 2.1Gb)--> update-grub2 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
/bin/ls: cannot access .gvfs: Permission denied
```
Which finally gave access to both windows and linux.
Thanks Quackers and Oldfred!

---

