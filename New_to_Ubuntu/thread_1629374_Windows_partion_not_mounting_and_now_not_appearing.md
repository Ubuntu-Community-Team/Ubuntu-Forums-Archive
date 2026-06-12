---
title: "Windows partion not mounting and now not appearing in the GRUB"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Shadowgamon on 2010-11-23
about 2 weeks ago, the partition that I have windows vista installed in refused to mount when I loaded up ubuntu. Since I only used it for gaming, it didn't bother me much. But last night when I updated GRUB , it removed the partition (also the ubuntu/memtest options are doubled). Is there a way to revert/correct  this? If not can I get help switching to a different bootloader?

---

### Post by Jetso on 2010-11-23
Mmm, never heard of that happening. When you run update grub, what does it return?

---

### Post by Shadowgamon on 2010-11-23
assuming I did this properly 

```
sudo update-grub
```
?

I get this 


```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```
yeah I found it odd as well. I've only seen (in the forums ofc) of something similar occuring when the person updgrade to 10.04

---

### Post by oldfred on 2010-11-23
So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by Jetso on 2010-11-23
I hope you never ran the command ```
sudo chmod -x /etc/grub.d/30_os-prober
``` Because that would cause it to not show up. I don't think it would effect mounting though. 
If you haven't ran the above code you shouldn't have to do this, but just in case, run ```
sudo chmod +x /etc/grub.d/30_os-prober
``` That will re activate it.

---

### Post by Shadowgamon on 2010-11-23
okee dokee then :P 



                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920   170,454,499   170,372,580   7 HPFS/NTFS
/dev/sda3         170,455,038   312,580,095   142,125,058   5 Extended
/dev/sda5         170,455,040   306,696,191   136,241,152  83 Linux
/dev/sda6         306,698,240   312,580,095     5,881,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        2CE02EA7E02E76EC                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        34cfe792-fcfd-4409-98f7-7f567be711a8   ext4                                     
/dev/sda6        2b312a80-a215-4cf8-9b41-da2922ca6a59   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34cfe792-fcfd-4409-98f7-7f567be711a8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=34cfe792-fcfd-4409-98f7-7f567be711a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b312a80-a215-4cf8-9b41-da2922ca6a59 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 128.2GB: boot/grub/core.img
 101.0GB: boot/grub/grub.cfg
 128.3GB: boot/initrd.img-2.6.32-24-generic
 128.4GB: boot/initrd.img-2.6.32-25-generic
 128.4GB: boot/initrd.img-2.6.32-26-generic
 128.3GB: boot/vmlinuz-2.6.32-24-generic
 128.3GB: boot/vmlinuz-2.6.32-25-generic
 128.3GB: boot/vmlinuz-2.6.32-26-generic
 128.4GB: initrd.img
 128.4GB: initrd.img.old
 128.3GB: vmlinuz
 128.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

> **Jetso said:**
> I hope you never ran the command ```
sudo chmod -x /etc/grub.d/30_os-prober
``` Because that would cause it to not show up. I don't think it would effect mounting though. 
If you haven't ran the above code you shouldn't have to do this, but just in case, run ```
sudo chmod +x /etc/grub.d/30_os-prober
``` That will re activate it.
Didn't run that command as far as I know , but I gave it a shot anyway. no dice :(

---

### Post by oldfred on 2010-11-23
It is showing major issues with your windows partition. Have you run chkdsk lately?

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

You have to rerun chkdsk until there are no errors as it does not fix everything on each pass.

Only if it does not work.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Shadowgamon on 2010-11-24
I would try that, but alas, I can't boot into windows. Is the a way to boot into it without the GRUB?

---

### Post by Shadowgamon on 2010-11-24
I would try that, but alas, I can't boot into windows. Is the a way to boot into it without the GRUB?

---

### Post by oldfred on 2010-11-24
Download this repair CD for windows.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Shadowgamon on 2010-11-24
well, the recovery disk wouldn't run chkdsk on its own, requiring windows to start up to begin testing, which once again is a brickwall. 


god I hate catch 22s

---

### Post by oldfred on 2010-11-24
The recovery disk is supposed to run.

If not then you can try the testdisk fixes, but do not know if it will help or not. Link in previous post.

---

### Post by Shadowgamon on 2010-11-24
test disk tells me that both the MFT and $MFT are both bad.

Chckdisk cant run until I launch windows

:(

---

### Post by Shadowgamon on 2010-11-26
I ended up just reinstalling windows. So the problem is kinda solved :\

---

