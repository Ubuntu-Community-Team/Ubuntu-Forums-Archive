---
title: "Grub Rescue Issues"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by wilfgilbert on 2011-03-06
Hi, I just tried to install ubuntu onto my laptop by installing onto an   SD card. The installation seems to run successfully and then prompts me   to reboot. However once I do so I get nothing but a grub  rescue prompt,  the sd card is still in. This now means I can't access  the ubuntu I just  installed and I also can't access the windows  partition. As you can  imagine I'm a little worried :razz:. 

Please bear in mind I'm new to this and may come across as a bit dim!

I tried running a script I found on another forum here (link to script here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/))

and got this result:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,945,087    41,943,040  27 Hidden HPFS/NTFS
/dev/sda2    *     41,945,088    42,149,887       204,800   7 HPFS/NTFS
/dev/sda3          42,149,888   333,653,984   291,504,097   7 HPFS/NTFS
/dev/sda4         333,653,985   625,137,344   291,483,360   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
245 heads, 62 sectors/track, 1021 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    14,753,791    14,751,744  83 Linux
/dev/sdb2          14,755,838    15,521,791       765,954   5 Extended
/dev/sdb5          14,755,840    15,521,791       765,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        828E78DB8E78C8E5                       ntfs       RECOVERY                      
/dev/sda2        76787A037879C303                       ntfs       SYSTEM                        
/dev/sda3        01CBA5163B8003E0                       ntfs                                     
/dev/sda4        01CBA51778D559B0                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f95855f5-1582-44e9-9b67-194cb79524a3   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        53435190-112d-491b-b017-89bf6d930324   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/01CBA5163B8003E0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=f95855f5-1582-44e9-9b67-194cb79524a3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=f95855f5-1582-44e9-9b67-194cb79524a3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f95855f5-1582-44e9-9b67-194cb79524a3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 828e78db8e78c8e5
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 76787a037879c303
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=f95855f5-1582-44e9-9b67-194cb79524a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=53435190-112d-491b-b017-89bf6d930324 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/core.img
   2.7GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.35-27-generic-pae
   2.8GB: boot/vmlinuz-2.6.35-27-generic-pae
   1.7GB: initrd.img
   2.8GB: vmlinuz
```

---

### Post by YesWeCan on 2011-03-06
Why doesn't Canonical fix this?

The Ubuntu installer has put the Ubuntu bootloader (Grub) boot sector on your Windows drive, thus over-writing the Windows boot sector. That is why you can no longer boot Windows.

But the Grub boot sector code is looking on your Windows drive to find its files (/boot/grub/), which are on the SD drive. This is why you cannot boot Ubuntu either.


One solution is to boot off the install CD/USB again and reinstall Grub.
Once booted, run 'sudo fdisk -l' to check what the drive letters are. Sometimes they change when you boot off an external device.
Then 'sudo grub-install --root-directory=/dev/sdb1 /dev/sdb'
Assuming your SD drive is called sdb.
Then reboot telling your bios to boot off the SD.
If the bios cannot boot the SD you can fix the Grub on the Windows drive:
'sudo grub-install --root-directory=/dev/sdb1 /dev/sda'
Assuming the Windows drive is sda and the SD is sdb

Once you are back into Ubuntu, run 'sudo update-grub' to make sure Windows will appear in the Grub boot menu.

Assuming you were able to boot directly off the SD drive, you probably want to fix your Windows MBR. To do this you need to repair it using the Windows CD.

---

### Post by wilfgilbert on 2011-03-06
Thanks for the help, I'm quite happy to do this but I have no windows install disk (windows came pre-installed on my laptop).
Also running sudo fdisk -l gave me this ```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfeb50cb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20971520   27  Unknown
/dev/sda2   *        2611        2624      102400    7  HPFS/NTFS
/dev/sda3            2624       20769   145752048+   7  HPFS/NTFS
/dev/sda4           20770       38913   145741680    7  HPFS/NTFS

Disk /dev/sdb: 7948 MB, 7948206080 bytes
245 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15190 * 512 = 7777280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f82f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         972     7375872   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(918, 97, 11) logical=(971, 69, 24)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             972        1022      382977    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(918, 129, 42) logical=(971, 102, 25)
Partition 2 has different physical/logical endings:
     phys=(966, 47, 41) logical=(1021, 206, 30)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             972        1022      382976   82  Linux swap / Solaris

