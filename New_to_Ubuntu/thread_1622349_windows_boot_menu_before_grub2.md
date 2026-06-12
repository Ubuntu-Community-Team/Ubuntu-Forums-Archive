---
title: "windows boot menu before grub2"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by indyeah on 2010-11-15
hi all

i have a dual boot desktop with windows 7 and ubuntu 10.10 installed on a separate partition on my hard drive.

whenever i start my pc i get grub2 menu from where i have option to choose either 10.10 or windows 7 but what i want is that windows 7 boot menu should show first instead of grub2 of 10.10

can some one provide me step by step instructions of how to accomplish this???
thanks

---

### Post by Quackers on 2010-11-15
You can do that with EasyBCD (installed to Windows).

---

### Post by indyeah on 2010-11-15
i did try EasyBCD in windows but maybe i didnt configure it correctly because after reboot it gave me grub2 then windows boot menu with option to choose operating system.

---

### Post by sikander3786 on 2010-11-15
**Quackers** seems away for the moment so I am jumping in ;-)

In order to get rid of Grub, you'll need to restore the Windows MBR from a Windows 7 install or recovery disc.

Boot from Windows 7 disc and perform startup repair 3 times until the Grub menu disappears and you are able to boot Windows with seeing it. Then add EasyBCD and you'll be good to go.

If you are unsure, please post the output of bootinoscript from your Ubuntu or an Ubuntu Live CD as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap the output using proper code tags # from the post menu. [ code] at beginning and [/code] at the end.

---

### Post by Rubi1200 on 2010-11-15
Sorry to jump in like this, but as I understand the post both Windows and Ubuntu are booting normally; correct?

What indyeah wants to do can be found in this fantastic guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The relevant section is #6 which explains how to create a custom menu.

If this is not what you wanted, ignore everything I wrote as this message will self-destruct in 10 seconds :)

---

### Post by indyeah on 2010-11-15
> **Rubi1200 said:**
> Sorry to jump in like this, but as I understand the post both Windows and Ubuntu are booting normally; correct?

What indyeah wants to do can be found in this fantastic guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The relevant section is #6 which explains how to create a custom menu.

If this is not what you wanted, ignore everything I wrote as this message will self-destruct in 10 seconds :)

everything is working fine on my pc.i really don't want custom grub2 just windows boot loader should show first before grub2 whenever i start my pc.

---

### Post by Enigmapond on 2010-11-15
Well...to do what you are looking to do, GRUB will NEED to be customized. If everything is working fine, why would you want to do this anyway??? Grub comes up and choose Windoze. Or make Windoze the default on GRUB...seems like a much easier solution.

---

### Post by indyeah on 2010-11-15
ok sikander this is what i got after running boot script loader


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS
/dev/sda2          39,086,206   156,312,449   117,226,244   f W95 Ext d (LBA)
/dev/sda5          39,086,208    48,885,408     9,799,201   b W95 FAT32
/dev/sda6          78,172,353   117,258,434    39,086,082   7 HPFS/NTFS
/dev/sda7         117,258,498   156,312,449    39,053,952   b W95 FAT32
/dev/sda8          48,885,760    76,847,103    27,961,344  83 Linux
/dev/sda9          76,849,152    78,172,159     1,323,008  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4818219D18218B50                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8044-2367                              vfat                                     
/dev/sda6        8E7EF3FB7EF3D9C3                       ntfs       VIP3                          
/dev/sda7        740E-0343                              vfat       VIP4                          
/dev/sda8        b0b5b1fe-d0ec-4881-8fed-655d90cf508b   ext4                                     
/dev/sda9        5d48a19f-977a-4852-8835-571f71fe1fe7   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=b0b5b1fe-d0ec-4881-8fed-655d90cf508b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=b0b5b1fe-d0ec-4881-8fed-655d90cf508b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=b0b5b1fe-d0ec-4881-8fed-655d90cf508b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=b0b5b1fe-d0ec-4881-8fed-655d90cf508b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b0b5b1fe-d0ec-4881-8fed-655d90cf508b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4818219d18218b50
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=b0b5b1fe-d0ec-4881-8fed-655d90cf508b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=5d48a19f-977a-4852-8835-571f71fe1fe7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  35.9GB: boot/grub/core.img
  32.0GB: boot/grub/grub.cfg
  32.1GB: boot/initrd.img-2.6.35-22-generic-pae
  27.0GB: boot/initrd.img-2.6.35-23-generic-pae
  35.9GB: boot/vmlinuz-2.6.35-22-generic-pae
  35.9GB: boot/vmlinuz-2.6.35-23-generic-pae
  27.0GB: initrd.img
  32.1GB: initrd.img.old
  35.9GB: vmlinuz
  35.9GB: vmlinuz.old
