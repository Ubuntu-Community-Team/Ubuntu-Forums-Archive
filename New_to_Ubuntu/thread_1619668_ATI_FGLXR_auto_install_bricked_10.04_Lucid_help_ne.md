---
title: "ATI FGLXR auto install bricked 10.04 Lucid help needed"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by sprintexec on 2010-11-12
Hi 

I now know that what I did was wrong, trouble is I was wooed into pressing the 'install restricted drivers' tab without checking! Checking around after the fact I learned of the problems that there have been and (in my case) still are re ATI Mobility Radeon HD4330 driver upgrades. The worst of it is that at least one user says that the standard driver is at least as good as the one which has now temporarily? trashed my install!

I cannot boot my dual install 10.04 / win 7 Acer 4810TZ to run under Ubuntu. When I boot it it starts to install then the screen shows a shower of green before going black and unresponsive. I can get a basic grub window but don't know what to do with it when I have it! I can also boot from a cd and using this route I have been able to follow advice I read online to download and run a boot info script and now have a boot info summary. (I've added it below as it may be helpful in unpicking the mess I created?) 

Before I go any further and waste yet more time, I'm appealing for help to get back to work. 

Thanks in advance, AJ 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   625,140,399   600,357,552   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1019 MB, 1019215872 bytes
32 heads, 63 sectors/track, 987 cylinders, total 1990656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 249     1,989,791     1,989,543   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1f62b89d-516c-4896-a064-203e68b6f9fc   ext4                                     
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        921C18621C18441F                       ntfs       SYSTEM RESERVED               
/dev/sda3        7892D84192D80612                       ntfs       ACER                          
/dev/sda: PTTYPE="dos" 
/dev/sdc1                                               vfat       VIVICAM5199                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/VIVICAM5199       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set daa41c49a41c2b11
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 921c18621c18441f
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 7892d84192d80612
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   2.4GB: boot/grub/grub.cfg
   6.7GB: boot/initrd.img-2.6.32-21-generic
   1.2GB: boot/initrd.img-2.6.32-22-generic
   6.9GB: boot/initrd.img-2.6.32-23-generic
  17.5GB: boot/initrd.img-2.6.32-24-generic
   5.7GB: boot/initrd.img-2.6.32-25-generic
   6.7GB: boot/vmlinuz-2.6.32-21-generic
   6.7GB: boot/vmlinuz-2.6.32-22-generic
   1.4GB: boot/vmlinuz-2.6.32-23-generic
  17.1GB: boot/vmlinuz-2.6.32-24-generic
  17.2GB: boot/vmlinuz-2.6.32-25-generic
   5.7GB: initrd.img
  17.5GB: initrd.img.old
  17.2GB: vmlinuz
  17.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by sully101 on 2010-11-21
It sounds like X is not loading. have a read here for the grub command line option to get you into vesa mode (failsafe) [https://wiki.ubuntu.com/BulletProofX]("https://wiki.ubuntu.com/BulletProofX") [COLOR="Navy"]**xforcevesa**[/COLOR]

You will then need to remove the offending module and reconfigure X to load the one you want. You cand find some information on that here [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")

I hope this helps.

---

### Post by sprintexec on 2010-11-25
Thank you for your suggestions which I shall investigate, action and report back on tomorrow. AJ

---

### Post by sprintexec on 2010-12-13
I'm afraid the pages of info on bulletproofX proved to be of limited use as I could not get the grub> to accept any command that I could contrive from that which I read. I'm now stuck as before. ANyone have any ideas please? Thanks AJ

---

### Post by sully101 on 2010-12-13
I re-read your posts and have done some googling. I would suggest that at the 4810TZ could actually have an intel graphics chip [http://reviews.cnet.com/laptops/acer-aspire-timeline-4810tz/4507-3121_7-33698047.html?tag=specs]("http://reviews.cnet.com/laptops/acer-aspire-timeline-4810tz/4507-3121_7-33698047.html?tag=specs"). So I am unsure of your symptoms.
Does your ubuntu install boot to or past grub? (if so do you see any messages on the screen?) Can you boot Win 7?

The easy fix which used to work years ago was to select rescue mode from the grub boot screen. (press the shift key after the bios screen as your computer boots you will then get several options , use the arrow keys an enter to select)

FailsafeX - should get you to a gui from which you can uninstall the offending modules

rootnet - should get you to a command prompt, You should then end up with a terminal screen thats gives a prompt "root#", from that you can type the commands on [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

and to reboot.

shutdown -r now


If you boot from a live ubuntu cd can you mount the  linux partition on your hard drive? If you can you could rename the /etc/X11/xorg.conf file to some thing like /etc/X11/xorg.conf.bak1 and then shutdown and remove the cd. Xorg should try to load some sane defaults when ubuntu starts up again. Could you post the xorg.conf file from your hard drive, It may shed some light on the problem.

The output of the following command in a terminal will show what display chipset you have.

sudo lspci | grep VGA

---

### Post by sprintexec on 2010-12-15
So after some searching I found the | character! (Slow learner at the helm!) this produced the below result which ties in with the information I was given 'ATI Radeon HD 4330 graphics of 512MB. 

ubuntu@ubuntu:~$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
ubuntu@ubuntu:~$ 

I can boot win 7 and ubuntu. However when I boot ubuntu the display flashes and goes black. The hard drive is working away but the ubuntu log in does not appear. If I force the computer to close down I see the ubuntu logo with the series of red dots below. I can trap the boot sequence and get to 'a minmal bash like line editing' screen which displays grub> 
This screen is, given my limited knowledge, next to useless as I cannot get it to accept any command that I might want it to follow. 

When I boot from the live CD I cannot see any of my files that must be somewhere on the hard drive. I would like to be able to get to these files whilst I continue to try to regain control of ubuntu on this m/c. Once again thanks for your assistance and patience. AJ

---

### Post by sprintexec on 2010-12-16
bump - why can I not see my files when I boot from the live cd? original problem still persists, can you help? thanks aj

---

### Post by sprintexec on 2010-12-31
Kudos and thanks to Sully101 whose help was invaluable in my keeping going to solve this problem (of my own making). The solution was, when I got to it, simple. I noticed from someone else post that interrupting the boot and deleting 'quiet splash' and inserting 'nomodeset' into the code was an option I had not yet tried. This proved to be the solution to recovering my display after the ATI driver hang up that had robbed me of my installation for the last six weeks. :guitar: Hurrah - just in time for New Year. AJ

---

### Post by avrpunk on 2010-12-31
A kernel update killed my ATI driver  install.  The machine would freeze when the graphics mode changed at  boot.  

**The shift key to show the Grub menu did not work!!!  **

Being unable to stop Ubuntu before it tried to change video modes and freeze the machine, SSH wouldn't work either.

Removing the video card and clearing the BIOS to use the built-in Intel  video did not result in text or graphics display, but the system did  work and using SSH to install the ATI driver was the solution.

Hope this helps someone.

---

