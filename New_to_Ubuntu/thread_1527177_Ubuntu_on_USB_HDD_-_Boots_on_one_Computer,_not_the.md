---
title: "Ubuntu on USB HDD - Boots on one Computer, not the other"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by NTL2009 on 2010-07-09
I wanted an install of Ubuntu that I could 'play' with, w/o risking my main machine. So I bought a portable USB HDD, 500GB and set the 4th as an extended partition, and installed 10.04 Lucid in 3 logical partitions (/, /home, swap).

I want to be able to plug this into either my EM725 laptop, or my ASUS PC901 and boot into it. At this point, I can boot into it from my EM725, but not my PC901. I've been trying to read/understand this GRUB 2 stuff, and I'm way confused - it seems to me if it can boot from the EM725, GRUB on the USB HDD must be OK, so why can't the PC901 boot it (it does let me select it after I hit 'esc' on booting)?

Now, some gory details - On the first install attempt, I made the mistake of not choosing the "Advanced" tab to put the bootloader on the external, so I ended up with the problem where it appeared to work fine, but if I unplugged the USB HDD, I could not boot my EM725 (horrors!).

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996)

More background: When I initially set up the EM725 laptop, I shrunk the Win7 partition, created a 4th extended partition,  and installed 10.04 Lucid in 3 logical partitions (/, /home, swap). I can hit F12 at boot, and choose W7 or Ubuntu - all is (was) good. 

After this install messing up the internal GRUB or MBR of the EM725, I *finally* got it booting from the internal OK - but I went through so many different steps from 50 different threads that I don't know exactly what steps fixed it, but I think it was a combo of using a tool to reinstall the Win7 loader (After which I could only boot Windows) and *then* running some grub update/install commands.

Next, I reinstalled UBUNTU a couple of times on the USB HDD, this time using my PC901, and choosing the Advanced tab (once choosing sdc, once choosing sdc5 - I couldn't tell which is 'correct') - but it would not boot either way on the PC901. I took it to the EM725 to troubleshoot, and was surprised to find that it would boot there! 

I should be able to boot on different machines, right? What could make it work on one and not the other? I have one theory that it is actually chaining back to the EM725, so when it tries that on the PC901, it fails to find what it needs? But how do I determine this and/or just fix this? I'm obviously a bit gun shy of making changes to my EM725 as it is my main machine and working now. The PC901 I'm more comfortable playing with for now.

Whew - sorry for the length of that, but I thought the background would be relevant.

TIA for any help -NTL2009

---

### Post by john newbuntu on 2010-07-09
Thanks for the detailed explanation.  I would suggest you to check the BIOS and see what the first boot device is on the PC901.  Go in to your BIOS on bootup (usually by pressing one of the keys like F2 or del or esc - don't know for sure).  The link below will help you with the navigation.  You should find a "Boot" menu.  Select the boot device priority and set the first one to be your external HDD/removable drive.  Save your changes.  Reboot and see if that helps.  Since you mentioned installing grub on sdc's MBR, that should help.
[http://www.neoseeker.com/Articles/Hardware/Reviews/asus_eeepc_901/4.html](http://www.neoseeker.com/Articles/Hardware/Reviews/asus_eeepc_901/4.html)

I have a feeling that your EM725 is set up the same way in BIOS.

If it does not help, download and run the boot info script courtesy of our forum member meierfra at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) . Post the output using code tags.  You can run it on PC901 with the external attached.

---

### Post by bwallum on 2010-07-09
> **NTL2009 said:**
>  What could make it work on one and not the other? ...

Grub uses the hd0,1 form of reference when it boots, 0 is the first harddrive specified in your cmos. 1 is the fiirst partition on that drive.

When you first install to an external hard drive you will do it from a running machine. That machine has already worked out the harddrive references and your external drive will be hd1 if you have an existing internal hard drive or hd2 if you have two existing internal harddrives etc.

So when grub installs on your external drive it will contain a command in the /boot/grub/grub.cfg file that says something like set root='(hd1,1)' -assuming you set it up on a machine with one internal harddrive - whereas if you have told you cmos to boot your external drive first, then it thinks that your external drive is hd0 so looks for the boot files in hd0,1. When it can't find them it throws an error such as error: no such device...

What you need to do is first work out if the machine you are wanting to boot has a bios that allows you to set a usb drive as primary or has a boot menu (before grub's) that enables you to choose the usb drive to bott from. If so then you need to set root='(hd0,1) on the grub.cfg file on your usb external harddrive.

Note that when grub picks up run command from cmos it translates the drive reference. Typically cmos calls the first hardrive hd0, the Ununtu os calls it sda.

You can tell how your harddrives are referenced by the os by using the command ```
sudo blkid
```Now you will probably say how do I set root='(hd0,1)' on my external drive grub.cfg file? Well DON'T try a direct edit of the grub.cfg file. I'm currently in the same boat and hopefully will find the resolution here! Thanks for posting.

---

### Post by NTL2009 on 2010-07-09
Thanks for the replies. Hopefully this leads to a fix/process that will help others also.

**john newbuntu,** I hit F2 to edit the BIOS boot prefs, I noticed two different entries - BOOT DEVICE PRIORITY and HARD DISK DRIVES. I set both of these to select my Hitachi USB HDD first. IIRC, these were more generic, like 'removable drive' before? 

This appears to send it to the USB HDD as expected, and I get:

error: NO SUCH PARTITION and am dropped to the grub rescue prompt.

On reboot, I can choose my internal SSD and it boots to my internal OK. I ran the script with the USB HDD attached. For ref, this is the PC901 with the 4GB SSD and separate 20GB SSD (no int HDD). I have UBUNTU 10.04 lucid root installed on the 4GB, /home and swap on the 20GB. One more detail - this PC901 originally had Xandros on it,  and when I installed 9.04 on it, I was afraid to touch the two~8MB areas of the SDD that appeared to the BIOS and another that comes up "unrecognized" now, I think that was some kind of quick boot thing, but I left it as is. I do have quick boot disabled now.  I'll include the printout below, two things I noticed from the script output:

First:> 1) sdc5: 
    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc5 and looks at sector 857935759 of the same hard drive for core.img, but core.img can not be found at this location.But I don't know the significance of this, and why it would boot on my EM725 w/o this 'core.img'. 

Second:  **bwallum**, I don't quite grasp all you said, but it did trigger something that has me wondering (or maybe I'm totally off-base - I _am_ an absolute beginner when it comes to booting). MY PC901 has this sda and sdb SDD, while my EM725 has a single HDD. Somewhere along the line, I thought I saw references to drive numbers that did not make sense to me - could it be that installing on the PC901 has created an offset in the drive numbering (and I somehow 'fixed' that somewhere along the way on the EM725)?

If that is the case, it seems odd - that seems to mean you could only move a portable drive between computers with similar drive layouts, or is this why people get in and mod the files/scripts for GRUB? But then, both machines 'see' my USB LIVE 'thumb/flash/stick' (whatever people call them) drive OK?

Oh, one more thing - I noticed my PC901 has GRUB 1.97~beta4, my EM725 is 1.98. Significant? If so, how do I upgrade?

Again, thanks so much for the help - NTL2009 (NTL = New to Linux in 2009 ;) )

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 7839720. According to the info 
                       in the boot sector, sda3 has 0 sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

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

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc5 and 
                       looks at sector 857935759 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb38fb38

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,839,719     7,839,657  83 Linux
/dev/sda3           7,839,720     7,855,784        16,065   c W95 FAT32 (LBA)
/dev/sda4           7,855,785     7,871,849        16,065  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf26d47c4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     5,237,189     5,237,127  82 Linux swap / Solaris
/dev/sdb2           5,237,251    31,519,529    26,282,279   5 Extended
/dev/sdb5           5,237,253    31,519,529    26,282,277  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c2661

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   319,484,654   319,484,592  83 Linux
/dev/sdc2         319,484,655   565,247,024   245,762,370  83 Linux
/dev/sdc3         565,247,025   790,526,519   225,279,495  83 Linux
/dev/sdc4         790,526,581   976,768,064   186,241,484   5 Extended
/dev/sdc5         790,526,583   872,441,954    81,915,372  83 Linux
/dev/sdc6         872,442,018   966,534,659    94,092,642  83 Linux
/dev/sdc7         966,534,723   976,768,064    10,233,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b7dba7cd-c524-48bb-85da-6b6890dca4de   ext4                                     
/dev/sda3        4861-2962                              vfat       BIOS                          
/dev/sdb1        af84f1e2-1b17-42ff-944c-ec9fd446cc1f   swap                                     
/dev/sdb5        30459d15-89bb-45b4-b467-b3de120c3f12   ext4                                     
/dev/sdc1        01e3a024-4cdc-4827-8773-db245370f48a   ext4       H_156GB_A                     
/dev/sdc2        c0f9f80c-b72f-4488-a3cf-baaf721ae856   ext4       H_120GB_B                     
/dev/sdc3        850a957c-fcc5-4fac-9ad5-69e328d542db   ext4       H_110GB_C                     
/dev/sdc5        f89ccde6-66d8-4d15-b0aa-b01973c24195   ext4       /                             
/dev/sdc6        9453f426-275d-4ce8-a17d-6df2ae1ecb81   ext4       home                          
/dev/sdc7        679d2138-170e-4be1-849b-0ae958217955   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)
/dev/sdc5        /media/_                 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc3        /media/H_110GB_C         ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc6        /media/home              ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc2        /media/H_120GB_B         ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc1        /media/H_156GB_A         ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc5)" {
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f89ccde6-66d8-4d15-b0aa-b01973c24195 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc5)" {
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f89ccde6-66d8-4d15-b0aa-b01973c24195 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# 13JAN2010 UPDATE UUID for /HOME and swap after repart my 16GB SSD
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
# ORIGINAL /HOME UUID - UUID=01eb1df3-3389-4f61-85c1-3e721ba27d4b /home           ext4    defaults        0       2
# Next line is 13JAN2010 /HOME UUID after a repartition of my 16GB SSD 
UUID=30459d15-89bb-45b4-b467-b3de120c3f12 /home           ext4    defaults        0       2

# swap was on /dev/sdb1 during installation
# 11JAN2010 swap - UUID=8df20010-93b3-47ed-801b-6c1f2a4952fe none            swap    sw              0       0
# Next line is 13JAN2010 swap UUID after a repartition of my 16GB SSD 
UUID=af84f1e2-1b17-42ff-944c-ec9fd446cc1f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   3.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   3.2GB: boot/initrd.img-2.6.31-17-generic
   3.9GB: boot/initrd.img-2.6.31-20-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   2.8GB: boot/vmlinuz-2.6.31-17-generic
   3.6GB: boot/vmlinuz-2.6.31-20-generic
   3.9GB: initrd.img
   3.2GB: initrd.img.old
   3.6GB: vmlinuz
   2.8GB: vmlinuz.old

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd3,5)'
search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
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
set root='(hd3,5)'
search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f89ccde6-66d8-4d15-b0aa-b01973c24195 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f89ccde6-66d8-4d15-b0aa-b01973c24195 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set f89ccde6-66d8-4d15-b0aa-b01973c24195
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b7dba7cd-c524-48bb-85da-6b6890dca4de
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b7dba7cd-c524-48bb-85da-6b6890dca4de ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=f89ccde6-66d8-4d15-b0aa-b01973c24195 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd6 during installation
UUID=9453f426-275d-4ce8-a17d-6df2ae1ecb81 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=af84f1e2-1b17-42ff-944c-ec9fd446cc1f none            swap    sw              0       0
# swap was on /dev/sdd7 during installation
UUID=679d2138-170e-4be1-849b-0ae958217955 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


 439.2GB: boot/grub/core.img
 424.8GB: boot/grub/grub.cfg
 439.2GB: boot/initrd.img-2.6.32-21-generic
 439.2GB: boot/vmlinuz-2.6.32-21-generic
 439.2GB: initrd.img
 439.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000010  00 00 00 00 0c 00 00 00  00 00 5f 5f 00 00 00 80  |..........__....|
