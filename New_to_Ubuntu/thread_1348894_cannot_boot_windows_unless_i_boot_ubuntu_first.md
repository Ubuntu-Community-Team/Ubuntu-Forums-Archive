---
title: "cannot boot windows unless i boot ubuntu first"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by drz4007 on 2009-12-07
hello guys. as i said i first have to boot ubuntu, then restart and then boot windows. if i dont do that windows don't boot. any ideas? thanx

---

### Post by u.b.u.n.t.u on 2009-12-07
Have you checked GRUB?

From Synaptic Package Manager search for and install startupmanager.

---

### Post by drz4007 on 2009-12-08
did that, but didnt help. same problem

---

### Post by u.b.u.n.t.u on 2009-12-08
Well I would suggest something else, but I suspect that such a move may prove to be a tad premature.

Are you able to post the results of GRUB?

---

### Post by ukripper on 2009-12-08
> **drz4007 said:**
> hello guys. as i said i first have to boot ubuntu, then restart and then boot windows. if i dont do that windows don't boot. any ideas? thanx

can you tell us:
How many Hardrives you have? 
Which version of ubuntu you are running? Is it 9.10, 9.04 or 8.04?

---

### Post by telovin on 2009-12-08
You can run sudo update-grub(applications-accessories-terminal)
which version of windows are you using?(xp?vista/7?)
Also u can check your harddrive partitions by going to applications-accessories-terminal
run sudo fdisk -l(its el)

---

### Post by drz4007 on 2009-12-08
> **telovin said:**
> You can run sudo update-grub(applications-accessories-terminal)
which version of windows are you using?(xp?vista/7?)
Also u can check your harddrive partitions by going to applications-accessories-terminal
run sudo fdisk -l(its el)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x825b57c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7354    59070973+   7  HPFS/NTFS
/dev/sda2            7355       30401   185125027+   5  Extended
/dev/sda5            7355       13729    51207156    7  HPFS/NTFS
/dev/sda6           29916       30401     3903763+  82  Linux swap / Solaris
/dev/sda7           13730       29915   130014013+  83  Linux

Partition table entries are not in disk order

ubuntu 9.10 and windows 7

---

### Post by telovin on 2009-12-09
Do u have windows 7 on sda1 or sda5(BOTH SHOWS NTFS PARTITION)? Could you run sudo update-grub and this will show you where your windows 7 is located. 

Also try the following. 

