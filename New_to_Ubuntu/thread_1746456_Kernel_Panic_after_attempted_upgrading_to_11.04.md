---
title: "Kernel Panic after attempted upgrading to 11.04"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by djmac on 2011-05-01
Hi all,

I attempted to upgrade my desktop from 10.10 to 11,04 over the weekend and failed dismally. 

Attempted the upgrade through the update manager ("New Ubuntu release 11.04 is available"). 

Seemed to go perfectly according to plan until reboot (doesn't seem to boot at all):

```
1.8418971 Kernal panc - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Does anyone know what has happened or how I should be able to fix it? Is it possible to be able to 'recover' this upgrade?

Fortunately, I can boot in with a live CD (and all my files and settings seem to be still there and intact) - and it would be good to be able to maintain these without too much hassle. 

Cheers.

---

### Post by drs305 on 2011-05-01
If we take a look at your boot file status we can probably figure out why Grub isn't pointing to the correct files.

Please download the boot info script from the following site. Run the script while booted on the LiveCD and post the contents of RESULTS.txt

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by djmac on 2011-05-02
Thanks for your quick reply (and sorry for my delay)

Here is the contents of Results.txt - sorry it is quite large:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         609,517,568   625,141,759    15,624,192  82 Linux swap / Solaris
/dev/sda2    *          2,048   609,515,519   609,513,472  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        40a96f7f-50e1-48f4-826a-338c5c6429b2   swap                                     
/dev/sda2        bfc5adb8-4e22-43ee-a13f-546f39b79cda   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5ff1c2fe-aa93-445e-8037-ad97645da744   ext4       Movies                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3b7ca5e1-2173-4dd8-ab92-368cb415d571   ext4       Backup                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        dec2e0a7-bfa0-4aff-a2f7-baef7c69e876   ext4       TV                            
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/sda2 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=/dev/sda2 ro single 
	echo	'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda ro single 
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
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root bfc5adb8-4e22-43ee-a13f-546f39b79cda
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=bfc5adb8-4e22-43ee-a13f-546f39b79cda /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/sdb1 /media/Movies ext4 defaults,relatime
/dev/sdc1 /mnt/Backup ext4 defaults,relatime
/dev/sdd1 /media/TV ext4 defaults,relatime

=================== sda2: Location of files loaded by Grub: ===================


 270.7GB: boot/grub/core.img
  26.3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
  57.7GB: boot/initrd.img-2.6.35-23-generic
  67.9GB: boot/initrd.img-2.6.35-24-generic
  75.5GB: boot/initrd.img-2.6.35-25-generic
  75.6GB: boot/initrd.img-2.6.35-27-generic
  96.0GB: boot/initrd.img-2.6.35-28-generic
 270.7GB: boot/vmlinuz-2.6.35-22-generic
 272.7GB: boot/vmlinuz-2.6.35-23-generic
 272.7GB: boot/vmlinuz-2.6.35-24-generic
 272.7GB: boot/vmlinuz-2.6.35-25-generic
 272.7GB: boot/vmlinuz-2.6.35-27-generic
 272.7GB: boot/vmlinuz-2.6.35-28-generic
 151.3GB: boot/vmlinuz-2.6.38-8-generic
  96.0GB: initrd.img
  75.6GB: initrd.img.old
 272.7GB: vmlinuz
 272.7GB: vmlinuz.old
```

---

### Post by fabricator4 on 2011-05-02
> **djmac said:**
> Thanks for your quick reply (and sorry for my delay)

Here is the contents of Results.txt - sorry it is quite large:

fstab is using the correct UUID to mount the boot drive.  Nothing jumps out at me (except weird sizes for the boot files but I've seen that before on working systems).

While waiting for DRS305 to come and have a look you should probably back up your data on sda2 if you haven't already done so.  Your data will be on /home/username on that drive.  Make sure you get all the .hidden files and directories (start with a '.') as this is where a lot of the settings and configuration is.

Chris.

---

### Post by drs305 on 2011-05-02
First, ensure your BIOS is booting from sda.

The files look ok, so perhaps just reinstalling Grub2 to point to the correct files may be enough. Note the Grub 1.99 of Natty uses a slightly different command switch than earlier versions.

From the LiveCD:```

sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```
In the second command, make sure you do NOT include the partition number.


Edit Added: *If it boots normally, then run 'sudo update-grub*

If you still can't boot, the next thing I'd ask is: from the grub prompt (press 'c' at the grub menu - hold down the SHIFT key if you don't get the menu):
```
ls (hd0,2)/  # Do you see 'vmlinuz' and 'initrd.img'
ls (hd0,2)/boot # Do you see the vmlinuz... and initrd files?
```

---

### Post by djmac on 2011-05-02
Thanks
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
Seemed to work okay:
```
Installation finished. No error reported.
```
However, the next step:
```
sudo update-grub
```
Threw up an error:
```
/usr/sbin/grub-probe: error: cannot stat 'aufs'.
```

(And it wouldn't boot). So I checked **ls (hd0,2)/** from the grub prompt. Both vmlinuz and initrd.img are presents (and so is vmlinuz.old and initrd.img.old, which could be relevant?)

Also checked **ls (hd0,2)/boot** . . . heaps of files. There were files of the form *vmlinuz-2.6.35-xx-generic* and *initrd.img-2.6.35-xx-generic* (where xx was between 22 and 28 ). There were other files in there as well. 

Thanks again.

---

### Post by drs305 on 2011-05-02
Sorry, the update-grub command should be run only after a normal boot. It won't work from the LiveCD. I'll edit the previous post.

So, if you haven't already, try booting. *If* it boots normally, *then* run 'sudo update-grub'.

---

### Post by djmac on 2011-05-02
Rigtheo ... attempted that. Didn't boot normally . . .

---

### Post by drs305 on 2011-05-02
> **djmac said:**
> Rigtheo ... attempted that. Didn't boot normally . . .

I have only two ideas left. The first is that your BIOS isn't seeing all of the disk (perhaps only the first 137GB). I didn't think you would get as far as you are if this is the case, but it's something to check:

Enter BIOS as the computer starts to boot and check the reported disk size. If it says the disk is only 137GB, see if there is a setting to enable large disks or LBA.
The other way to check is from the grub prompt (press 'c' at the menu). Try "ls (hd0,2)/boot/". Does it find the kernel and initrd.img... files? Try "ls (hd0,2)/boot/grub". Does it see lots of *.mod files?

 The other thing to try to get the system booting is to purge Grub2 completely and then reinstall. This often works when things appear to be normal. To do this from the LiveCD, you would mount sda2 and then 'chroot'. The procedures are in the 'Chroot' link in my signature line.

---

### Post by zdv on 2011-05-02
Happened to me too. Then I downloaded 11.04 live CD (32-bit) to make a clean install. The live CD won't boot either with the same error:

Kernel panc - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)


Ideas?

---

### Post by djmac on 2011-05-03
Thanks for you help drs305

I began your 'Chroot' instructions - Completed step one, and then when I attempted step two (confirm internet connectivity etc) I got this (familiar) message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a'
```

Which I did. I decided it was probably worth rebooting again (before completing the other steps), once the update was properly completed. And voila, computer booted into Natty without any errors! So for now, I haven't purged and re-installed grub2..

Unfortunately, X freezes on login (doesn't respond to input, mouse cursor can still move, but clicking has no effect etc etc). Other service/systems seem to work fine (e.g ssh, and can access content from apache server), just not the graphical console.  

As much as it is a bit of a pain, these are (I believe) an unrelated issue, so if you think it is appropriate, I might mark this as solved.

---

### Post by drs305 on 2011-05-03
> **djmac said:**
> As much as it is a bit of a pain, these are (I believe) an unrelated issue, so if you think it is appropriate, I might mark this as solved.

Your analysis is probably correct and you will get better help by starting a new thread with a title relating to your current situation. You may need to add a kernel option to the 'linux' line in the Grub menuentry but I'm not sure what it would be.

Hopefully you can get this resolved fairly quickly.

---

### Post by djmac on 2011-05-10
Thanks again.

It was unrelated issue ([http://ubuntuforums.org/showthread.php?t=1747781](http://ubuntuforums.org/showthread.php?t=1747781))

---

