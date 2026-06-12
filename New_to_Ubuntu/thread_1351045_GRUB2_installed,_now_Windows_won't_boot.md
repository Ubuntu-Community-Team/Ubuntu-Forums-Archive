---
title: "GRUB2 installed, now Windows won't boot"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-10
I run Ubuntu from an HDD connected to my laptop by USB.

Since intrepid, the configuration is such that if my USB HDD is attached, Ubuntu boots, but if it isn't, Windows boots.

This has worked fine for ages, but yesterday came the upgrade/update package from Canonical that included GRUB2.

(I had thought that GRUB2 was incorporated into karmic, which I installed fresh a few weeks ago, but it would seem that that was GRUB 1.97 beta, for some reason.)

When GRUB2 installed yesterday, my internal HDD was connected, and it would seem that the installation process put it onto its MBR, not the MBR on my Ubuntu HDD. This now means that when I try to boot without my USB HDD attached, my PC no longer boots Windows.

Can anyone help me resolve this rather serious problem please?

---

### Post by Roger Allott on 2009-12-10
I don't know why, but this thread doesn't seem to appear on the forum's list, so I wonder whether it will now appear after I bump it.

---

### Post by Roger Allott on 2009-12-10
This forum is acting weird. On the Absolute Beginners Forum, the most recent thread is showing as having had its last post added 9 hours ago.

What's going on?

---

### Post by Roger Allott on 2009-12-10
There are a few fixes on this issue on this forum, but most seem to date from 2008 and revolve around a package named ms-sys. But that package is not showing up as being in Synaptic, and there's mention elsewhere that it breaks some Microsoft copyright or other.



BTW, could someone who's reading this just reply to this thread so that I at least feel comfortable that this is showing up on some forum and isn't lost in some virtual parallel universe?

---

### Post by Roger Allott on 2009-12-10
bump again

---

### Post by presence1960 on 2009-12-10
> **Roger Allott said:**
> I run Ubuntu from an HDD connected to my laptop by USB.

Since intrepid, the configuration is such that if my USB HDD is attached, Ubuntu boots, but if it isn't, Windows boots.

This has worked fine for ages, but yesterday came the upgrade/update package from Canonical that included GRUB2.

(I had thought that GRUB2 was incorporated into karmic, which I installed fresh a few weeks ago, but it would seem that that was GRUB 1.97 beta, for some reason.)

When GRUB2 installed yesterday, my internal HDD was connected, and it would seem that the installation process put it onto its MBR, not the MBR on my Ubuntu HDD. This now means that when I try to boot without my USB HDD attached, my PC no longer boots Windows.

Can anyone help me resolve this rather serious problem please?

It would indeed seem that GRUB 2 is installed on your internal disk's MBR. It is a relatively easy 2-step fix. But I want to be sure first. 

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Roger Allott on 2009-12-10
> **presence1960 said:**
> It would indeed seem that GRUB 2 is installed on your internal disk's MBR. 
That certainly sound feasible. I should have removed my internal HDD when I saw that Ubuntu wanted to update my version of Grub. D'OH!


> **presence1960 said:**
> 
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I think I did that right, so here's what's in RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=688df683-e46e-4be5-8979-0d850c67d15a)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x509ee0a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048   217,948,159   193,370,112   7 HPFS/NTFS
/dev/sda4         217,948,160   312,578,047    94,629,888   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301487 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     4,209,029     4,208,967  82 Linux swap / Solaris
/dev/sdb2    *      4,209,030    46,154,744    41,945,715  83 Linux
/dev/sdb3          46,154,745    53,898,074     7,743,330  83 Linux
/dev/sdb4          53,898,075   156,296,384   102,398,310   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A2401BBF401B995D" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="CEA61E2BA61E1515" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="DC0E219E0E2172A6" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: UUID="7551d527-6cc4-4f42-9f68-7d2cead50e3c" TYPE="swap" 
/dev/sdb2: UUID="688df683-e46e-4be5-8979-0d850c67d15a" TYPE="ext4" 
/dev/sdb3: LABEL="OLD-HOME" UUID="e8714d41-bba5-4764-bb96-957fa7b188a1" TYPE="ext3" 
/dev/sdb4: UUID="7F2A3353027874FC" LABEL="EXTRA" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/stuart/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stuart)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb3 on /media/OLD-HOME type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb4 on /media/EXTRA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/SYSTEM type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
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
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a2401bbf401b995d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cea61e2ba61e1515
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=688df683-e46e-4be5-8979-0d850c67d15a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=7551d527-6cc4-4f42-9f68-7d2cead50e3c none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


   2.1GB: boot/grub/grub.cfg
   2.1GB: boot/initrd.img-2.6.31-14-generic
   2.1GB: boot/initrd.img-2.6.31-15-generic
   2.1GB: boot/initrd.img-2.6.31-16-generic
   2.1GB: boot/initrd.img-2.6.31-9-rt
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   2.1GB: boot/vmlinuz-2.6.31-15-generic
   2.1GB: boot/vmlinuz-2.6.31-16-generic
   2.1GB: boot/vmlinuz-2.6.31-9-rt
   2.1GB: initrd.img
   2.1GB: initrd.img.old
   2.1GB: vmlinuz
   2.1GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-12-10
