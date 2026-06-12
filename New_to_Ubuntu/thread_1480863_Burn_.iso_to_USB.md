---
title: "Burn .iso to USB"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by jaansson on 2010-05-12
Hello!

I've downloaded a bootable .iso file (some windows vista rescue thing). I tried creating a bootable .iso with unetbootin, as I did before when I installed Lucid. However, this time it won't really boot.

It tries to boots, showing me a screen where I have to press enter. Then I come to this blue screen with silver background showing something about what option that I want to use. The problem is that there is only one option. And it's called "Default". And when I press it, nothing happens except that "10sec until auto select or whatever" timer restarts. 

I tried waiting until the timer ran out to see what would happen, but it was just the same thing. It makes like a 1/10 of a second short flickering, then restarts the timer. Weird? I'd sure like to think so! :) I've been looking for a solution for a few hours now, but I doubt I'm the first one with this problem. Probably just me looking in the wrong place. So does anyone have a solution?

Thanks in advance! Really need to get my Vista working for dual-boot again.

---

### Post by Abhijit Navale on 2010-05-12
What is this iso of? ubuntu? linux? any other distro? windows? vista? 7? or what?

---

### Post by jaansson on 2010-05-12
That is the windows vista rescue thing.

Vista_Recovery_Disc.iso

Everything that I've read about it is positive. Everyone seem to get it working, which is weird. I even tried formatting my USB.

---

### Post by wilee-nilee on 2010-05-12
> **jaansson said:**
> That is the windows vista rescue thing.

Vista_Recovery_Disc.iso

Everything that I've read about it is positive. Everyone seem to get it working, which is weird. I even tried formatting my USB.

Here is a link, I haven't used this as I don't have vista.
[http://xtreview.com/review207.htm](http://xtreview.com/review207.htm)
Hit control>f and type usb and you will right to the info.

---

### Post by jaansson on 2010-05-12
Thanks for the link. Might try if that windows aik thing works if I don't find a solution on how to make a bootable usb.

Anyway, I forgot to mention in my first post that I can't reach vista properly, so I need to do it from Ubuntu. And that thing was made for Windows. Might work through wine with a bit of luck, but I don't want to waste my precious bandwidth unless I really have to :)

---

### Post by wilee-nilee on 2010-05-12
> **jaansson said:**
> Thanks for the link. Might try if that windows aik thing works if I don't find a solution on how to make a bootable usb.

Anyway, I forgot to mention in my first post that I can't reach vista properly, so I need to do it from Ubuntu. And that thing was made for Windows. Might work through wine with a bit of luck, but I don't want to waste my precious bandwidth unless I really have to :)

You can scan the windows partitions with clamav if your problems are any malware, viri, rootkits,...etc. Have you tried the f8 option for safe mode.

---

### Post by jaansson on 2010-05-12
Havn't tried safe-mode actually. Not virus scanning either. Might try those. But I'm pretty sure vista have become corrupted or something, because I noticed it for the first time after I installed Lucid and I hade to repartition some partitions.

Heading for a scan now, thanks :)

---

### Post by wilee-nilee on 2010-05-12
> **jaansson said:**
> Havn't tried safe-mode actually. Not virus scanning either. Might try those. But I'm pretty sure vista have become corrupted or something, because I noticed it for the first time after I installed Lucid and I hade to repartition some partitions.

Heading for a scan now, thanks :)

You might have a booting problem, post this boot script and we will see whats going on. When you paste it into a reply highlight the text and click on the # in the reply gui panel. This puts it in a scrolling format that is easier to read.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
It is 2:15 am here so I may only be around for a little longer, but there are others that are on during the day pacific LA time after 12 noon that are very good at discerning problems with the script. You may not need the vista recovery cd but is useful to have one. Here is the one that is recommended most often.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by jaansson on 2010-05-12
Well, it actually starts booting Vista, that's the problem. Then everything kind of just crashes sooner or later. So the BIOS and everything works just fine. As well as GRUB finding my Vista install and Ubuntu kernel.

It's more like a "Can't make my USB boot thing" working :) It's actually that recovery cd that you linked to that I'm using. Or trying to use. My computer basically just don't know what to read from it is my new thought about it after some more info search about it. Maybe I'm just doing it wrong? And I've put USB first in the Boot BIOS thing.

---

### Post by wilee-nilee on 2010-05-12
I have never been able to get anything MS to boot with a usb/thumb device, but thats just me. I would post the script as it may be that this can be fixed with out using a vista recovery disk. But if you need to use it in the end, burn it to a CD, you haven't mentioned  whether you do or don't have the cd capability. You need to provide more information if you can.

