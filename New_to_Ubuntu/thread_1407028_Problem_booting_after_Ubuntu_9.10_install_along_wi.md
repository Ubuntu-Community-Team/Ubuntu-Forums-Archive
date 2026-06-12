---
title: "Problem booting after Ubuntu 9.10 install along with Windows 7"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by linuxnovice on 2010-02-14
Hi,

I recently purchased this computer:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5602487&sku=G180-0122&cm_re=Homepage-_-Spot%2011-_-CatId_6_G180-0122]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5602487&sku=G180-0122&cm_re=Homepage-_-Spot%2011-_-CatId_6_G180-0122")

I have a Windows 7 Professional DVD that I got from my school. I planned to dual boot Windows 7 and Ubuntu 9.10. Since I was going with a fresh installation, I followed this guide:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

to set up my operating systems. However, after I have installed Ubuntu, I get this error:

> 
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key


I have set up my computer as follows:
300GB - Windows 7
400GB - Common data 
300GB - Ubuntu 9.10
      / - 100GB
      /home - 198GB
      swap - 2GB

Both the operating systems are the x86_64 versions.

I searched online, but couldn't find a viable solution. Right now I am not able to boot into either OS's. Any help is appreciated.

Thanks.

---

### Post by linuxnovice on 2010-02-14
I dont usually bump my own thread. But this is kind of an emergency and I could really use some help.

Thanks, won't bump it again.

---

### Post by meierfra. on 2010-02-14
We need more information. Follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to download the boot info script and post the RESULTS.txt

---

### Post by gordintoronto on 2010-02-14
When I installed Windows 7 and Ubuntu on a brand-new system (blank hard drive), I installed Windows 7 first, then Ubuntu.  The lifehacker instructions make things more complicated than they need to be.  From Ubuntu, I have full access to the Windows 7 partition.

---

### Post by linuxnovice on 2010-02-14
> **meierfra. said:**
> We need more information. Follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to download the boot info script and post the RESULTS.txt

Thank you friend.

Here are the results:

```

                    Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x509c93ac

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   614,405,924   614,405,862   5 Extended
/dev/sda5                 126   195,318,269   195,318,144  83 Linux
/dev/sda6         195,318,333   610,502,129   415,183,797  83 Linux
/dev/sda7         610,502,193   614,405,924     3,903,732  82 Linux swap / Solaris
/dev/sda2    *    614,405,925 1,228,811,849   614,405,925   7 HPFS/NTFS
/dev/sda3       1,228,811,850 1,953,520,064   724,708,215   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16131293184 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,503,464    31,503,402   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        7A2DF1C81A72DAE7                       ntfs       Windows                       
/dev/sda3        563A61610446B1C9                       ntfs       Data                          
/dev/sda5        1bcba10f-5890-4939-9528-ef7f58aee4c4   ext4                                     
/dev/sda6        1d306932-459b-4ca3-8558-409a8ff68084   ext4                                     
/dev/sda7        8a1b6c5a-d98b-4ab5-b8a3-b4d30de05204   swap                                     
/dev/sdb1        FE1A-2EEB                              vfat       USBDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 1bcba10f-5890-4939-9528-ef7f58aee4c4
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
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcba10f-5890-4939-9528-ef7f58aee4c4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1bcba10f-5890-4939-9528-ef7f58aee4c4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1bcba10f-5890-4939-9528-ef7f58aee4c4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1bcba10f-5890-4939-9528-ef7f58aee4c4 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 7a2df1c81a72dae7
	chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1bcba10f-5890-4939-9528-ef7f58aee4c4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=1d306932-459b-4ca3-8558-409a8ff68084 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=8a1b6c5a-d98b-4ab5-b8a3-b4d30de05204 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   3.6GB: boot/grub/core.img
   3.5GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.31-14-generic
    .4GB: boot/vmlinuz-2.6.31-14-generic
    .4GB: initrd.img
    .4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 

```

FYI sbd1 refers to my Ubuntu USB liveCD. 

Thanks.

---

### Post by fwin on 2010-02-14
Hi linuxnovice,

I am not a linux expert, but i have successfully installed ubuntu and windows 7 in one hard drive.

- I recommend you to first install windows but dont forget to leave some free space for ubuntu (i.e. make a partition for windows dont make a full installation).

-Then insert the ubuntu 9.10 cd (or flash disk) and boot the computer from there, once you are on the ubutnu desktop there will be an icon called "install" or something like that. Double click this icon and just follow the instructions, you will get to a point where the installer will ask you (if i remember correctly) if you want to install ubuntu in the whole hard drive or if you just would like to install it next to windows, Dont choose any of these options, there is an extra button there called "advanced" (i think), click on that and it will take you to a window where you can make partitions, there you choose the amount of disk space that you want for ubuntu and for "common data" . If the "comon data" partition needs to be accessible from windows and ubuntu, dont forget to make this partition NTFS otherwise windows wont be able to access it.  

- Also i recomend you to install ubuntu from usb flash disk, since it is faster than a cd installation. It took me about 15min to install ubuntu from a flash disk.


I hope this helps, good luck

---

### Post by mechro on 2010-02-14
> Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

Is your BIOS set to boot from CD or USB drive? Perhaps it needs changing to boot from the main Hard Drive?

---

### Post by linuxnovice on 2010-02-14
> **mechro said:**
> Is your BIOS set to boot from CD or USB drive? Perhaps it needs changing to boot from the main Hard Drive?

You were right. I'm sorry I wasted all of your time. But all the computers I've worked have a boot order and I thought that would be followed here as well. If it didn't find a USB disk, it would normally boot from the next device on the boot list. However, it didn't and I had to manually change the boot order.

Thanks for all your help, everything seems to be find now.

---

### Post by mathfreak123 on 2010-02-14
I'm not an expert either, but what is the "/dev/sdb1" partition? It sounds like some kind of USB drive plugged in during bootup to me, so have you tried removing it?

EDIT: situation solved. Ignore this post.

---