> **Roger Allott said:**
> That certainly sound feasible. I should have removed my internal HDD when I saw that Ubuntu wanted to update my version of Grub. D'OH!




I think I did that right, so here's what's in RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=688df683-e46e-4be5-8979-0d850c67d15a)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x509ee0a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048   217,948,159   193,370,112   7 HPFS/NTFS
/dev/sda4         217,948,160   312,578,047    94,629,888   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301487 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     4,209,029     4,208,967  82 Linux swap / Solaris
/dev/sdb2    *      4,209,030    46,154,744    41,945,715  83 Linux
/dev/sdb3          46,154,745    53,898,074     7,743,330  83 Linux
/dev/sdb4          53,898,075   156,296,384   102,398,310   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A2401BBF401B995D" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="CEA61E2BA61E1515" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="DC0E219E0E2172A6" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: UUID="7551d527-6cc4-4f42-9f68-7d2cead50e3c" TYPE="swap" 
/dev/sdb2: UUID="688df683-e46e-4be5-8979-0d850c67d15a" TYPE="ext4" 
/dev/sdb3: LABEL="OLD-HOME" UUID="e8714d41-bba5-4764-bb96-957fa7b188a1" TYPE="ext3" 
/dev/sdb4: UUID="7F2A3353027874FC" LABEL="EXTRA" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/stuart/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stuart)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb3 on /media/OLD-HOME type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb4 on /media/EXTRA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/SYSTEM type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
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
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 688df683-e46e-4be5-8979-0d850c67d15a
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=688df683-e46e-4be5-8979-0d850c67d15a ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a2401bbf401b995d
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cea61e2ba61e1515
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=688df683-e46e-4be5-8979-0d850c67d15a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=7551d527-6cc4-4f42-9f68-7d2cead50e3c none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


   2.1GB: boot/grub/grub.cfg
   2.1GB: boot/initrd.img-2.6.31-14-generic
   2.1GB: boot/initrd.img-2.6.31-15-generic
   2.1GB: boot/initrd.img-2.6.31-16-generic
   2.1GB: boot/initrd.img-2.6.31-9-rt
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   2.1GB: boot/vmlinuz-2.6.31-15-generic
   2.1GB: boot/vmlinuz-2.6.31-16-generic
   2.1GB: boot/vmlinuz-2.6.31-9-rt
   2.1GB: initrd.img
   2.1GB: initrd.img.old
   2.1GB: vmlinuz
   2.1GB: vmlinuz.old
```
The good news is we are right, and your sdb disk has GRUB already installed to MBR so it will be a one step process.

You will need your Windows vista install DVD, which you may not have as you have recovery partition for Vista on sda1. If your manufacturer hasn't given you the option to access Vista Recovery Console you can download an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it as an image to CD and use that. it will not install Vista, only give you access to Recovery Console.

Once you are set with the CD/DVD unplug your external disk and then boot the CD/DVD. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista.

When done reboot and check to see you boot right to Vista. Then plug in the external and reboot and see if GRUB loads. Hopefully we won't have to install GRUB also

---

### Post by Roger Allott on 2009-12-10
Many thanks for helping. I'm downloading the iso via Deluge right now and will follow your directions, but I have the feeling this is going to take a bit of time!

---

### Post by Roger Allott on 2009-12-10
First stage done, in that I'm now booting fine into Windows.

Now onto stage 2, checking whether I can still boot Ubuntu.

---

### Post by Roger Allott on 2009-12-10
Stage 2 seems good too, as Ubuntu boots exactly as it used to.

The one concern I have is that the GRUB2 update yesterday obviously hasn't installed correctly on sdb, as it installed itself on sda.

As it was shown on Update Manager as a security update, I presume it's quite important.

Should I now remove my internal HDD (sda), reboot Ubuntu, and reinstall all the grub packages? If so, is it better to do that via Synaptic or Terminal?

---

### Post by meierfra. on 2009-12-10
> The one concern I have is that the GRUB2 update yesterday obviously hasn't installed correctly on sdb, as it installed itself on sda.

Run

```
sudo dpkg-reconfigure grub-pc
```

This will let choose which MBR Grub should be installed to during updates.
(use the  "arrow" and "space" keys to select /dev/sdb).

---

### Post by presence1960 on 2009-12-10
> **meierfra. said:**
> Run

```
sudo dpkg-reconfigure grub-pc
```

This will let choose which MBR Grub should be installed to during updates.
(use the  "arrow" and "space" keys to select /dev/sdb).

Thanks meirfra. I learned something today again.

---

### Post by Roger Allott on 2009-12-10
Thanks.

The first thing it tells/asks me has got me a tad confused.
```
The following Linux command line was extracted from /etc/default/grub or the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it is correct, and modify it if necessary.

Linux command line:

vga=769
```

How can I know whether that is correct or not?

Something that raises a bit of an alarm bell is that the first thing that happens when I boot (straight after the bootloader option screen) is a message saying something suspiciously similar to:
```
vga=769 has been deprecated
```

But then it carries on and loads Ubuntu anyway.

---

### Post by presence1960 on 2009-12-10
> **Roger Allott said:**
> Thanks.

The first thing it tells/asks me has got me a tad confused.
```
The following Linux command line was extracted from /etc/default/grub or the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it is correct, and modify it if necessary.

Linux command line:

vga=769
```

How can I know whether that is correct or not?

Something that raises a bit of an alarm bell is that the first thing that happens when I boot (straight after the bootloader option screen) is a message saying something suspiciously similar to:
```
vga=769 has been deprecated
```

But then it carries on and loads Ubuntu anyway.
I get a similar message on Sabayon 5.0 when it boots, but have never had a problem, so I left well enough alone. I have no idea what it means, maybe meierfra will know.

EDIT: I found a [thread]("http://ubuntuforums.org/showthread.php?p=8420347") on here. Investigate and see if your /etc/default/grub has the same error. Open a terminal and run ```
gksu gedit /etc/default/grub
``` and see what you have.

---

### Post by Roger Allott on 2009-12-10
Many thanks for all your help guys. I hope I've resolved most of the issues with booting now, but I've got one last query.

I've just run
```
sudo update-grub
```
to create a new cfg file as the other thread suggested. This was the output:
```
:~$ sudo update-grub
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-9-rt
Found initrd image: /boot/initrd.img-2.6.31-9-rt
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
```
What intrigues me is why I have so many varieties of linux on my system. Why would I want to retain the versions of the linux image that were, I presume, replaced by 2.6.31-16?

---

### Post by harrisonk on 2009-12-10
[SIZE=4]Hello

The reason is because ubuntu doesn't uninstall the old Linux images to do that go to the synaptic and search for that Linux image: Example,

linux-image-2.6.31-14-generic

right click and select mark for complete removal.

Hope this explains your question.

Harrisonk
[/SIZE]

---

### Post by presence1960 on 2009-12-10
> **harrisonk said:**
> [SIZE=4]Hello

The reason is because ubuntu doesn't uninstall the old Linux images to do that go to the synaptic and search for that Linux image: Example,

linux-image-2.6.31-14-generic

right click and select mark for complete removal.

Hope this explains your question.

Harrisonk
[/SIZE]
They are all kernel versions. The lowest #'s are the oldest. To uninstall them you want to remove linux-headers-2.6.31-x and linux-image-2.6.31-x
You can do that through Synaptic by marking for complete removal.

It is always a good idea but not necessary to leave the two most recent kernels, that way if the newer one does not boot you can boot into the older one.

---

### Post by raymondh on 2009-12-10
> **meierfra. said:**
> Run

```
sudo dpkg-reconfigure grub-pc
```

This will let choose which MBR Grub should be installed to during updates.
(use the  "arrow" and "space" keys to select /dev/sdb).

learned something new too.... thanks meierfra !

---

### Post by meierfra. on 2009-12-10
> thanks meierfra 
Actually all the credit goes to astron:

[http://ubuntuforums.org/showthread.php?p=8327173]("http://ubuntuforums.org/showthread.php?p=8327173")

---

### Post by ssulaco on 2009-12-10
> **presence1960 said:**
> 
It is always a good idea but not necessary to leave the two most recent kernels, that way if the newer one does not boot you can boot into the older one.
I agree,you 'll have a backup.


also,you can remove unwanted linux-images and headers by running 
```
sudo apt-get remove --purge 2.6.31-xx-*
```
where xx is the specific kernel you want to remove

---

### Post by ranch hand on 2009-12-11
I would remind folks that running;
```

sudo grub-install /dev/<the drive you want it on I use sda>

```
will when run from the OS you want as boot/root, set up that way for you.

If you have one or two OS' and are not going to put any more on right away, you would be better of with a custom menu with a symbolic menu entry for your Ubuntu.  It never needs updated.  You ca n then take away the executable permissions for 10_linux, 20_memtest86, 30 os-prober.

Makes life very easy.

You could even check the link in my sig and the first 3 links in it.

---

### Post by Roger Allott on 2009-12-11
> **presence1960 said:**
> They are all kernel versions. The lowest #'s are the oldest. To uninstall them you want to remove linux-headers-2.6.31-x and linux-image-2.6.31-x
You can do that through Synaptic by marking for complete removal.

It is always a good idea but not necessary to leave the two most recent kernels, that way if the newer one does not boot you can boot into the older one.

Thanks. That's what I was looking for - advice on whether one should remove the old kernels, and what the effect would be.

It seems to me that the default updating process used by Canonical/Ubuntu should leave just one previous kernel installed when it updates to a new version, perhaps with a question to the user to see whether he/she would prefer to keep more than that.

---

### Post by ranch hand on 2009-12-11
I am not sure why, but this is the way it has always been.  There are people that leave all the buggers on there.  This has gat to take up a lot of space.

---