---

### Post by jaansson on 2010-05-12
Thanks, tried that script but it didn't help me out. It showed two bootable files in my usb, which I tried to run when that boot command line thing came up. But it said something like "Could not find kernel." And if I tried just pressing enter without putting anything in me it said "Could not find Linux kernel."

But yes, windows and usb boot seem like a pain! Have done many searches without finding anything about making it bootable on a usb. I do have a cd/dvd drive, but nothing to write it on atm. Guess I'll have to buy one then :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar, totalt 312581808 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,734,664   167,734,602   7 HPFS/NTFS
/dev/sda2         291,604,480   293,701,631     2,097,152   c W95 FAT32 (LBA)
/dev/sda3         293,703,344   312,581,807    18,878,464   7 HPFS/NTFS
/dev/sda4         167,734,789   291,595,814   123,861,026   5 Extended
/dev/sda5         286,455,078   291,595,814     5,140,737  82 Linux swap / Solaris
/dev/sda6         167,734,791   187,269,704    19,534,914  83 Linux
/dev/sda7         187,269,768   191,173,499     3,903,732  83 Linux
/dev/sda8         191,173,563   286,455,014    95,281,452  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8021 MB, 8021606400 byte
255 huvuden, 63 sektorer/spår, 975 cylindrar, totalt 15667200 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,663,374    15,663,312   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0B92DAEF522D1731                       ntfs                                     
/dev/sda2        0A23-B0B6                              vfat       HP_TOOLS                      
/dev/sda3        E056567B56565280                       ntfs       HP_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6f3a2227-b712-4912-9644-033031ed38ef   swap                                     
/dev/sda6        753ccab0-9997-406e-a67f-fffb6399ca4b   ext4                                     
/dev/sda7        3b16e180-3420-4158-9b1f-23c8704bfe7c   ext4                                     
/dev/sda8        0adc4081-9fe1-49d4-a4ff-73b63039af9c   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        87E9-3F34                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /boot                    ext4       (rw)
/dev/sda8        /home                    ext4       (rw)
/dev/sda1        /media/sda1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/sda3              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/87E9-3F34         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=753ccab0-9997-406e-a67f-fffb6399ca4b /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=3b16e180-3420-4158-9b1f-23c8704bfe7c /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=0adc4081-9fe1-49d4-a4ff-73b63039af9c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=6f3a2227-b712-4912-9644-033031ed38ef none            swap    sw              0       0
UUID=0B92DAEF522D1731 /media/sda1 ntfs-3g users 0 0
UUID=E056567B56565280 /media/sda3 ntfs-3g users 0 0

=================== sda6: Location of files loaded by Grub: ===================


  86.1GB: initrd.img
  86.0GB: initrd.img.old
  86.1GB: vmlinuz
  86.0GB: vmlinuz.old

============================= sda7/grub/grub.cfg: =============================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 753ccab0-9997-406e-a67f-fffb6399ca4b
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
set locale_dir=($root)/grub/locale
set lang=sv
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	linux	/vmlinuz-2.6.32-22-generic root=UUID=753ccab0-9997-406e-a67f-fffb6399ca4b ro   quiet splash
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/vmlinuz-2.6.32-22-generic root=UUID=753ccab0-9997-406e-a67f-fffb6399ca4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	linux	/vmlinuz-2.6.32-21-generic root=UUID=753ccab0-9997-406e-a67f-fffb6399ca4b ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=753ccab0-9997-406e-a67f-fffb6399ca4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	linux	/vmlinuz-2.6.31-21-generic root=UUID=753ccab0-9997-406e-a67f-fffb6399ca4b ro   quiet splash
	initrd	/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/vmlinuz-2.6.31-21-generic root=UUID=753ccab0-9997-406e-a67f-fffb6399ca4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 3b16e180-3420-4158-9b1f-23c8704bfe7c
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b92daef522d1731
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set e056567b56565280
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda7: Location of files loaded by Grub: ===================


  96.0GB: grub/core.img
  96.0GB: grub/grub.cfg
  96.0GB: initrd.img-2.6.31-21-generic
  96.0GB: initrd.img-2.6.32-21-generic
  96.1GB: initrd.img-2.6.32-22-generic
  96.0GB: vmlinuz-2.6.31-21-generic
  96.0GB: vmlinuz-2.6.32-21-generic
  96.1GB: vmlinuz-2.6.32-22-generic
```

---