00000020  75 01 00 00 05 00 50 37  30 31 00 00 52 4f 4f 54  |u.....P701..ROOT|
00000030  5c 63 69 6d 76 32 5c 6d  73 5f 34 30 39 00 1d 00  |\cimv2\ms_409...|
00000040  00 00 00 ff ff ff ff 00  00 00 00 04 00 00 00 04  |................|
00000050  00 00 00 00 00 00 00 00  00 00 80 0c 00 00 00 00  |................|
00000060  00 00 00 00 00 00 80 26  01 00 00 00 00 00 00 00  |.......&........|
00000070  05 00 00 00 04 00 00 00  0f 00 00 00 0e 00 00 00  |................|
00000080  00 0b 00 00 00 ff ff 01  00 00 00 2a 00 00 00 6b  |...........*...k|
00000090  00 00 00 19 ff ff ff ff  95 00 00 80 00 5f 5f 50  |.............__P|
000000a0  41 52 41 4d 45 54 45 52  53 00 00 61 62 73 74 72  |ARAMETERS..abstr|
000000b0  61 63 74 00 13 00 00 00  00 00 00 00 00 00 00 00  |act.............|
000000c0  00 00 04 00 00 00 00 52  65 74 75 72 6e 56 61 6c  |.......ReturnVal|
000000d0  75 65 00 00 75 69 6e 74  33 32 00 13 00 00 00 00  |ue..uint32......|
000000e0  00 00 00 00 00 00 00 00  00 11 00 00 00 0a 00 00  |................|
000000f0  80 03 08 00 00 00 5e 00  00 00 00 75 69 6e 74 33  |......^....uint3|
00000100  32 00 00 6f 75 74 00 13  00 00 00 00 00 00 00 00  |2..out..........|
00000110  00 00 00 00 00 1c 00 00  00 0a 00 00 80 03 08 00  |................|
00000120  00 00 5e 00 00 00 66 00  00 00 00 0b 00 00 00 ff  |..^...f.........|
00000130  ff 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 0c 00 00  |................|
00000190  00 00 00 5f 5f 00 00 00  80 1d 00 00 00 57 00 69  |...__........W.i|
000001a0  00 6e 00 33 00 32 00 5f  00 53 00 65 00 63 00 75  |.n.3.2._.S.e.c.u|
000001b0  00 72 00 69 00 74 00 79  00 53 00 65 00 74 00 74  |.r.i.t.y.S.e.t.t|
000001c0  00 69 00 6e 00 67 00 4f  00 66 00 4f 00 62 00 6a  |.i.n.g.O.f.O.b.j|
000001d0  00 65 00 63 00 74 00 5a  02 b0 9c ef f5 c7 01 e9  |.e.c.t.Z........|
000001e0  01 00 00 00 00 00 00 00  09 00 00 00 27 00 00 00  |............'...|
000001f0  00 57 69 6e 33 32 5f 53  65 63 75 72 69 74 79 53  |.Win32_SecurityS|
00000200
```

---

### Post by C.S.Cameron on 2010-07-09
Grub2 seems to have complicated booting a full install to USB a bit.
I don't think you can go wrong by disabling the internal HDD of the machine you are using to install to USB.

---

### Post by NTL2009 on 2010-07-09
> **C.S.Cameron said:**
> Grub2 seems to have complicated booting a full install to USB a bit.
I don't think you can go wrong by disabling the internal HDD of the machine you are using to install to USB.

I have come across that suggestion in other threads & tutorials, and it makes sense knowing what I think I know now (I'm not sure of anything, my head is spinning!). But if that means physically disabling (unplugging), then I don't think I can even do that on my PC901 (4GB SSD soldered in?) - I have not looked at my EM725 yet, some laptops are pretty simple to pull the HDD out of, some are a nightmare. I would hope there is a more universal solution for people trying to do this.

If there is, I'd like to help out in the Community Documentation or in some way. Installing on an ext drive is something that I picture a beginner like myself doing, to avoid conflicts with the install on their machine, so I feel this really needs to be documented in an absolute beginner way. I avoided the "Advanced" tab on the installer for those boot options because I figured that was for people who knew they wanted to do some fancy non-standard boot process. I wasn't happy to find out after-the-fact that I needed to select that for what I saw as a basic install. Live & Learn, but I hope others can avoid my mistake.

BTW, I'm still confused if I was supposed to point that boot loader to sdc, or sdc5 in my case.  My USB HDD came up as sdc, but I was installing to the logical partition 5. I saw warnings about bootloaders and partitions, but I couldn't figure it out, and when it would not boot on my PC901 after installing and selecting sdc, I re-installed and selected sdc5. I *think* that was the final install, but to be honest I lost track along the way.

I'll add - I have no problem re-installing the OS on this USB HDD, I haven't modified in anyway, no big deal if that is something to help get it straightened out. I am worried about doing anything to my EM725, it is my daily machine now.

-NTL2009

---

### Post by C.S.Cameron on 2010-07-09
At this moment I'm looking at deleting grub2 from my flash drive and reinstalling grub legacy.

---

### Post by QLee on 2010-07-09
[QUOTE=C.S.Cameron]Grub2 seems to have complicated booting a full install to USB a bit.[/QUOTE]

This isn't correct, which drive to boot (which is hd0) is a function of the system BIOS, that happens before the bootloader in the MBR loads.

[QUOTE=C.S.Cameron]I don't think you can go wrong by disabling the internal HDD of the machine you are using to install to USB.[/QUOTE]

Well, many people have because they don't understand how grub works and where to put the MBR when they have multiple drives. I've seen lots of posts in the last year.

---

### Post by QLee on 2010-07-09
[QUOTE=NTL2009]...

BTW, I'm still confused if I was supposed to point that boot loader to sdc, or sdc5 in my case.  My USB HDD came up as sdc, but I was installing to the logical partition 5. I saw warnings about bootloaders and partitions, but I couldn't figure it out, and when it would not boot on my PC901 after installing and selecting sdc, I re-installed and selected sdc5. I *think* that was the final install, but to be honest I lost track along the way.
[/QUOTE]

You want the MBR portion of GRUB in the MBR of the drive which you have optioned your system BIOS to boot from (that's what you choose at the "advanced" button) and it has to point to the partition where the rest of GRUB lives (usually your Ubuntu install - the partition that has the "/boot" which you want to use).

[Edit] So, if I have followed the thread correctly and understood what you want, then you want to install Ubuntu to sdc5 and (at the advanced button) choose sdc , then option the system you want to boot so that it boots from USB (selecting the correct USB drive of course).

---

### Post by john newbuntu on 2010-07-09
Once you get to the grub rescue prompt, boot using the CLI:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

---

### Post by oldfred on 2010-07-09
the grub install to the partition will have no effect on your booting or boot problems. Generally you do not install to a partition and grub2 does not like to be in a partition as it thinks it is less reliable. Unless you use another boot loader and chainload to the partition an install in a partition is not used. Only the install in the MBR. 

BIOS boots by jumping to the MBR of the primary master. With SATA you now can select boot drive in BIOS where before you had to jumper the hard drive as primary master. My BIOS with only SATA still calls it primary master as the boot drive.

I found when I installed to a USB flash drive and then removed another USB flash drive I had used for installing, the drive order was confused. sdg became sdf and I had to manually edit the hd number at the grub menu to a different number to get it to work.  At the grub menu I would use e to edit the menu and experiment with drive number. You know the partition so try all drive numbers from 0 to n until it works. (yes it is a kluge). After I updated mine I was able to boot in my portable as sdb, hd1 or my desktop sdd or hd3.

It may be that grub stops looking at drives once it finds an empty space. I have seen several cases where it does not seem to work and the UUID should work, but in just about every case it was a drive letter that was beyond the sequential list of drives.

---

### Post by NTL2009 on 2010-07-09
Thanks - I'll comment more fully on some of this later, but for now:

**john newbuntu**: Once you get to the grub rescue prompt, boot using the CLI:

I've done some of this before, but maybe now I understand it better, will try again.

So, I've got it set to boot from the USB HD, I get the grub rescue prompt. An 'ls' returns (on one line, I'll break it here for easier reading):

(hd0) (hd0,3) (hd0,2) (hd0,1)
(hd1) (hd1,5) (hd1,1)
(hd2) (hd2,4) (hd2,3) (hd2,1)

This confuses me - my root install is on partition 5. I thought that selecting the USB HDD as the boot device would label it as hd0, but that does not match my partition scheme.

I'm not sure what to use for the following root and prefix commands from that tutorial. I'm guessing that hd1,1 is where my GRUB2 is, and then hd1,5 is my root, but I don't know and don;t want to confuse things further by proceeding the wrong way.

I have done some of this before in my attempts to get my EM725 to boot again, so who knows what I hosed along the way? And since I installed several times, I may have GRUB at both the MBR of the device and the partition, I really don't know.

Anyhow - should I proceed with hd1,1 for the prefix, and 1,5 as the root?

-NTL2009

---

### Post by NTL2009 on 2010-07-09
> **oldfred said:**
> the grub install to the partition will have no effect on your booting or boot problems.   ...

BIOS boots by jumping to the MBR of the primary master.   ...

I found when I installed to a USB flash drive and then removed another USB flash drive I had used for installing, the drive order was confused. sdg became sdf and I had to manually edit the hd number at the grub menu to a different number to get it to work.

... (yes it is a kluge). 

Thanks **oldfred**, I had not seen your post when I posted the above.

I think you are saying something along the lines of what **bwallum** said above, and I am thinking that is the issue here.

I'm glad you said it is a kluge - anytime I need to think this hard about something, I figure there must be something screwy in the process. As **QLee** said *"I've seen lots of posts in the last year."* - that is certainly an indication that things are just not right. I am reasonablt proficient in some aspects of computing, and tech in general, but have little experince with boot process, and this is making my brain hurt!

The following is beyond the scope of this thread, so humor a bit of a rant/suggestion, but I can't help thinking that this whole boot process needs rethinking from some of the brains and coders in the Linux world. GRUB 2 looks to me like polishing a slide rule instead of inventing the calculator. I come from Mac OS9/OSX land, and I routinely did installs and copies on external drives and booted them on a variety of machines. Outside of obvious hardware limitations (you can't boot an Intel install on a PPC machine, of course), the process 'just worked'. From what I gather, all the info on an OS9/OSX bootable parition is kind of 'self-contained' and points to itself (that might not be a good technical description). So the Mac bootloader just gathers a list of anything that says it is boot-able, asks you to choose one, hands over control and it boots. That drive doesn't need to know anything about where it is in the chain, what other drives are connected, what the conditions were when it was installed/copied, or anything about hd#'s, sd#'s, UUIDs, etc. It just does its thing.  I don't know if there is a downside to this, or what would be hard about emulating this in Linux, but it sure seems to solve a lot of problems. /rant

Hope that didn't sound negative - I am super-impressed with Ubuntu in so many ways. I'm floored that a user community has managed to do so many things so much better than the commercial suppliers. But some of these nagging problems really put a damper on my enthusiasm at times. And I do want to help - if I can get my head around this, and help improve the documentation I'd like to take a stab at that. But I've got to get my system working before I can explain to others what to do.

-NTL2009

---

### Post by NTL2009 on 2010-07-09
[FONT=Courier New][FONT=Arial]**oldfred:** *At the grub menu I would use e to edit the menu and experiment with drive number. *

But I just get the grub rescue prompt, and  'e' is unknown command.  Should I do this from my EM725, booting to the USB HD?

Here is what I did try so far from grub rescue:

here's my (formatted) ls output -   

(hd0) (hd0,3) (hd0,2) (hd0,1)
(hd1) (hd1,5) (hd1,1)
(hd2) (hd2,4) (hd2,3) (hd2,1)

I used those set prefix and set root commands -[/FONT]

Prefix .....Root ......ls /boot
1,1        1,5       File Not Found
1,1        1,1       Unknown File system
0,1        0,5       No such partition
2,1        2,5     [/FONT][FONT=Courier New]  No such partition
[/FONT][FONT=Courier New]0,1        0,1       File Not Found[/FONT]

I think I should get some kind of response from the 1,1 1,5 combo?

-NTL2009

---

### Post by oldfred on 2010-07-09
The e is if you get to a menu, to edit the menu entries.

Grub is installed to the MBR or hd1 and your install is then in hd1,5.

I would think it should be this but I never had to use it:
      ls
      set root=(hd1,5)
      linux /boot/vmlinuz root=/dev/sdb5 ro
      initrd /boot/initrd
      boot
[COLOR=Red]Corrected:[/COLOR]
ls
      set root=(hd1,5)
      linux /vmlinuz root=/dev/sdb5 ro
      initrd /initrd
      boot

---

### Post by NTL2009 on 2010-07-09
> **oldfred said:**
> The e is if you get to a menu, to edit the menu entries.

Grub is installed to the MBR or hd1 and your install is then in hd1,5.

I would think it should be this but I never had to use it:
      ls
      set root=(hd1,5)
      linux /boot/vmlinuz root=/dev/sdb5 ro
      initrd /boot/initrd
      boot

OK, that is making some sense to me (the MBR being hd1 and my root install being hd1,5), but when I do the 

linux /boot/vmlinuz root=/dev/sdb5 ro

I get " Unknown command 'linux' " which I'm assuming is because when I do ls /boot it says 'file not found' - it just does not have what it is expecting?

I've seen references to doing  *ls (hdx,y) /boot *but I get err msgs from those combos to (bad filename, unknown filesystem)

-NTL2009

---

### Post by QLee on 2010-07-09
[QUOTE=NTL2009]... As **QLee** said *"I've seen lots of posts in the last year."* - that is certainly an indication that things are just not right. I am reasonablt proficient in some aspects of computing, and tech in general, but have little experince with boot process, and this is making my brain hurt!
...[/QUOTE]

I disagree with your intrepretation of what I wrote. Almost all of the posts I referred to were ones where someone didn't understand the new GRUB (Grub2/GRUB_PC) and made an error in judgement thus causing the trouble they were trying to get help with. This often happened because the poster had a mindset that they just click on something and it will take care of any mistakes they've made, in short, an unreal expectation. I know most people don't read documentation or even release notes and get away with that most of the time but sometimes new methods of doing things require knowledge first. In short, it's not GRUB's fault. The Ubuntu developers made a nice upgrade path for the transition to GRUB2 but some people didn't read even the messages that printed out on their screen and ended up never finishing the path. On a simple install, GRUB2 usually doesn't give even a totally inexperienced user a problem but when it comes to multi-booting the problems have occurred but, once again, it's from lack of knowledge (and that advanced button which has confused many), that and the fact thatwhat  used to be partition 0 in legacy GRUB is now partition 1 in GRUB2. But all of this is can be learned, I had to learn it over the last year too.

I just want to note:
I have a USB drive with a full install of Ubuntu on it and I have booted it to three different systems by booting to the USB. (it's netbook remix but that is not sufficiently different from a regular install to matter) so ultimately you will be able to do it. 

But, I suggest you take a break, it's hard to learn things quickly under pressure. I imagine it will start to make sense if you don't try to cram all of it in your head at one time or absolutely have to have a working USB drive by this evening.

I wish you good luck!

---

### Post by oldfred on 2010-07-09
I gave you wrong locations. If in /boot you have to refer to the version. i.e. /boot/vmlinuz-2.6-.xx.xx  and the same for initrd. The one in root is a link to the newest kernel and saves having to have the specific kernel version typed in.

ls
      set root=(hd1,5)
      linux /vmlinuz root=/dev/sdb5 ro
      initrd /initrd
      boot

---

### Post by NTL2009 on 2010-07-09
> **QLee said:**
> I disagree with your intrepretation of what I wrote.

I apologize if I misinterpreted your comments and appeared to put words in your mouth. That wasn't my intent, I was really using that as a jumping off point for my own comments. Sorry.

> On a simple install, GRUB2 usually doesn't give even a totally inexperienced user a problemI agree - the install itself on my PC901 and EM725 was painless - I was very impressed! The Live mode with Try/Install was very 'elegant'. Though I needed to study up a bit to learn about the partitioning, and I was trying to be cautious about retaining W7 on the EM725, and that took some study (mostly because of MS not wanting to 'play nice with others') - though it might have also worked just fine just 'pressing the buttons', esp if I was wiping W7. But since we are otherwise an OSX household, I thought it would be good to have a Win version around.

>   but when it comes to multi-booting the problems have occurred but, once again, it's from lack of knowledge (and that advanced button which has confused many), that and the fact that what  used to be partition 0 in legacy GRUB is now partition 1 in GRUB2.Another thing adding to the confusion is it is hard to tell if information I read is for GRUB or GRUB2 - even the version numbers say 1.xx, and most files and references are to "GRUB", whether it is legacy or "GRUB2" - maybe a total name change would have been better. Changing the partition numbers between the two seems rather arbitrary to me. Maybe there is a good reason I just don't understand, but things like that also need to be flagged so people don't make mistakes so easily. And yes, there really needs to be some added information on that "Advanced" tab - it did me in, and I'm apparently not the first or the last.

I guess we can agree to disagree on the robustness of design of GRUB2, or maybe I'll change my mind as I learn more. I will at least say that the documentation needs work - if a user needs to gain some specific knowledge before installing on an external drive, then there should be some kind of warning about that. The impression that I got was that this should be fine for an install of this sort. I don't consider it 'advanced' at all, it sure wasn't in OSX, I did it dozens of times. It's not until after I had problems that I started searching for bugs - beforehand, I would not have even known what to search for. Never saw grub rescue prompt before.

> I just want to note:
I have a USB drive with a full install of Ubuntu on it and I have booted it to three different systems by booting to the USB. (it's netbook remix but that is not sufficiently different from a regular install to matter) so ultimately you will be able to do it. Yes, thank you - I initially I wanted to verify that this was indeed supported in the way I expected. I didn't want to fight a battle that could not be won (or not be won w/o encyclopedic knowledge of Linux)

> But, I suggest you take a break, it's hard to learn things quickly under pressure. I imagine it will start to make sense if you don't try to cram all of it in your head at one time or absolutely have to have a working USB drive by this evening.

I wish you good luck!Thank you - but OTOH, if I put it down for a few days, I end up having to relearn where I was - it just doesn't stick, esp when I can't put the whole picture together. That's why I'm trying to get through it, I'm hoping it will be easier to fill in some details once I get from here to there. But I know what you mean.

> I know most people don't read documentation or  even release notes and get away with that most of the time but sometimes  new methods of doing things require knowledge first.I think I'm sort of caught in a Catch-22 at the moment. I've been doing a lot of reading, a lot of this GRUB2 stuff isn't making sense to me, probably because I don't really understand the architecture of Linux, and how the pieces fit. But then how do I learn about the architecture if I can't reliably get an install together that I can play with?

Sorry to get long winded and philosophical here, but I really like Ubuntu/Linux and I want to see it succeed and gain wider adoption. Granted that anybody motivated enough to actually attempt an install of an OS is going to generally be a little more knowledgeable than your average computer user, but that doesn't mean that everyone really wants to learn the intricacies of a boot process just to install it on a portable drive. I want to install this so I can learn about Ubuntu, I don't really want to have to learn so much just to install it. That's my Catch-22.

Thanks for listening - I'm sure I'll get over this hump.

-NTL2009

---

### Post by QLee on 2010-07-09
> **NTL2009]I apologize if I misinterpreted your comments and appeared to put words in your mouth. That wasn't my intent, I was really using that as a jumping off point for my own comments. Sorry.[/QUOTE]

Acknowledged and accepted but it wasn't necessary, I just wanted to clarify. And, yours is not the worst misinterpretation I have experienced or likely will in future.  said:**
> 
Another thing adding to the confusion is it is hard to tell if information I read is for GRUB or GRUB2 - even the version numbers say 1.xx, and most files and references are to "GRUB", whether it is legacy or "GRUB2" - maybe a total name change would have been better. 

No, legacy GRUB was 0.9x, never made it to 1.0. But I agree about the confusion, however, they make those decisions upstream and I can understand why they want to keep the "brand" name.

> **NTL2009]Changing the partition numbers between the two seems rather arbitrary to me. Maybe there is a good reason I just don't understand, but things like that also need to be flagged so people don't make mistakes so easily. [/QUOTE]

Well, it does appear in lots of documentation. Actually, I imagine it was a good idea in the long run because people often had trouble remembering partition 0 meant the 1st partition and there were troubles with that. Now the first partition is partition 1 in GRUB.

[QUOTE=NTL2009]And yes, there really needs to be some added information on that "Advanced" tab - it did me in, and I'm apparently not the first or the last.[/QUOTE]

Nope, and I'd be willing to bet the developers are aware of the complaints too.  said:**
> I guess we can agree to disagree on the robustness of design of GRUB2, or maybe I'll change my mind as I learn more. 

Sure, either way. I know I swore a lot and hated the fact that what I previously knew how to do easily, now needed learning and practice. But over time I started to see how some of the changes will make a better future.


[QUOTE=NTL2009]I will at least say that the documentation needs work - if a user needs to gain some specific knowledge before installing on an external drive, then there should be some kind of warning about that. [/QUOTE]

Virtually all documentation in the GNU/Linux world needs work, problem is that in open source, it's usually done by volunteers who also have lives and have to make a living. Some has been poorly translated and many of the geeks who could write the correct answers aren't interested in writing documentation. Compound that with a distro with a 6 month release cycle (for example Ubuntu) and I'm sure you understand how documentation is going to lag. You're certainly encouraged to take part if you so desire.
[http://www.ubuntu.com/community/get-involved](http://www.ubuntu.com/community/get-involved)


[QUOTE=NTL2009]Thank you - but OTOH, if I put it down for a few days, I end up having to relearn where I was - it just doesn't stick, esp when I can't put the whole picture together. That's why I'm trying to get through it, I'm hoping it will be easier to fill in some details once I get from here to there. But I know what you mean.[/QUOTE]

Different people learn with different methods. I understand the "aha" moment of which you speak. Just remember to breathe and try to keep it fun.

[QUOTE=NTL2009]I think I'm sort of caught in a Catch-22 at the moment. I've been doing a lot of reading, a lot of this GRUB2 stuff isn't making sense to me, probably because I don't really understand the architecture of Linux, and how the pieces fit. But then how do I learn about the architecture if I can't reliably get an install together that I can play with?[/QUOTE]

Well, you might have started with something more simple and waited to get that USB working on all three computers until you were more advanced.

Have a look at the last sticky thread at the top of this sub forum page. The one with the subject, "New to Ubuntu? Start here...", you'll probably find some useful stuff there. And just for fun, open a terminal and enter the command, man hier. That will show you something about the file system hierarchy.

[QUOTE=NTL2009]Thanks for listening - I'm sure I'll get over this hump.[/QUOTE]

Yes, I expect you will.

---

### Post by NTL2009 on 2010-07-09
> **QLee said:**
> 

Virtually all documentation in the GNU/Linux world needs work, problem is that in open source, it's usually done by volunteers who also have lives and have to make a living. ... You're certainly encouraged to take part if you so desire.
[http://www.ubuntu.com/community/get-involved](http://www.ubuntu.com/community/get-involved)



I certainly understand how the documentation can lag (it takes second fiddle in the commercial world also), and I do hope to contribute once I get more up-to-speed.


> Well, you might have started with something more simple and waited to get that USB working on all three computers until you were more advanced.I was under the impression that what I was doing *was* simple  - (surprise!) ;).  After all, the USB thumb drive with the Try/Installer booted fine on each machine, my installs (09.04 & two 10.04) booted fine. And when I looked through those docs you pointed out (I've at least skimmed just about all of them), the USB issues I saw were regarding older computers that don't boot USB. And in my experience with OS9/X, this _is_ simple. And since the Ubuntu installer seemed as simple as an OSX install,  I didn't see anything that made it seem advanced. And I was even able to add a swap partition after-the-fact on the install on my PC901 to get it to hibernate, which is a small step above 'simple', IMO.

But, live & learn - aside from this, I have an option I'd like to throw out on this - I'll make a separate post after I research it a bit.

-NTL2009

---

### Post by NTL2009 on 2010-07-10
It turns out that it is very easy to remove the internal HDD from my EM725 laptop - 2 screws, slide over and lift out. So I figured it could not hurt to try to re-install on that ext USB HDD with no other drives present. I had nothing there to lose, maybe I'll learn something in the process.

Install went smooth, I clicked the "Advanced" tab, it initially said sda, but when I tabbed through it it seemed to report only the sdb device and its partitions, so I chose the device itself.  

As before, all combinations of booting from the EM725 were fine. I had high hopes for the PC901, but I got the grub rescue prompt :(

Oh well, worth a try. So yes, I'm putting this issue to bed for a few days ;) Then I'll run the scripts again, see if I or anyone here can make any sense of them.

Thanks - NTL2009


-ERD50

---

### Post by john newbuntu on 2010-07-10
The fact that you got to the grub rescue prompt means that grub2 (possibly the embedded core.img in the DOS compat region) could not find a workable grub.cfg.  Anyways, once you get to the grub rescue prompt, try these commands (except the one that I have commented with --).  Now, I am assuming that hd1,5 is the linux root partition on your external USB.  If not, keep changing it to what you think is right.

```
ls
--just to check what devices and partitions are available.
set prefix=(hd1,5)/boot/grub
set root=(hd1,5)
ls /boot/
---This should hopefully list the kernel and initrd files.
insmod (hd1,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sdb5 ro
initrd /initrd.img
boot
```If at all you manage to boot into your external using this method, it is only temporary.  Run sudo update-grub.  In any case post back your results of everything.  Might help someone someday.

---

### Post by C.S.Cameron on 2010-07-10
It may not make a difference, but when I install to USB with all other drive disabled I ignore the advanced tab.
I also have better luck installing from a Live CD and not a Live USB.
Grub2 searches for other O/S and includes them in grub.cfg which is not usually desired in a flash drive install.
UUID's also complicate things over the old root(x,x) method.

---

### Post by NTL2009 on 2010-07-10
[FONT=Arial][SIZE=2]thanks** john newbuntu** - I am going to take the advice of some posters above, and move a bit slower and step-wise and try to more fully understand what I'm doing here. These are still rather 'magic' commands to me. So maybe you or someone else will have the patience to verify what I'm thinking here (and I promise to post back as I learn - I hate those threads that just end w/o feedback - did the suggestions work or not?), and if I learn enough to add to the documentation somewhere, I'll do that too.

I posted last night that I removed the int HDD from my EM725 and reinstalled Ubuntu onto my USB HDD (same setup - root to part5; home to part6; swap is part7), selecting the "Advanced" tab and selecting the _device_ as the target (sdb-with the text descriptor of my Hitachi 500GB drive in this case). Booting results were the same, fine on the EM725 (w&w/o the internal drive installed), but PC901 gives the Grub Rescue prompt.

I am now at the grub rescue prompt on the PC901, when I type 'ls' I get a slightly different output than I got earlier:
[/SIZE][/FONT]
[FONT=Arial][SIZE=2](formatted) ls output - 

(hd0) (hd0,3) (hd0,2) (hd0,1)
(hd1) (hd1,4) (hd1,3) (hd1,1)[/SIZE][/FONT]
 [FONT=Arial][SIZE=2](hd2) (hd2,5) (hd2,1)        << so the designations for hd1 and hd2 are swapped around from before...[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Yet, when I do a **set** command (with no parameters, it should just return current settings), I get:[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]prefix=(hd0,5)/boot/grub[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]root=hd0,5[/SIZE][/FONT]

[FONT=Arial][SIZE=2]So it would appear to me that this is the problem, and that I need to follow your instructions using hd2,5 instead. But that would be 'magic' to me until I understand _why_ I am doing this.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[SIZE=2][FONT=Arial]WAIT A MINUTE!  I've been doing some more **ls** commands, and I'm gathering some info from this. I will need to reboot this machine to validate what I'm seeing, but I'll post where I am now - but it looks like the drives were not the ones I think they are. And it looks like my logical partitions of 5,6,7 on my USB drive just are not showing up on the PC901.

The trigger was, when I did a:

[/FONT][/SIZE]                                  [FONT=Arial][SIZE=2]**ls (hd2,5)/**   I got a listing that clearly was the /Home partition of my PC901 install (I had two users there). So that is leading me to believe that hd0 is referencing my ext USB (which is what I would have thought), but since the only hd0,x I get from **ls** are  
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2](hd0) (hd0,3) (hd0,2) (hd0,1) I am stumped. Then again, maybe this is key to the problems - should I expect to be able to  see [/SIZE][/FONT][FONT=Arial][SIZE=2] (hd0,5) (hd0,6) (hd0,7) here? An ls of those returns "no such partition". Reminder - logical partitions 5,6,7 are where I installed Ubuntu on the USB drive

One more data-gathering question: Can I get into terminal after a normal boot and run these grub rescue prompts? I'd like to see what my EM725 returns.

TIA - NTL2009[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by NTL2009 on 2010-07-10
> **C.S.Cameron said:**
> It may not make a difference, but when I install to USB with all other drive disabled I ignore the advanced tab.

I probably didn't need to touch it - I'm pretty sure it would have just defaulted to the USB DEVICE (sdb in my case), but I wanted to explicitly see where it was pointing, as this is what got me into all this trouble to start with (I couldn't boot my EM725 after unplugging the USB drive, because if I understand this, it wrote to GRUB on my EM725 and it pointed to the USB drive - so remove and no boot).

> 
I also have better luck installing from a Live CD and not a Live USB.
Grub2 searches for other O/S and includes them in grub.cfg which is not usually desired in a flash drive install.
UUID's also complicate things over the old root(x,x) method.

Interesting. Although my PC901 does not have a CD, that means different procedures for each, and ideally I'd like to stick to one procedure to reduce variables, but I will make a note of it, thanks.

-NTL2009

---

### Post by NTL2009 on 2010-07-10
OK, another beginner Q as I try to understand the ins/outs of this:

Is there any difference between selecting the boot device by interrupting the BIOS (ESC on my PC901, F12 on my EM725) to bring up the boot device selection menu, versus getting into the BIOS settings (F2 on both my machines)?

I understand with F2 you can save the config to make it 'sticky' on re-boot, but other than that, would these drive assignments change or anything else in one versus the other?

-NTL2009

---

### Post by john newbuntu on 2010-07-11
> **NTL2009 said:**
> [FONT=Arial][SIZE=2]

I am now at the grub rescue prompt on the PC901, when I type 'ls' I get a slightly different output than I got earlier:
[/SIZE][/FONT]
[FONT=Arial][SIZE=2](formatted) ls output - 

(hd0) (hd0,3) (hd0,2) (hd0,1)
(hd1) (hd1,4) (hd1,3) (hd1,1)[/SIZE][/FONT]
 [FONT=Arial][SIZE=2](hd2) (hd2,5) (hd2,1)        << so the designations for hd1 and hd2 are swapped around from before...[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT]

> 
 [FONT=Arial][SIZE=2](hd0) (hd0,3) (hd0,2) (hd0,1) I am  stumped. Then again, maybe this is key to the problems - should I expect  to be able to  see [/SIZE][/FONT][FONT=Arial][SIZE=2]  (hd0,5) (hd0,6) (hd0,7) here? An ls of those returns "no such  partition". Reminder - logical partitions 5,6,7 are where I installed  Ubuntu on the USB drive[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]You are right.  Just to restate the obvious, your 4GB drive has partitions 1,3 and 4.  This corresponds to your what gets shown in (hd1)
Similarly your 16GB drive has sdb1 and 5.  This  corresponds to (hd2)
The 500GB external has partitions 1,2,3,5,6 and 7. I expected this to  show up as (hd0,1), (hd0,2)...(hd0,7).  Why it does not show (hd0,5) is something beyond me.   Perhaps a problem with the ls.mod module or a size barrier restriction?

Anyway, since we know for sure that (hd0,5) is where your boot sector  is, you could try the brute force way of running the same set of commands I gave you BUT change the (hd1,5) with (hd0,5).  Also replace sdb5 with sda5.  This is assuming  that you get the same results with "ls" from the rescue prompt.  Please post back your results.

For answer on your post#21, that option is only to decide the disk to boot from and you are right again - The save option makes it sticky on reboot.  As far as I know, the drive assignments do not change although I am not a 100% sure on this.

> 
[FONT=Arial][SIZE=2]One more data-gathering question: Can I get into terminal after a normal  boot and run these grub rescue prompts? I'd like to see what my EM725  returns.[/SIZE][/FONT]
You can not run grub rescue commands from a terminal since you would have passed that stage.

---

### Post by QLee on 2010-07-11
NTL2009,

Having stepped back from your thread because it was obvious that all of us firing commands and things to try at you at one time was probably just adding to your stress and confusion. Some of the advice was even opinion that was presented as fact. You're getting good help from john newbuntu follow along slowly and make sure you understand the steps you're asked to take, or ask for clarification. I'm somewhat surprised that you didn't take the break you mentioned but, I too sometimes become obsessed with what I'm working on and have trouble putting it down. At least, remember to sleep.

Are you absolutely sure that when you re-installed (post 22) that you did the install back to partitions 5,6,7?

This situation, where there are multiple drives with the same OS and version, is a classic for mistakes in working on a different partition than one thinks they are working on. One of the ways I avoid that is by labelling my partitions when I format them with a label that makes sense to *me* so I can identify them more easily in a multiple drive system. For example, I might choose to label the Ubuntu partition on the USB drive as ubu10move. 

Keep at it, you're already understanding more than you realise. Success is just around the corner.

---

### Post by NTL2009 on 2010-07-11
> **QLee said:**
> NTL2009,
 I'm somewhat surprised  that you didn't take the break you mentioned but, I too sometimes become  obsessed with what I'm working on and have trouble putting it down. At  least, remember to sleep.

Understandable, but before I took a little break, I wanted to document more clearly what I had done so far, else it would all be mush-mash to me when I return. The calm of documenting it did set off a few light bulbs and other questions though, so I figured I'd post those to see if I got feedback in the mean time.

> Are you absolutely sure that when you re-installed (post 22) that you  did the install back to partitions 5,6,7?

This situation, where there are multiple drives with the same OS and  version, is a classic for mistakes in working on a different partition  than one thinks they are working on. One of the ways I avoid that is by  labelling my partitions when I format them...
Keep at it, you're already understanding more than you realise. Success  is just around the corner.Good point, and I (calmly ;) ) followed your advice. I'm pretty sure I knew what was where from the start ( I learned a bit more about partitions/issues when installing Linux on my EM725, as I wanted to keep W7, and their install used up 3 parts already - ugly), but I validated it from a  few different angles just to make sure I wasn't fooling myself, and then I labeled them. That does help. This thing about the logical partitions not appearing in the grub rescue **ls** did throw me, and I'm more and more certain that this is a symptom of the source of the problem.

> **john newbuntu said:**
> 
The 500GB external has partitions 1,2,3,5,6 and 7. I expected this to  show up as (hd0,1), (hd0,2)...(hd0,7). ** Why it does not show (hd0,5) is something beyond me.   Perhaps a problem with the ls.mod module or a size barrier restriction?**

Anyway, since we know for sure that (hd0,5) is where your boot sector  is, you could try the brute force way of running the same set of commands I gave you BUT change the (hd1,5) with (hd0,5).**  Also replace sdb5 with sda5.**  This is assuming  that you get the same results with "ls" from the rescue prompt.  Please post back your results.

Before I went ahead with those commands using hd0,5 - I stood back and took one more look (calmly ;) ), and I rechecked that the set command was returning:

                                 [FONT=Courier New][SIZE=2]prefix=(hd0,5)/boot/grub[/SIZE][/FONT]
 [FONT=Courier New][SIZE=2]root=hd0,5[/SIZE][/FONT]
 
So my thinking at this point is, it is already pointing to the correct place, but it can't 'see it' for some reason. So if I understsnd correctly, running thos commands (set prefix & root) would seem to be just setting something that appears to already be set (but I'll try it later if you think it is a good step). I don't know anything about ls.mod (yet, I'll research later), but the 'size barrier' you mention makes me wonder, since this is a rather large (500GB) drive, and I have large partitions for 1,2,3 ( ~156, 120, 110 GB respectively). Maybe there is something about my PC901 that cannot 'see' past these large partitions, but my EM725 can?

Also, i didn't understand your 'sdb5/sda5' comment, I didn't see any sdx,y statements in those commands, they were all hdx,y format- maybe you were just meant generally that my sdb is now sda when I boot this way?

So I won't act on this yet, but two things I'm contemplating:

1) my PC901 comes up with GRUB 1.97~beta4 when it boots internal - I guess this isn't an issue, it should be seeing the grub on the USB MBR (_GRUB 1.98_ ) right?, but I'll throw it out there as a Q.

2) I could repartition this USB drive and start from scratch, maybe a different partition scheme would be more 'robust'? I have some data backed up on one partition, but it isn't that critical, I can re-copy later. I would like to have 4 partitions on this drive for flexibility, but if I can make the 1st a logical and put my root, home, swap there that works for me (if it works for GRUB2). Or something else would be better? Only one extended partition per drive, right?

TIA again -NTL2009

---

### Post by john newbuntu on 2010-07-11
> 
Also, i didn't understand your 'sdb5/sda5' comment, I didn't see any sdx,y statements in those commands.....
So I won't act on this yet, but two things I'm contemplating:

In post #23, I had listed this command:
     linux /vmlinuz root=/dev/sdb5 ro
I wanted this to be replaced with:
     linux /vmlinuz root=/dev/sda5 ro
since sda5 was what I/we thought to be the root partition.

There is no harm in going ahead and trying those commands even though the 'set' command gives the right value. Lets see what it says.  Remember that these commands do not stick on your next boot.

To make sure that your logical and extended partitions are ok, fire up gparted from one of your ubuntu installation or a liveCD and check if it finds any problem.  You could also run "sudo sfdisk -l /dev/sdX" where X is the external USB device.

> 
1) my PC901 comes up with GRUB 1.97~beta4 when it boots internal - I  guess this isn't an issue, it should be seeing the grub on the USB MBR  (_GRUB 1.98_ ) right?, but I'll throw it out there as a Q.

Your PC901 has karmic that comes with grub1.97...  It should be able to see the other disks/partitions that have 1.98... installed.

> 
2) I could repartition this USB drive and start from scratch, maybe a  different partition scheme would be more 'robust'?
....
(if it works for GRUB2). Or something else would be  better? Only one extended partition per drive, right?

Yes only one extended per drive.  Just think about future growth of these partitions while deciding on the scheme.  Also have one NTFS partition so that you can exchange data with windows perhaps on another computer.

Before repartitioning, if you have time on your hands and want to experiment a bit more, there are a few things you could do.  One is to reinstall grub to the MBR manually from a liveCD.  drs305 describes that here in step#13:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

What this does is write the grub to the MBR, embed the core.img to the post MBR region and copy/modify files in /boot/grub of your external.  Make sure you run it with the "--root-directory=/mnt" option where /mnt is the mountpoint of the root(/) directory of your external HDD.  Then reboot to see if the ls command detects your other partitions and whether you are able to boot normally (or from the rescue prompt) from the external.

The theory I have is that the search.mod gets embedded along with core.img and that module uses UUID in determining where the /boot/grub directory is on your external.  Perhaps the normal install does not do that and uses the drive/partition#.  Again this is just a guess. If you are able to boot in, the immediately run "sudo update-grub" from a terminal.

---

### Post by QLee on 2010-07-12
Things appear to be distilling down to something about that USB drive or some interaction (or lack thereof) between it and the 901.

When the boot info script was run the first time, Post4, there was already a problem reading the partition, doesn't seem to be reporting filesize correctly.

> =================== sdc5: Location of files loaded by Grub: ===================


 439.2GB: boot/grub/core.img
 424.8GB: boot/grub/grub.cfg
 439.2GB: boot/initrd.img-2.6.32-21-generic
 439.2GB: boot/vmlinuz-2.6.32-21-generi
 439.2GB: initrd.img
 439.2GB: vmlinuzI also note this from Post 22
> It turns out that it is very easy to remove the internal HDD from my EM725 laptop - 2 screws, slide over and lift out. So I figured it could not hurt to try to re-install on that ext USB HDD with no other drives present. I had nothing there to lose, maybe I'll learn something in the process.

Install went smooth, I clicked the "Advanced" tab, it initially said sda, but when I tabbed through it it seemed to report only the sdb device and its partitions, so I chose the device itself. At this point, because you had the "real" hard drive out of the system, I would have expected the correct choice to be sda, it should have been the only harddrive. I will say here, I've never even seen a 901, don't know anything about how it's hardware is configured.


So what might be instructive at this point, would be to plug the USB drive into the em725 and repeat the steps you have just done on the 901. Might give us some more data to work with. While you have it on there, run the boot info script again and post it so we can see what things look like now.

This has turned into a more interesting problem than I originally thought. Lucky for you NTL2000, it's providing lots of opportunities to learn.

@ John newbuntu, I'm not trying to "take over", just wanted to point out something and make a suggestion for more data, I imagine you are finding this as "interesting" as I do and the OP will continue to benefit from your good explanations.

---

### Post by bwallum on 2010-07-12
I have probably missed it noted in earlier replies but just in case, the latest Grub2 official manual was released on 2nd July 2010.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by john newbuntu on 2010-07-12
@QLee: Useful contributions such are yours are always appreciated.  I certainly don't think you are taking over.  Overseeing what I or others say is always healthy IMHO.

I have always ignored those file sizes on the last part of the report. These, I believe are the end point locations of the file, although I would defer the explanation to meierfra and co-workers for a more detailed explanation.

As I understood the OP, there is no sdb on EM725 since there were no other drives present other than the external.  So grub got installed into the only MBR. I suggested the OP to reinstall grub to the MBR of the external from a liveCD pointing the root-directory to the correct location for grub files to sort out any issues with core.img.

---

### Post by QLee on 2010-07-12
[QUOTE=john newbuntu]...  I certainly don't think you are taking over.  Overseeing what I or others say is always healthy IMHO.[/QUOTE]

+1

[QUOTE=john newbuntu]I have always ignored those file sizes on the last part of the report. These, I believe are the end point locations of the file, although I would defer the explanation to meierfra and co-workers for a more detailed explanation.[/QUOTE]

Well, obviously I didn't look at them either, initially (nor would I normally). Just when I looked back over everything because things we were seeing weren't making sense. Have a look back at what the b-i script shows for sda in post 4, those file sizes seem to be in the correct ballpark.

[QUOTE=john newbuntu]As I understood the OP, there is no sdb on EM725 since there were no other drives present other than the external.  So grub got installed into the only MBR. I suggested the OP to reinstall grub to the MBR of the external from a liveCD pointing the root-directory to the correct location for grub files to sort out any issues with core.img.[/QUOTE]

Yes, I agree that might work. However, because of what we are seeing, I would also like to see how that USB drive presents itself when booted on the EM725, are the 5,6,7, seen there before the "fix". Some depends on NTL2000 and how much energy there is to devote to this.

---

### Post by NTL2009 on 2010-07-12
Just a quick note, since I'm getting so much attention here - it will probably not be until later today that I have a chance to follow up, but a few things now so I am ready to go at that time:

You have mentioned "LiveCD" and I'd like to know if you mean that literally or is any "live" running installer OK (I've been using a USB thumb drive for all my 10.04 installs). There was a comment earlier with the opinion that a CD may be more robust, so I'll do that if others agree. I may need to burn one, I can't recall if I made one for 10.04 or not, I know I did some version, just to see if I could boot it (it did), but I didn't go any further with it at the time.

I did some checking last night from LIVE-USB on the PC901 - Gparted does not seem to see any problems at all, the** fdisk-l** command output seemed normal to me - all partitions found, labeled and the start-end blocks as I would expect, extended partition#4 marked as such, logical p5,6,7 marked correctly. I then re-did those set prefix & root commands last night, before/after reinstall grub2 (which looked to be workign away for 10 seconds or so, and reported "FINISHED - NO ERRORS", but I get the same thing with **ls** in grub rescue not showing the logical parts 5,6,7. So any further commands to access the files there fail with a "no such partition" response.

I was strongly considering just repartitioning this guy, but since this error seems to have caught some interest, I'll invest more time with you people to try to find out _why_ it is doing it, rather than just a possible brute force fix. Maybe some good will come from it.

Also, to clarify my setup, as it is easy to get lost in these threads:

EM725 has a 250GB HDD, 3 partitions hogged by Win7, with 10.04 on the 4th extended partition with a logical partition for each of root, home, swap. This is the machine that I was able to easily remove the int HDD from, and I did the most recent install to my USB HDD (500GB) from the EM725 with the int HDD removed. But I've since re-installed GRUB2 from the PC901.

ASUS PC901 - this has a 4GB SSD (soldered in, I think) that holds my root, plus a 16GB SSD for home, swap. Ahh, here are some notes/comment that I had made/saved earlier. Those sda3 and sda4 may be legacy from the original Xandros install, or BIOS firmware backup, I don't know, so I let them be when I installed 9.04 to replace Xandros:

  	 	 	 	 	 	  [FONT=Arial][SIZE=1]Here are some notes from Gparted on my PC901:[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=1]sda (my 4GB 'root') -[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=1]sda1 - ext4; mount point "/"	; 2.75GB/3.74GB used/size		; Flags: "boot"[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]sda3 - unkn; LABEL "BIOS" 	; 7.84MegaB size (no used shown)	; Flags: "lba" ?[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]sda4 - unkn; 			 	; 7.84MegaB size (no used shown)	; Flags:  nothing shown[/SIZE][/FONT]

 [FONT=Arial][SIZE=1]sdb (my 16GB "/home" and swap ) -   no Flags on any partition of sdb[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=1]sdb1 - linux-swap				;	;  2.50GB size (no used shown)[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]sdb2 - extended				;	; 12.53GB size (no used shown)[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]	sdb5; ext4	; LABEL "/home" 	; 12.53GB/1.83GB size/used[/SIZE][/FONT]
 
It looks odd to me that sda has no partition 2, but maybe that is no issue. I understand there being no sdb3&4, as my p2 is the extended and logical parts start at 5. At any rate, if I'm understanding this, when I point the BIOS to the external usb HDD, none of this *should* matter - it should just be looking for what's on the USB drive - though I think I see where it could possibly conflict with the grub install process, if that is going out and looking for anything connected in order to build the grub.cfg (and other?) files.

So yes, later I will try these suggestions from my EM725, and I'll remove the internal just to eliminate that variable. Since that post got longer than I intended, I'll re-ask - **Should I do this with LIVE-CD, or is live USB OK?**

-NTL2009

---

### Post by QLee on 2010-07-12
[QUOTE=NTL2009]...

So yes, later I will try these suggestions from my EM725, and I'll remove the internal just to eliminate that variable. [/QUOTE]

No, please leave the EM725 in working condition. Nothing to be gained with the drive out, that doesn't just eliminate a variable, it changes the conditions from when you ran the boot script on the 901 which I want to compare it to, I want to look at the differences the script reports between a workng 901(with the drive attached and not booting it) and a working EN725 (with the drive attached and booting it). 


If you choose to just reinstall GRUB to the MBR of the USB drive, I think you should do it from the GRUB version on EM725, that's the version that corresponds with the Ubuntu installed in the drive, isn't it? Or from the LiveWhatever you used to install it.


[Edit] Yes, I too am bothered by that missing sda2 and the fact that 3 and 4 don't show partition type.

---

### Post by john newbuntu on 2010-07-12
I am at a loss as to why the grub "ls" fails to see the logicals on your external when it can see it on my 500GB external.  Mine is not an ASUS but my extended partition begins at around the 40th GB and my last primary(NTFS) begins at around 100th GB.  I wish someone who has encountered a similar problem with ASUS can help (perhaps a BIOS flash?)

So, if there are no more ideas you get, repartition your external as you mentioned before installing ubuntu towards the beginning of the drive in a logical partition and see if that helps.

---

### Post by NTL2009 on 2010-07-12
> **QLee said:**
> 

[Edit] Yes, I too am bothered by that missing sda2 and the fact that 3 and 4 don't show partition type.

Just quickly, I really must run - but the ASUS PC901 never had Windows on it. It came with Xandros, which I found to be nice in some ways but very, very odd in others. Within about a week, I worked up the nerve to install Ubuntu on it, that seemed much better. I later re-installed 10.04 on it (maybe even 9.10, I'd need to check my notes), at that time I did some work on the paritions to add swap (and had to edit fstab to get it to 'see' the swap,  and some other files to get hibernate to work). It's possible I did something strange (or at least unconventional), my understanding of parititoning was even less than it is now ;)

john newbuntu - I'm also very suspicious of the BIOS, again, my limited understanding here, but from what I gather, it is BIOS to GRUB, and GRUB has to rely on info from BIOS to be able to read disks, so if GRUB doesn't 'see' those logical partitions, it seems to me that the problem lies with the BIOS. 

Geez, I'm never quick with these posting - I'll just throw out that re-partitioning my PC901 isn't out of the question either. I have not customized it so much, I'm pretty confident I could back up what I need, re-install, and get it reconfigured w/o too much pain. I'd like to get rid of those little 8MB partitions if they really are Xandros left-overs, but not f the BIOS is needing them of course.

-NTL2009

---

### Post by QLee on 2010-07-12
[QUOTE=NTL2009]
...
- I'll just throw out that re-partitioning my PC901 isn't out of the question either. I have not customized it so much, I'm pretty confident I could back up what I need, re-install, and get it reconfigured w/o too much pain. I'd like to get rid of those little 8MB partitions if they really are Xandros left-overs, but not f the BIOS is needing them of course.

-NTL2009[/QUOTE]

That's what I would do, I've not seen anything about the people running on 901s doing anything special (like leaving those partitions). I suppose you could ask about this over at the eeeuser forum, people over there should have a definitive answer for you. 

That one labeled BIOS ,(3) might be some trick the original OS used to "combine" the disks or something and which probably isn't needed now but that is just a guess.

---

### Post by NTL2009 on 2010-07-12
> **QLee said:**
> That's what I would do, I've not seen anything about the people running on 901s doing anything special (like leaving those partitions). I suppose you could ask about this over at the eeeuser forum, people over there should have a definitive answer for you. 


Good idea, I have not poked my head in the eeeuser forum in quite a while as the newer Ubuntu releases have worked very well with this HW right out-of-the-box.

-NTL2009

---

### Post by NTL2009 on 2010-07-15
An update, but it might be time for a change in direction (suggestions below), unless those helping me are still curious about the root problem, and maybe uncovering some bugs in GRUB or the install processes:

1) I re-partitioned my PC901 4GB SSD to a single partition, wiping those two 8MB (xandros legacy?) partitions. I re-installed 10.04, w/o formatting my /home partition on the 16GB SSD (sdb5 in this config, sdb1 is swap) to preserve it. PC901 seems all back to normal after a few program re-installs (still not booting the USB of course).

?? NOTE: Gparted now shows 1MB unallocated, sector 0-2047 on that 4GB SSD. It is possible that this start sector was set when I hit the apply button in Gparted and I missed it - when I clicked through I was trying to observe the settings and expecting one more check/sure/validate? button ( I obviously should be on _double-red alert_ when using a partitioning tool!) - I doubt this means anything, (or is just set for MBR? my other drives show 63 sectors for start), but thought I should mention it. I could reformat yet again for assurance. I'm getting good at this ;)

2) Ran the boot scripts from:[INDENT]PC901 w/USB attached; and from 
EM725 booted from the internal and 
EM725 booted from the USB drive.
[/INDENT]3) Prepared for a GRUB re-install. Rather than use a USB stick, I booted my EM725 (kept the int drive installed) from a 9.10 CD that I already had burnt. I verified this release used GRUB2, but it wasn't until I was installing that I wondered which version - it is 1.97~beta4 (same as I _had_ on my PC901 4GB SSD install - that is now 1.98 since yesterday's re-format/re-install from 10.04 installed that version).

4) I then re-installed GRUB, following #13 of the GRUB BASICS thread, summary of my commands:

sudo mount /dev/sdb5 /mnt 
 sudo grub-install --root-directory=/mnt /dev/sdb 
sudo umount /mnt  

It finished w/o ERROR, and output:[INDENT](hd0) /dev/sda 
(hd1) /dev/sdb

[/INDENT]When I re-booted into USB on EM725, I got some error messages scroll by (any way to freeze this or look up in a log later?), and then it ran a disk check (I looked into boot.log, and that seemed to report this as a routine 35x w/o a check - force? so just co-incidence I guess). It seemed to boot OK after that. On re-boot, the message flashed again, I caught some of it it looked *something* like:* File not found... LINUX B2 IMAGE... setup 0x0034...?????* Yet, it seems to boot fine after that (no disk checks on later boots). I ran another boot script, booted from the USB drive.

5) On the PC901, I get the GRUB R[FONT=Verdana]ESCUE prompt when selecting the USB drive... slightly diff[/FONT]erent this time (partially expected, since I re-parted the 4GB SSD).  I get:
[FONT=Arial]
[/FONT][FONT=Arial](hd0) (hd0,3) (hd0,2) (hd0,1)
(hd1)   << assume this is 4GB int SSD, seems 'normal' now, since I re-parted as one
[/FONT][FONT=Arial](hd2)  [/FONT]   [FONT=Arial]<< assume this is 16GB int SSD, why no 1,1 (swap) and 1,5 (my /home logical partition)?[/FONT]
 

[FONT=Arial]And after that, it says* "error: no such disk"* (I did not get THAT before!)[/FONT]

[FONT=Verdana]set command still refs to (hd0,5). Attempts to go through that set procedure fail at the later steps when I try to access anything in the directory, with 'partition not found'....
[/FONT]
[FONT=Verdana]And recall that he PC901 now has GRUB 1.98 (since my re-part and re-install with USB_LIVE 10.04). It had GRUB 1.97~beta4 previous to this. I guess this tells me that when an installer sees GRUB2, it just re-runs the install, but it does not actually re-install GRUB2 itself. But with a fresh partition, it installs GRUB2 from the installer - right?
[/FONT]
[FONT=Verdana]Are we having fun yet? heh-heh ;)[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]OK, so I will post (code tags) all those before/after bootscript results if anyone is interested, but I am wondering if this is a wild goose chase, and just some odd anomaly. Recall that the original problem was that I installed to the USB, and avoided the 'Advanced" tab, modifying GRUB on my internal and making it unbootable w/o the USB drive attached. I did a slew of things to attempt to fix that, so maybe that sequence did something really odd that will never be replicated in our lifetimes? Still seems strange to me  that a GRUB reinstall does not repair it.[/FONT]

[FONT=Verdana]
So, if there is not much interest in hunting down the root, I am thinking of the following, and would really appreciate feedback:

A) (optionally) Reinstall GRUB2 on my USB from my 10.04USB LIVE to get 1.98, just in case 1.97~beta4 has some funny stuff.

B) Repartition my USB drive. Some options here:
[/FONT][INDENT]Well, I really would like the ability to eventually have multiple UBUNTU installs on this drive, and the ms-dos partitioning seems rather limiting, since I really want a separate partition for my /home. I don't even know if you can have multiple installs as logical partitions, or if that confuses things (I think it would confuse _me_). In my readings, I came across the GUID/GPT partition format - this sounds so much more flexible, and I do almost zero with Windows anyway (I just kept it on my EM725 as a just in case, I'm a mac guy). I'm assuming that I didn't initially see much on GPT, as most people are coming from Windows on a single drive? Other than that, it seems like the way to go (and the future?).

It looks like one can actually re-do an ms-dos as a GPT, I figure I could try this for the USB, maybe this would even clean up whatever is going on with my boot issues. If not I'll do a complete wipe. I will be starting a new thread looking for partitioning advice before I proceed, as there is so much I do not know.

[/INDENT]So let me know - and just to be clear, I will continue to pursue this on the current installs if you people are gaining anything from it, but if not, and a repartition seems in order to get it working, I'm ready.

Thanks so much for all the assistance, I'm starting to get some ideas now to help out with the documentation which might help people like me avoid some of these problems from the start
 - NTL2009

---

### Post by oldfred on 2010-07-15
I have several Ubuntu installs & /home in extended partitions on my sdc drive.

To understand gpt a little more I converted my sdb to gpt and did an install to my 16GB USB as gpt. Both booted the gpt Ubuntu installs but I did not fully use them.
It seemed to work ok, I did create the bios_grub partition on both for grub to have room. But ..

I was trying to help another user who had gpt on one drive and MBR on the other and he could not boot the MBR drive from the gpt grub menu.
I said, oh it must work my systems seems ok and shows my XP on sda and Ubuntu installs on sdc and went to test.
They already have a fix and later I found in my own notes the same info from meierfra. early this year that I had forgotten since then I did not have gpt. 
GRUB_PRELOAD_MODULES="part_msdos"
 See:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)
The fix is in Maverick but they had me manually add part_msdos to 40_custom per the bug to  boot MBR (msdos) partitions from gpt boot.

---

### Post by bwallum on 2010-07-15
I've just finished going around the houses trying to get a usb drive to boot up from any machine capable of booting from a usb drive.

What I did was to create a menu entry in a file that I called 05_USBboot. It sits alongside the default /etc/grub.d/ file set. I then made all default except 00_header as non executable. That ensured I get a single menu entry. My 05_USBboot file is:> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'USBboot Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
insmod ext2
search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52
linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro   
initrd    /boot/initrd.img-2.6.32-24-generic
}The UUID reference is the partition UUID that /boot/grub sits on. You can find this info with ```
sudo blkid
```When I first ran into the grub rescue> prompt I used ```
insmod normal
normal
``` at the prompt and booted into the USB drive ok. I then ran ```
sudo update-grub
```All's now ok and the external USB drive will boot any machine (tried so far) that is capable of being booted from a USB drive.

I elected to leave the 00_header file as I thought it would be best left unchanged so that when updates came along I didn't have to remember customisation. 

I do have to remember to change the linux and initrd lines though, as new kernels come along.

Partitioning using msdos style partitions does not give me any issues. I have ext4 partitions alongside fat32 to keep the drive storage flexible across machines with different os's.

I guess there's a million and one ways to cut grub files but at least I have found one that I think I understand. Good luck with yours!

Bob

---

### Post by NTL2009 on 2010-07-15
Thanks again for this latest round of feedback. I am going to mull this over for a while, and maybe do some more reading before I proceed. But it occured to me, maybe, just to be absolutly clear, I should go back to square one for a moment, just in case my expectations are just not meeting with reality, and I've got lost in the fog of problems I created by allowing GRUB to be modified on my internal drive during the first install of the USB HDD:

**SQUARE ONE**: Is it reasonable for me to expect that:

1) If I correctly install UBUNTU onto this USB HDD, and move it from one computer to another, I will be able to boot from it OK with nothing more than selecting it as the boot device from the BIOS (hitting ESC or F12 as needed on the booting computer, and seeing the USB drive appear as  a choice, and selecting it)?

2) 'Correctly install' means select that "Advanced tab" and select the USB HDD device, so that MBR/GRUB2 et al are properly configured to boot this drive on other computers.

3) If I do the install correctly, I should not need to do anything further to any drive or to the computers that I wish to boot it on. Assuming those computers can boot from USB drives (most 'modern' BIOSs?). No file editing, no re-install of GRUB, etc. ?

I'm assuming all this stuff I've been doing is because of the initial problem I had, and subsequent attempts at fixes, but maybe I'm confused at this point, and this editing is an expected requirement to boot on different setups? I hope that is not the case, but if it is I need to accept it and understand this further.

My impression is that I should not need to do anything, as my USB_LIVE sticks boot just fine, and I don't do anything other than select the device when it appears on the BIOS list (after an ESC or F12 as required).

**bwallum** - just re-reading your post - So what I take from this is that your added file "05_USBboot" would go into  /etc/grub.d/ of the root directory that I wish to boot (partition 5 of my USB drive in my case, using my UUIDs & kernel name). And I'm guessing that this (after running the other commands to update-grub)  would 'force' GRUB to be aware of that kernel name and associate the proper UUID to it.  So that for whatever reason it does not find them now, this gets the info there regardless? Rather than 'discovering' the relationships, we are just 'telling them'?

Is my understanding even half-way close? 
 

-NTL2009

---

### Post by bwallum on 2010-07-15
> **NTL2009 said:**
> Thanks again for this latest round of feedback. I am going to mull this over for a while, and maybe do some more reading before I proceed. But it occurred to me, maybe, just to be absolutely clear, I should go back to square one for a moment, just in case my expectations are just not meeting with reality, and I've got lost in the fog of problems I created by allowing GRUB to be modified on my internal drive during the first install of the USB HDD:

SQUARE ONE: Is it reasonable for me to expect that:

1) If I correctly install UBUNTU onto this USB HDD, and move it from one computer to another, I will be able to boot from it OK with nothing more than selecting it as the boot device from the BIOS (hitting ESC or F12 as needed on the booting computer, and seeing the USB drive appear as a choice, and selecting it)?

Yes. You can select it through editing the cmos (or BIOS, technically it's the EEPROM that holds the info that POST checks, not the BIOS chip per se, so consider cmos and BIOS to be interchangeable terms when people talk about BIOS Setup) with SETUP or you can select it from an alternative boot menu (F9, F11 etc depending upon your motherboard) PROVIDING that the BIOS of any pc you want to use it on can support booting up from a USB device.

> 2) 'Correctly install' means select that "Advanced tab" and select the USB HDD device, so that MBR/GRUB2 et al are properly configured to boot this drive on other computers.Let's say you set up your USB external drive initially on a machine that has two internal hardrives. You install Ubuntu with a live cd. You choose the drive you want to install it on (simple) and install Ubuntu to the whole of the drive. When the install process writes grub2 to the USB MBR it thinks it is writing to hd2,1.

If you want to do something more clever then use the advanced tab and set up as many partitions as you like, subject to a limit of 4 primary partitions and general advice is no more than 12 total, the others being logical partitions. You set up an extended partition first to 'house' the logical partition.

If this gets a bit too complicated (it does for me) then just install Ubuntu to the whole drive (simple) and don't go near the advanced button....because you can subsequently use gparted to make additional partitions and by using gparted you are unlikely to commit errors to disk, gparted won't let you.```
sudo apt-get install gparted
```if you don't already have it.

All further setup and folder comments refer to USB external drive: Back to the MBR. Grub2 installs to it and has some preset variables loaded there. You can see what these variables are. When you get to the Grub2 menu press 'c'. That will give you a command line. This is Grub's command like. Type 'set' without the quotes and you will see what variables are set.

The main thing that I have learnt is that no matter what the 'set root=' command says, Grub2 will use UUID in preference. So don't worry if the root variable doesn't look right. That can be over-ridden. I still have the 00_header file declaring that root=(hd3,1) but rather than tweak the default 00_header file you can tell Grub2 the UUID of the partition you really want Grub2 to use.

That is what I did in my 05_USBboot file.

You've probably worked out that when update-grub is run it looks at all the files in the etc/grub.d/ folder and processes them in numerical order, 00_header, 10_linux, etc and writes the grub.cfg file that Grub2 subsequently picks up and runs at boot to create the Grub2 menu. You just write your own file, (copy 40_custom as a template) make sure it is executable (right click on file, check box under Properties) and after running update-grub you have created your own Grub2 menu entry which includes the instruction to use the image and kernel on the USB drive partition, using UUID to identify it. You can check the commands under the menu entry at boot time by selecting the Grub2 menu line and pressing the 'e' key.

> 3) If I do the install correctly, I should not need to do anything further to any drive or to the computers that I wish to boot it on. Assuming those computers can boot from USB drives (most 'modern' BIOSs?). No file editing, no re-install of GRUB, etc. ?That's right.

> I'm assuming all this stuff I've been doing is because of the initial problem I had, and subsequent attempts at fixes, but maybe I'm confused at this point, and this editing is an expected requirement to boot on different setups? I hope that is not the case, but if it is I need to accept it and understand this further.

My impression is that I should not need to do anything, as my USB_LIVE sticks boot just fine, and I don't do anything other than select the device when it appears on the BIOS list (after an ESC or F12 as required).I don't know your hardware unfortunately so couldn't be much help to you.> bwallum - just re-reading your post - So what I take from this is that your added file "05_USBboot" would go into /etc/grub.d/ of the root directory that I wish to boot (partition 5 of my USB drive in my case, using my UUIDs & kernel name). And I'm guessing that this (after running the other commands to update-grub) would 'force' GRUB to be aware of that kernel name and associate the proper UUID to it. So that for whatever reason it does not find them now, this gets the info there regardless? Rather than 'discovering' the relationships, we are just 'telling them'?Partition 5 makes me a little nervous because I am half aware of the 4 primary partition limit and have no idea how Grub2 works on a logical partition. I simply don't know enough to give you a definitive, I'm just timidly waving a little flag here. You otherwise guess correctly, we tell Grub2 the UUID to use and this overrides the 'set root='(hdX,Y)' command. Remember Grub2 is beta too, so things can change.

> Is my understanding even half-way close?No, it's as close as you can get without being there...I can hear the penny drop from here about now....

On the road remember the grub rescue escape and allow time for the USB drive to boot. It can be slower than booting from an internal drive but once up it flies.

EDIT
Another caveat - use 32 bit on the USB drive. It will take 64bit but then you will only be able to boot on 64 bit machines. By using 32 bit Ubuntu you can boot on 32 and 64 bit machines.


-NTL2009[/QUOTE]

---

### Post by NTL2009 on 2010-07-16
Thanks **bwallum** for all that info. I will take some time to absorb all that, but I share your 'nervousness' over those logical partitions towards the end of a 500GB drive. I suspect they are 'funny' in a way my EM725 deals with, but the PC901 does not.

But while I'm absorbing that, I decided to try a little experiment that seemed to have little to lose, and might provide a little insight. My 1st partition on that USB disk is a primary one, and I hadn't put anything there yet, so I:

1) Installed 10.04 onto partition 1 (booted into LIVE_USB on my PC901). I chose 'manual partition' from the installer, but just pointed it to that partition (sdc1 in this case).

2) First interesting thing was, MIGRATION ASSISTANT. I probably failed to mention this, but on the recent re-installs, it didn't report any of the other OS installs as available to migrate from.  This time, it 'saw' both users on the install on the PC901 internal _and the one user from partiton 5 of the USB HDD_. I selected my account on the PC901 to migrate from.

3) Install went fine, and on reboot the GRUB menu showed both this new  p1 install and the p5 install (no GRUB Rescue prompt - yeah!). And yes - **the new p1 install booted on the PC901!** Although, nothing seemed to be migrated to it.

4) So I re-boot to try booting p5 since it now displays in the menu - no dice. A string of                                   [FONT=Arial]error: out of disk"[/FONT]
 [FONT=Arial]and then one...........................[/FONT]
 [FONT=Arial]error: no such device: 4b2cdf......0049 << my UUID of p5[/FONT]


5) 'Press any key to return'  to the GRUB menu from here - nothing boots. But a forced power down & restart, and I can choose either the internal OS, or the p1 OS of the USB HDD both OK. But once I choose the p5, all are un-bootable until I force a power cycle.


6) On the EM725, I can boot both the new p1 and the 'old' p5 (which always booted fine on the EM725).


Differences: 


A) One primary partition for the new p1 install versus 3 logical partitions for the p5 install ( I don't think this matters, it seems common and recommended to use a separate partition for /, /home & swap, and with msdos partition limits, I assume logical partitions would be common).


B) The p1 install is closer to the beginning of the disk - perhaps the PC901 has trouble with logical partitions higher up on the disk?


C) Maybe my previous 'fixes' to get my EM725 booting again, hosed up the p5 in some odd way that the PC901 does not like?


So there it is, progress of a sort. I'll run a follow up post to talk about direction from here.


-NTL2009

---

### Post by NTL2009 on 2010-07-17
Just a little more info here - 

Now that I can boot the USB HDD on the PC901, I can report that when I interrupt GRUB with 'c', I get the same kind of results from the **ls** commands as I got from the GRUB Rescue prompt before. It still doesn't 'see' the 5,6,7 partitions, and I can't **ls** into the directories under them.

But I _can_ **ls** into the 1st partition of the USB HDD (the new one that now boots properly) and list everything as expected.

Hitting the 'c' prompt when booted on the EM725 lets me **ls** all these places with the results I expect. And it boots all of them.

I guess this is exactly what I should expect, but being able to see it this way is making things clearer to me. The PC901 just isn't 'seeing' those logical partitions, so it can't boot into a system there. But it can and does see the 1st partition, and boots fine from there.

So I'm about ready to re-part that USB HDD. Leaning to GPT. Install systems in the lower #'s, keep the higher for data. And hope the PC901 'sees' everything fine.

Thoughts?  -NTL2009

---

### Post by bwallum on 2010-07-17
Difference in BIOS capability on both machines probably accounts for boot/no boot discrepancies. Right on for installing OS's on primary partitions for avoidance of quirky behaviour.

I think you've become an expert! You'll have to write a HowTo to let others know how to install Grub2 on a USB harddrive so that it'll boot on any capable machine.

---

### Post by NTL2009 on 2010-07-17
> **bwallum said:**
> 
I think you've become an expert! You'll have to write a HowTo to let others know how to install Grub2 on a USB harddrive so that it'll boot on any capable machine.

Thank you, but I'm thinking that maybe your standards for 'expert' label are much lower than mine! ;)

But I do think I'm making steps in getting enough background to help fill out a few missing pieces of the current documentation, and hope to do that soon.

> 
Difference in BIOS capability on both machines probably accounts for  boot/no boot discrepancies. Right on for installing OS's on primary  partitions for avoidance of quirky behaviour.

Well, as part of the learning process, here is what I plan, as time permits...

1) Install 10.04 onto p2 of that USB HDD. Just to verify another install a bit higher up the drive.

2) Re-format that extended p4 as primary, and install 10.04 there, to test primary versus logical in that area of the drive.

3) Re-format p2 as extended, and install 10.04 to logical partitions there, to test  primary versus logical in that lower area of the drive.

4) Maybe repeat down to p1.

I suspect all of this will continue to point to the ASUS PC901. I'm also going to do further research on PC901 having trouble with higher areas of external drives. So far, I get so many generic boot/partition hits on a search, I have not found much specific to this yet.

But I think this will pin some things down for me, and I've gone this far, I'd like to have a little more understanding/closure before (if) I decide to re-part this as GPT and (hopefully) move on from this issue.

-NTL2009

---

### Post by NTL2009 on 2010-07-20
[FONT=Arial]An update - 

I installed to primary partition 3 of the USB_HDD, and I got the same results - GRUB2 on the PC901 would not 'see' the files there.[/FONT][FONT=Arial]
[/FONT] 
 [FONT=Arial]Same for my install on p2 primary. So I went ahead and deleted the extended partition #4; made it as primary, then changed p1 to extended with logical partitions for /,/home & swap. PC901 boots OK on p1 as primary OR extended.[/FONT][FONT=Arial]
[/FONT] 
 [FONT=Arial]So, the only common element is the PC901 seems to only boot from P1 of this USB_HDD.[/FONT]
 
 [FONT=Arial]When trying to boot p2, I get* no such device, cannot get C/H/S values; you need to load the kernel first... any key to continue.*[/FONT][FONT=Arial]
[/FONT] 
 [FONT=Arial]So I wonder -  p1 is 164GB, is this any limit for PC901 BIOS? (Well, I upgraded to 2103 BIOS from 1109 - no diff in boot)[/FONT][FONT=Arial]
[/FONT] 
 [FONT=Arial]Wish I had a third machine to try this on, but everything else in the house is Apple EFI. Not sure what the next best step is to sort this out, but I might try a 20GB partition for p1 just to see if p2 would be 'seen' then.[/FONT]

[FONT=Arial]-NTL2009
[/FONT]

---

### Post by Golem XIV on 2010-07-21
I'm sorry if this has been mentioned - I skipped over the 6 pages of technical stuff - but if you want to boot the same system on different computers why don't you set up a Live image on the external drive?  You could even make it persistant so that you can save files, install software, update, etc.

---

### Post by oldfred on 2010-07-21
Does the BIOS of [FONT=Arial]PC901 have a floppy set but you do not have floppy? That has been an issue with some BIOS. Review other BIOS settings to see if some thing related to drives is different.
[/FONT]

---

### Post by NTL2009 on 2010-09-09
Hello again - I finally got back to this after recently buying another 500GB USB ext drive that I could play with. I'm almost positive that it is the PC901 BIOS that is limited - it appears to me that the BIOS does not recognize partitions that start above roughly 128GB from the start.

With my new drive, I used a GPT partition scheme so I could create more than 4 primary partitions. All ext4 except swap:

P1 - 8GB; P2 - 30GB
P3 - 8GB; P4 - 30GB
P5 - 8GB; P6 - 30GB
P7 - 8GB; P8 - 30GB
P9 - 8GB; P10 - 30GB
P11 - 5GB swap
P12 - 100GB (data)
P13 - 180GB (data)

I did a fresh 10.4 install on each 8/30GB 'pair' with the 8GB as '/' and the 30GB as '/home', being careful to choose the ADVANCED button to put the bootloader on the external drive, and testing the boot on PC901 as I went. Results:

Install on P1/2 - boots fine.

Install on P9/10 - "Geom Error" after selecting the drive - no drop to grub, nothing. So I can't get to the P1/2 install anymore.

Install on P3/4 - Now I can boot into 3/4 and/or P1/2 (re-writing GRUB on the drive cleans the "Geom Error" up I guess), but attempting to boot into p9/10 gives something like "No such device, no such partition, you need to load the kernel first".

A little more poking under grub rescue, and I get 'Unknown File System" when I 'ls' p8 and above. I get normal responses on p1-7. And all these installs boot fine on my EM725.

So at this point, I'm not going to dig any deeper - I will just accept that the PC901 has this limitation. The good news is that as part of this process I learned about the GPT partitions, and that sure makes it easier to set up the many partitions I want for my systems, and it makes it easy to keep a bunch on the lower numbered sectors for booting my PC901, while I keep my EM725 bootable systems up in the higher sector areas.

**Thanks to all for helping out with understanding this,** I learned a lot along the way. If anyone would like me to try anything else, just for the learning experience I'll see if I can give it a try. But I'm ready to just accept it as is.

-NTL2009

---

### Post by oldfred on 2010-09-09
Did you create a bios_grub partition with the gpt partitioning?

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown


This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)



Legacy BIOS Issues with GPT
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

---

### Post by NTL2009 on 2010-09-10
> **oldfred said:**
> Did you create a bios_grub partition with the gpt partitioning?

I don't have anything in my notes, and I don't recall doing anything specific regarding setting up boot spaces and I am not using a separate /boot partition. I used GPARTED to do the partitioning.

It was my (weak) understanding that by default,  GPT provides a traditional MBR but also has some header space to provide expanded capability, so this is supposed to maintain compatibility with older boot processes (pre-EFI).

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

> MBR-based partition table schemes insert the partitioning information in the master boot record (MBR) (which on a BIOS system is also the container for code that begins the process of booting the system). In a GPT, partition table information is stored in the GPT header, but to maintain compatibility, GPT retains the MBR entry as the first sector on the disk followed by a primary partition table header, the actual beginning of a GPT.

This really isn't a problem for me at this point, as long as I know I can only install boot partitions on the first 128GB for the PC901, I can live with that. Of course, a real fix for the problem would add to my knowledge base on this stuff.

I'll have to study those links you provided later, got some other non-computer stuff going on for a few days.

Thanks - NTL2009

---

### Post by srs5694 on 2010-09-10
The "bios_grub" partition to which oldfred refers is a [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) which is a type of partition that's used by GRUB 2 on GPT disks to store data that resides in unallocated space after the MBR on MBR disks. Since GPT disks can't be relied upon to have unallocated sectors, GRUB 2 requires the use of a special partition for this function. Although it's supposed to be possible to boot using GRUB 2 on GPT disks without a BIOS Boot Partition, this isn't as reliable as booting with a BIOS Boot Partition. It's conceivable that you'd be able to boot from additional partitions if you added a BIOS Boot Partition to your system and re-installed GRUB 2; however, it's likely that the BIOS Boot Partition would have to reside in the early part of the disk, since GRUB would probably be using the BIOS to read it. Personally, I'm skeptical that adding this partition would improve your ability to boot beyond the BIOS limits, but I'm not positive of that.

You can also resort to the old technique of using separate /boot partition(s) that reside within the BIOS-accessible part of the disk. Once GRUB has loaded the Linux kernel and initial RAM disk, the kernel takes over and reads the rest of the disk without using the BIOS. Thus, putting the kernel, initial RAM disk, and boot-time GRUB configuration file, all of which are in /boot, on a separate partition early on the disk can overcome BIOS limitations.

---