```

I'm not really sure what any of that means...

---

### Post by YesWeCan on 2011-03-06
I am not sure either. In fact, I didn't know it was possible to install Ubuntu on an SD card. But try anyhow.
sudo grub-install --root-directory=/dev/sdb1 /dev/sdb

and see if it reports without errors. Then try to boot from the SD.

There is a program called lilo that can restore your Windows MBR. From the live CD 'sudo lilo -M /dev/sda mbr'

---

### Post by wilfgilbert on 2011-03-06
Thanks for the help, I get this after mkdir: cannot create directory `/dev/sdb1': Not a directory
Doesn't sound great to me.

After sudo lilo -M /dev/sda mbr
I get sudo: lilo: command not found

---

### Post by YesWeCan on 2011-03-06
Try mounting the sdb1 partition
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb


I'll see if I can find out how to fix your Windows MBR.

---

### Post by wilfgilbert on 2011-03-06
continuing the theme of every command line entry giving an error... mount: block device /dev/sdb1 is write-protected, mounting read-only

Thanks for the continued help.

The next command then gives this: rm: cannot remove `/mnt/boot/grub/915resolution.mod': Read-only file system

---

### Post by YesWeCan on 2011-03-06
I don't know why the SD is mounting read-only.

try
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by wilfgilbert on 2011-03-06
That gives me: The Master Boot Record of  /dev/sda  has been updated.
sounds hopeful?

---

### Post by YesWeCan on 2011-03-06
Cross your digits and reboot into Windows...:-o

---

### Post by wilfgilbert on 2011-03-06
Thanks so much. Have an internet hug and a cyber pat on the back.


EDIT: I realise this is somewhat cheeky but any idea how to get the ubuntu side of the install to work?
If not don't worry.

---

### Post by YesWeCan on 2011-03-06
\\:D/
It's always a relief to get Windows back (some would disagree ;) ).

As for installing Ubuntu on your SD card, try Googling for some tutorials or start a fresh thread here entitled "How do I install on SD card?" or similar.

Be very careful when you install Ubuntu as to where the Grub boot-loader is installed. The Ubuntu installer is rather incompetent (in my opinion) and will overwrite and cripple your Windows MBR if you are not careful. There is an "advanced" tab in the installer in the partitioning section that let's you choose where the boot-loader goes.

---

### Post by drs305 on 2011-03-06
> **wilfgilbert said:**
> I realise this is somewhat cheeky but any idea how to get the ubuntu side of the install to work?
If not don't worry.

The original problem stemmed from the fact that Grub was installed and looked at your Windows partition for the Grub files, which obviously weren't there.

If your partition structure is ok (I'm not sure that it is) and Ubuntu is installed correctly (same disclaimer), and you can boot a LiveCD:

You can mount your SD card and install Grub2 to it. Then you would change your BIOS to boot first from the SD card, next from the Windows partition. Then, if the SD card is inserted at boot, you would have a choice of Ubuntu or Windows. If the card isn't inserted, the Windows (well, in your case Lilo bootloader) would boot (Windows).

From a LiveCD, confirm the Ubuntu partition. In my example, I'll assume it's the same as before (sdb1). If it's different, change the designation in the commands:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Note you don't put the partition number in the second command.

As long as you don't install Grub2 to sda (or whatever designation the Windows drive is), it won't affect your Windows boot. If the Ubuntu partition is screwed up or Ubuntu isn't correctly installed, it may not boot but if you remove the SD card your Windows should still boot normally.

---

### Post by YesWeCan on 2011-03-06
We tried that. There is some other problem that causes the SD partition to mount read-only.

---

### Post by drs305 on 2011-03-06
> **YesWeCan said:**
> We tried that. There is some other problem that causes the SD partition to mount read-only.

I don't use SD cards often, but I suspect the problem then is with the partition table. The "cylinder boundary" message isn't a problem but the other messages from the fdisk command probably are.

Using something like TestDisk may be able to sort it out but it could very well take longer to fix it than to reformat the SD and try installing Ubuntu again - especially if other SD cards mount without issue.

---

### Post by Dumpy Dumpster on 2011-03-06
If it is any comfort, I had ENDLESS attempts to boot Lubuntu off a Compact Flash drive with similar results to you - in the end I gave up and went back to a 'conventional HDD'.
I never found out why, but with a normal HDD, installaton was faultless and the system is running well.

---

### Post by wilfgilbert on 2011-03-06
> **drs305 said:**
> reformat the SD and try installing Ubuntu again

I may well try that.

---