[LIST=1]
[*]Insert your win7cd/dvd. Press any key to boot from cd/dvd
[*]Select language and currency and click next.
[*]Install windows 7 screen will appear
[*]Select repair your computer
[*]Check use recovery tools that can help fix your computer
[*]Select startup repair(it might make changes and reboot your system a couple of times.Once it is done, you will get a screen which says "restart immediately, if repair was success windows will start normally,if repair was not a success.Start up repair might run again to continue fixing ur computer". Click finish and see if it works.(you might have to restart the system and see if it fixes the issue. Sometimes this might delete the grub from MBR. You might have to reinstall grub after this).The following link has screenshots on how to do startuprepair of win 7   " [http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm) "
[/LIST]

ukripper if you know  another way, please suggest the same. We will try different methods and see which one works.

---

### Post by JBAlaska on 2009-12-09
What happens when you try to boot win first? does it just hang or what?

Also try booting into win and force a chkdsk on reboot, maybe your NTFS partition has a error.

---

### Post by shailendra on 2009-12-09
It seems like the Windows MBR has been corrupted while installing Ubuntu. 

Try to fix the MBR.

You can refer to the "HOW TO" at the following link;
[http://ubuntuforums.org/showthread.php?t=822789](http://ubuntuforums.org/showthread.php?t=822789)

---

### Post by drz4007 on 2009-12-09
> **JBAlaska said:**
> What happens when you try to boot win first? does it just hang or what?

Also try booting into win and force a chkdsk on reboot, maybe your NTFS partition has a error.
 yes, it hangs. i just tried to fix any possible problems with the windows live cd but didnt find any problems. my windows partition is sda1. i will try the other suggestion and will get back to you guys. thanx

---

### Post by telovin on 2009-12-09
Is there any other hard drive which shows windows 7 boot loader other than sda1? if it does, then that could the problem.
When windows loads, does it show any error messages?
u can also try turning of AHCI in bios and try loading windows7.

---

### Post by drz4007 on 2009-12-09
> **telovin said:**
> Is there any other hard drive which shows windows 7 boot loader other than sda1? if it does, then that could the problem.
When windows loads, does it show any error messages?
u can also try turning of AHCI in bios and try loading windows7.
i changed the AHCI to IDE but that didnt help. it made it worse. i reinstalled windows, restored grub, and i still have the same problem! i think that the problem doesn't depend so much on booting linux first, but it seems that the windows "booter" doesn't work sometimes due to an unknown reason. sometimes windows boot, and sometimes they don't. i'm really confused...

---

### Post by presence1960 on 2009-12-09
> **drz4007 said:**
> i changed the AHCI to IDE but that didnt help. it made it worse. i reinstalled windows, restored grub, and i still have the same problem! i think that the problem doesn't depend so much on booting linux first, but it seems that the windows "booter" doesn't work sometimes due to an unknown reason. sometimes windows boot, and sometimes they don't. i'm really confused...

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by drz4007 on 2009-12-09
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x825b57c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   118,142,009   118,141,947   7 HPFS/NTFS
/dev/sda2         118,142,010   488,392,064   370,250,055   5 Extended
/dev/sda5         118,142,073   220,556,384   102,414,312   7 HPFS/NTFS
/dev/sda6         480,584,538   488,392,064     7,807,527  82 Linux swap / Solaris
/dev/sda7         220,556,448   480,584,474   260,028,027  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="30AC1197AC1158A4" TYPE="ntfs" 
/dev/sda5: UUID="13417EC26B2AD6B8" TYPE="ntfs" 
/dev/sda6: UUID="9c5b01b3-1572-434c-a896-b441656f2392" TYPE="swap" 
/dev/sda7: UUID="5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/va/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=va)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-11-generic
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 30ac1197ac1158a4
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9c5b01b3-1572-434c-a896-b441656f2392 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 112.9GB: boot/grub/grub.cfg
 112.9GB: boot/initrd.img-2.6.28-11-generic
 112.9GB: boot/initrd.img-2.6.28-14-generic
 112.9GB: boot/initrd.img-2.6.28-15-generic
 112.9GB: boot/initrd.img-2.6.28-16-generic
 112.9GB: boot/initrd.img-2.6.31-14-generic-pae
 112.9GB: boot/initrd.img-2.6.31-15-generic-pae
 112.9GB: boot/initrd.img-2.6.31-16-generic-pae
 112.9GB: boot/vmlinuz-2.6.28-11-generic
 112.9GB: boot/vmlinuz-2.6.28-14-generic
 112.9GB: boot/vmlinuz-2.6.28-15-generic
 112.9GB: boot/vmlinuz-2.6.28-16-generic
 112.9GB: boot/vmlinuz-2.6.31-14-generic-pae
 112.9GB: boot/vmlinuz-2.6.31-15-generic-pae
 112.9GB: boot/vmlinuz-2.6.31-16-generic-pae
 112.9GB: initrd.img
 112.9GB: initrd.img.old
 112.9GB: vmlinuz
 112.9GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-12-09
> **drz4007 said:**
> ```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x825b57c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   118,142,009   118,141,947   7 HPFS/NTFS
/dev/sda2         118,142,010   488,392,064   370,250,055   5 Extended
/dev/sda5         118,142,073   220,556,384   102,414,312   7 HPFS/NTFS
/dev/sda6         480,584,538   488,392,064     7,807,527  82 Linux swap / Solaris
/dev/sda7         220,556,448   480,584,474   260,028,027  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="30AC1197AC1158A4" TYPE="ntfs" 
/dev/sda5: UUID="13417EC26B2AD6B8" TYPE="ntfs" 
/dev/sda6: UUID="9c5b01b3-1572-434c-a896-b441656f2392" TYPE="swap" 
/dev/sda7: UUID="5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/va/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=va)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro vga=789  quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d ro single vga=789
	initrd	/boot/initrd.img-2.6.28-11-generic
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 30ac1197ac1158a4
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5a9742e6-ce47-4d4d-8cbb-fb0e48b3b98d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9c5b01b3-1572-434c-a896-b441656f2392 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 112.9GB: boot/grub/grub.cfg
 112.9GB: boot/initrd.img-2.6.28-11-generic
 112.9GB: boot/initrd.img-2.6.28-14-generic
 112.9GB: boot/initrd.img-2.6.28-15-generic
 112.9GB: boot/initrd.img-2.6.28-16-generic
 112.9GB: boot/initrd.img-2.6.31-14-generic-pae
 112.9GB: boot/initrd.img-2.6.31-15-generic-pae
 112.9GB: boot/initrd.img-2.6.31-16-generic-pae
 112.9GB: boot/vmlinuz-2.6.28-11-generic
 112.9GB: boot/vmlinuz-2.6.28-14-generic
 112.9GB: boot/vmlinuz-2.6.28-15-generic
 112.9GB: boot/vmlinuz-2.6.28-16-generic
 112.9GB: boot/vmlinuz-2.6.31-14-generic-pae
 112.9GB: boot/vmlinuz-2.6.31-15-generic-pae
 112.9GB: boot/vmlinuz-2.6.31-16-generic-pae
 112.9GB: initrd.img
 112.9GB: initrd.img.old
 112.9GB: vmlinuz
 112.9GB: vmlinuz.old
```

I am not entirely sure because it is windows 7 but did you add a grub loader to the windows boot files? Maybe that /grldr is part of windows 7 boot files, maybe it is not. As far as I know windows 7 is mostly like Vista. here is my Vista output from the script. note the red.

```
sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]
```

here is yours:


```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr[/COLOR]
```

If that is some sort of grub loader you added to the boot files that would be why it keeps looping back to GRUB.

Edit: I googled that and you have added grub4dos, that is what the /grldr is. You may want to remove that so when GRUB 2 tries to boot windows it can.

---

### Post by drz4007 on 2009-12-09
> **presence1960 said:**
> I am not entirely sure because it is windows 7 but did you add a grub loader to the windows boot files? Maybe that /grldr is part of windows 7 boot files, maybe it is not. As far as I know windows 7 is mostly like Vista. here is my Vista output from the script. note the red.

```
sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]
```

here is yours:


```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr[/COLOR]
```

If that is some sort of grub loader you added to the boot files that would be why it keeps looping back to GRUB.

Edit: I googled that and you have added grub4dos, that is what the /grldr is. You may want to remove that so when GRUB 2 tries to boot windows it can.
i really dont have an idea what that is... i didnt add anything, at least on purpose. if that was the case reinstalling windows should have fixed the problem, shouldn't it...?

---

### Post by presence1960 on 2009-12-09
> **drz4007 said:**
> i really dont have an idea what that is... i didnt add anything, at least on purpose. if that was the case reinstalling windows should have fixed the problem, shouldn't it...?

I am not familiar with GRUB4DOS. here is a [link]("http://grub4dos.sourceforge.net/wiki/index.php/Main_Page"), which when read will confirm you have installed GRUB4DOS. That /grldr in your boot files for Windows is the culprit. Maybe you can google on how to uninstall GRUB4DOS and that will allow your GRUB 2 to work as intended.

---

### Post by drz4007 on 2009-12-09
i wiil try that and i'll get back.thanx

---

### Post by drz4007 on 2009-12-09
ya man. it was this **grldr**. i erased it from my c: drive and everything works like a charm. (for future reference it is a hidden file in c: drive. while in linux i mounted that drive, since i couldn't boot windows, and erased it). i really have no idea how did this file come up. thanx anyway

---

### Post by presence1960 on 2009-12-09
> **drz4007 said:**
> ya man. it was this **grldr**. i erased it from my c: drive and everything works like a charm. (for future reference it is a hidden file in c: drive. while in linux i mounted that drive, since i couldn't boot windows, and erased it). i really have no idea how did this file come up. thanx anyway

excellent!! Enjoy Ubuntu.

---

### Post by telovin on 2009-12-10
drZ, good to know it is solved:)

---