```

---

### Post by indyeah on 2010-11-15
> **Enigmapond said:**
> Well...to do what you are looking to do, GRUB will NEED to be customized. If everything is working fine, why would you want to do this anyway??? Grub comes up and choose Windoze. Or make Windoze the default on GRUB...seems like a much easier solution.

i know i know i can choose windows from grub2 but my grub2 is pretty messy with lots of options.

i want a clean boot loader at the start so i can choose windows 7 or linux then go to grub2 whenever i choose to run linux.its as simple as that.

---

### Post by Rubi1200 on 2010-11-15
When you installed Ubuntu and its bootloader, GRUB, the Windows bootloader was written over in the MBR:
> Grub 2 is installed in the MBR of /dev/sda
What this means, practically speaking, is that in your current situation, GRUB controls booting for both operating systems.

If you read the information in the link I posted, you will see that there are ways to clean up the GRUB menu.

You might also find this link useful:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by indyeah on 2010-11-15
> **Rubi1200 said:**
> When you installed Ubuntu and its bootloader, GRUB, the Windows bootloader was written over in the MBR:

What this means, practically speaking, is that in your current situation, GRUB controls booting for both operating systems.

If you read the information in the link I posted, you will see that there are ways to clean up the GRUB menu.

You might also find this link useful:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)


yeah reading this forum for past hour or so i got the picture about ubuntu installation overwriting my windows boot loader.

anyway thanks fr all the help guys.

let me try cleaning my GRUB menu or EasyBCD again and post the results here

---

### Post by stoogiebuncho on 2010-11-15
If you're thinking about changing your bootloader anyway, you might look at BURG [http://www.omgubuntu.co.uk/tag/burg/]("http://www.omgubuntu.co.uk/tag/burg/").  There's some pretty striking themes available.

---

### Post by Mark Phelps on 2010-11-15
When you replace your MBR, it will then boot automatically into Win7.  At that point, you can NOT use GRUB anymore. 

What you will have to do is install EasyBCD.  It, in turn, will install GRUB4DOS into an NTFS partition -- and THAT can be used to then launch Ubuntu.

These are the Ubuntu forums -- where you can get LOTS of help on using the different forms of GRUB.  But, to get detailed help on using EasyBCD, you would do better going to the NeoSmart Technology forums.  They have forums and tutorials readily available to help you in doing exactly what you want to do.

And, just so you know ... you have a lot of work ahead of you to get this working the way you want.  An easier solution (since you are able to boot OK at present) is to just change the default in the GRUB boot sequence to select Win7.  That only requires one change to one line in the default boot config file. You don't have to uninstall or install anything.

---

### Post by indyeah on 2010-11-16
> **Mark Phelps said:**
> When you replace your MBR, it will then boot automatically into Win7.  At that point, you can NOT use GRUB anymore. 

What you will have to do is install EasyBCD.  It, in turn, will install GRUB4DOS into an NTFS partition -- and THAT can be used to then launch Ubuntu.

These are the Ubuntu forums -- where you can get LOTS of help on using the different forms of GRUB.  But, to get detailed help on using EasyBCD, you would do better going to the NeoSmart Technology forums.  They have forums and tutorials readily available to help you in doing exactly what you want to do.

And, just so you know ... you have a lot of work ahead of you to get this working the way you want.  An easier solution (since you are able to boot OK at present) is to just change the default in the GRUB boot sequence to select Win7.  That only requires one change to one line in the default boot config file. You don't have to uninstall or install anything.


well at this moment i have decided not to experiment way too much with boot menu and let things be maybe in future oh well...anyways i did try EasyBCD,tweaked some settings over there and got the windows boot menu like the way i wanted though i admit i didnt change my boot up screen,i still get GRUB2 at restart...coz well GRUB2 has overwritten my windows MBR.

thanks for all ur help guys

---

### Post by indyeah on 2010-11-17
ok here is a quick question can someone tell me step by step instructions about how to get back my windows MBR which was overwritten by GRUB2 and after that how to reinstall GRUB2 in same partition as my ubuntu installation???

thanks

---

### Post by drs305 on 2010-11-17
> **indyeah said:**
> ok here is a quick question can someone tell me step by step instructions about how to get back my windows MBR which was overwritten by GRUB2 and after that how to reinstall GRUB2 in same partition as my ubuntu installation???

If your Windows boot files are still intact, you can do both these things from a LiveCD (or Ubuntu boot):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo grub-install --force /dev/sda8
```

The first command installs lilo, a bootloader. Disregard it's notes about fully installing it. The second command will write to the sda MBR, which should pass control to the Windows bootloader.

The third will install grub on the sda8 partition. 

That set of commands will do what you ask. However, you are going to get the Windows bootloader and will have to figure out how to get to the Grub bootloader on sda8. I'm not a Windows guy - perhaps adding an entry to boot.ini or back to installing EasyBCD. Someone with expertise will have to tell you how to accomplish getting to the Ubuntu grub menu. 

I would wait for an answer to this last part before executing the commands.

---

### Post by drs305 on 2010-11-17
I don't know if you have already read my previous post, so here is an update.

After completing the steps I outlined above, I found a link that explains how to add Grub2 to a Windows boot.ini file.

The basics are:
[LIST=1]
[*]Download bootpart.zip from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) 
[*]Extract the content to a created folder C:\bootpart
[*]Run "bootpart" to find the linux partition: bootpart
[*]Run the bootpart command with the partition number and title: 
bootpart X C:\BOOTLINX.BIN Ubuntu
with X being the Linux partition. Note *bootpart* still counts partitions from 0
[/LIST]

Here is the link with the details:
[http://forums.fedoraforum.org/showthread.php?t=145212]("http://forums.fedoraforum.org/showthread.php?t=145212")

It worked very well for me on XP. Please let us know how it works for you.

(Now I'm restoring Grub2...)  ;-)

---

### Post by indyeah on 2010-11-17
> **drs305 said:**
> If your Windows boot files are still intact, you can do both these things from a LiveCD (or Ubuntu boot):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo grub-install --force /dev/sda8
```

The first command installs lilo, a bootloader. Disregard it's notes about fully installing it. The second command will write to the sda MBR, which should pass control to the Windows bootloader.

The third will install grub on the sda8 partition. 

That set of commands will do what you ask. However, you are going to get the Windows bootloader and will have to figure out how to get to the Grub bootloader on sda8. I'm not a Windows guy - perhaps adding an entry to boot.ini or back to installing EasyBCD. Someone with expertise will have to tell you how to accomplish getting to the Ubuntu grub menu. 

I would wait for an answer to this last part before executing the commands.


before i embark on this wonderful journey :P i have just two questions:

1.If i understand it correctly restoring windows bootloader i will no longer be able to boot into my ubuntu unless and untill i restore GRUB2 into sda8???

2.Can i safetly use EASYBCD to add ubuntu option in my windows boot menu as i would have already restored GRUB2 to my sda8 using the first method???

---

### Post by drs305 on 2010-11-17
> **indyeah said:**
> before i embark on this wonderful journey :P i have just two questions:

1.If i understand it correctly restoring windows bootloader i will no longer be able to boot into my ubuntu unless and untill i restore GRUB2 into sda8???
In the way I described it, yes. Simplified, you can have the MBR point to either Windows (Windows bootloader or lilo) or Ubuntu (Grub).

Since you wanted a Windows bootloader, I suggested lilo (or you can restore the real Windows bootloader via the Windows CDs). This will remove Grub from the MBR. Without Grub in the MBR, the only other way to invoke it is to put it on the Ubuntu partition. 

Grub does not prefer this, as the location of certain Grub files are recorded and unchangeable. If the files move, Grub will break. Normally this is not a problem unless you are repartitioning, resizing, etc. If it does break, you would boot to the LiveCD and reinstall G2 to the partition.

> 
2.Can i safetly use EASYBCD to add ubuntu option in my windows boot menu as i would have already restored GRUB2 to my sda8 using the first method???
I don't know about EASYBCD. I know people use it and I think when it is used Grub is not on the MBR, but you will have to find out from EasyBCD users.

The lilo option I described works for presenting the Windows menu with an option to boot into the grub menu defined by the partition's grub.cfg file. For this to work, Grub must be installed on the partition since Windows/lilo already 'owns' the MBR.

---

### Post by indyeah on 2010-11-17
@drs305

thanks for the useful info,ummm let me try these methods and get back to you.

---

### Post by indyeah on 2010-11-17
> **drs305 said:**
> If your Windows boot files are still intact, you can do both these things from a LiveCD (or Ubuntu boot):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo grub-install --force /dev/sda8
```

The first command installs lilo, a bootloader. Disregard it's notes about fully installing it. The second command will write to the sda MBR, which should pass control to the Windows bootloader.

The third will install grub on the sda8 partition. 

That set of commands will do what you ask. However, you are going to get the Windows bootloader and will have to figure out how to get to the Grub bootloader on sda8. I'm not a Windows guy - perhaps adding an entry to boot.ini or back to installing EasyBCD. Someone with expertise will have to tell you how to accomplish getting to the Ubuntu grub menu. 

I would wait for an answer to this last part before executing the commands.

wow this worked and i got exactly what i wanted.

thank a lot man

---

