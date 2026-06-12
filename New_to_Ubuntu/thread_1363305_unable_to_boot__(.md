---
title: "unable to boot  :("
date: 2009-12-24
forum: New to Ubuntu
---

### Post by mighty mouse on 2009-12-24
Hi 
 
Please help me out.
I have an ACER laptop which has been dual booted with windows 7 and ubuntu 9.01.Yesterday when i switched on my laptop the screen kept on flickering between ACER start page and GRUB loading.It doesnt go further.
When i placed ubuntu's live cd...it got booted through it.I can access my ntfs partition as well as ubuntu's file system.My data and partitions are intact.
Is it a problem of MBR?
can you guys please help me to restore my laptop...
please!!

---

### Post by mapes12 on 2009-12-24
Boot into Ubuntu from the LiveCD, launch Firefox then go here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Download the boot_info_script to your Desktop. Once on your Desktop open a terminal (Applications>Accessories>Terminal) and run this command
```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your Desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the QUOTE button (4th from right on the forum toolbar) to place quote tags around the text. This info will give a clear picture of your set up and boot process. Someone can then have a look and try to help you out.

---

### Post by mighty mouse on 2009-12-24
> ============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc988c988

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden HPFS/NTFS
/dev/sda2    *     26,626,048    26,830,847       204,800   7 HPFS/NTFS
/dev/sda3          26,830,848   767,055,919   740,225,072   7 HPFS/NTFS
/dev/sda4         767,071,620   976,768,064   209,696,445   5 Extended
/dev/sda5         767,071,683   976,768,064   209,696,382  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 32.0 GB, 32015122432 bytes
1 heads, 32 sectors/track, 1954048 cylinders, total 62529536 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    62,529,535    62,521,344   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DAA41C49A41C2B11" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="921C18621C18441F" LABEL="SYSTEM RESERVED" TYPE="ntfs" 
/dev/sda3: UUID="24EADE87EADE5520" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="91c5f39c-abb4-4a1d-a783-3c9ba038edad" TYPE="ext4" 
/dev/sdb1: LABEL="" UUID="6515-B203" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/6515-B203 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda3 on /media/ACER type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set 91c5f39c-abb4-4a1d-a783-3c9ba038edad
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
    search --no-floppy --fs-uuid --set 91c5f39c-abb4-4a1d-a783-3c9ba038edad
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=91c5f39c-abb4-4a1d-a783-3c9ba038edad ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 91c5f39c-abb4-4a1d-a783-3c9ba038edad
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=91c5f39c-abb4-4a1d-a783-3c9ba038edad ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 921c18621c18441f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 24eade87eade5520
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
UUID=91c5f39c-abb4-4a1d-a783-3c9ba038edad /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 392.7GB: boot/grub/grub.cfg
 392.7GB: boot/initrd.img-2.6.31-14-generic
 392.7GB: boot/vmlinuz-2.6.31-14-generic
 392.7GB: initrd.img
 392.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 



Here it is...please help me out !!

---

### Post by oldfred on 2009-12-24
I do not see anything in the results.txt that look like a problem. 

If you start the liveCD and select use the hard drive does it boot? It may require a reinstall of grub2.

We have seen issues with software on HP and Dell that write bits into the MBR and since grub2 is slightly larger than grub legacy or the windows boot, there are conflicts.

Was this after being in windows and were you running anything specific?

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

Someone else was running Norton Ghost and that was causing a problem.

---

### Post by Zoot7 on 2009-12-24
If it were me I'd give re-installing Grub 2 a shot. Either that or a downgrade to Grub Legacy.
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by mighty mouse on 2009-12-24
I dont know if this might help in solving the problem:

when i type this command : sudo gedit /boot/grub/menu.lst   
Its empty/blank.

And sudo grub
>  grub not found !!

---

### Post by Zoot7 on 2009-12-24
> **mighty mouse said:**
> I dont know if this might help in solving the problem:

when i type this command : sudo gedit /boot/grub/menu.lst   
Its empty/blank.

And sudo grub
>  grub not found !!
That's because you're using Grub 2 instead of Grub legacy. Grub 2 doesn't use /boot/grub/menu.lst but uses /boot/grub/grub.cfg which is a shell script instead of a config file.
Also it doesn't provide you with the same prompt that Grub legacy did.
Have a read through the first link I posted, all the basics of Grub 2 are covered there including how to re-install it to the MBR (which'd be the first thing i'd try).

---

### Post by mighty mouse on 2009-12-24
i am confused...the result of fdisk was 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       47748   370112536    7  HPFS/NTFS
/dev/sda4           47749       60801   104848222+   5  Extended
/dev/sda5           47749       60801   104848191   83  Linux


Now how should i proceed.I should mount my linux distribution....then?

Can you please provide me the steps.

---

### Post by Zoot7 on 2009-12-24
> **mighty mouse said:**
> Can you please provide me the steps.
**[*HERE*]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")** :)
The only difference in your case is that /dev/sda5 is the one to use.
EDIT: Don't worry too much about editing the file /etc/default/grub too much, if you had a dual boot between Vista and Ubuntu that should be okay.

---

### Post by mighty mouse on 2009-12-24
> **Zoot7 said:**
> **[*HERE*]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")** :)
The only difference in your case is that /dev/sda5 is the one to use.
EDIT: Don't worry too much about editing the file /etc/default/grub too much, if you had a dual boot between Vista and Ubuntu that should be okay.


[LIST]
[*]Now you need to edit the **/etc/default/grub** file to fit your system 
[/LIST]
[FONT=monospace]>> fit your system?
what should i do now? :confused: how should i edit this!
i had a dual boot with windows 7 and ubuntu
Really ....thanks for your patience in helping me out !!!
[/FONT]

---

### Post by Zoot7 on 2009-12-24
> **mighty mouse said:**
> [LIST]
[*]Now you need to edit the **/etc/default/grub** file to fit your system 
[/LIST]
[FONT=monospace]>> fit your system?
what should i do now? :confused: how should i edit this!
i had a dual boot with windows 7 and ubuntu
Really ....thanks for your patience in helping me out !!!
[/FONT]
Don't worry about it, if you had a dual boot with Ubuntu and Vista already then you should be good to go as far as the configuration in that file. :)

---

### Post by mighty mouse on 2009-12-24
> **Zoot7 said:**
> Don't worry about it, if you had a dual boot with Ubuntu and Vista already then you should be good to go as far as the configuration in that file. :)


All right...let me try!
Will keep you posted.  :)

---

### Post by ibuclaw on 2009-12-24
Hmm... rather than installing / configuring any odd piece of software, why not discover the root of the problem.

Has booting Ubuntu worked before?
Were you asked to do any updates on the day before it started failing?

Regards
Iain

---

### Post by mighty mouse on 2009-12-24
> **Zoot7 said:**
> Don't worry about it, if you had a dual boot with Ubuntu and Vista already then you should be good to go as far as the configuration in that file. :)


successfully booted into my ubuntu partition.....  :)
Thanks a llot !!!

When i restarted my laptop ...i couldn't find my windows 7 partition on the boot list.
what shouldi do now to get my windows partition back !!

---

### Post by bicyclerider on 2009-12-24
I tried to install the Ubuntu 9.10 Karmic Koala this was on a hrd drive that had a previous problem of not loading grub and the company replaced the hd with a smaller drive. Regardless I downloaded the image and burned the install to cd.
Ran the cd after changing the boot sequence to CD drive. Installed as a oem and that allowed me to wipe out the previous install of 8.0 ubuntu.
I ran the script as you described in the post and the results are as follows
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0e23e80

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   769,384,979   769,384,917  83 Linux
/dev/sda2         769,384,980   781,417,664    12,032,685   5 Extended
/dev/sda5         769,385,043   781,417,664    12,032,622  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="28d11412-5532-476b-a6ae-2aa2decc306f" TYPE="ext4" 
/dev/sda5: UUID="dda8ab83-33b0-4e4f-9928-3b9255ad3ef6" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/28d11412-5532-476b-a6ae-2aa2decc306f type ext4 (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 28d11412-5532-476b-a6ae-2aa2decc306f
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 28d11412-5532-476b-a6ae-2aa2decc306f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=28d11412-5532-476b-a6ae-2aa2decc306f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 28d11412-5532-476b-a6ae-2aa2decc306f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=28d11412-5532-476b-a6ae-2aa2decc306f ro single 
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
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=28d11412-5532-476b-a6ae-2aa2decc306f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dda8ab83-33b0-4e4f-9928-3b9255ad3ef6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz


So from this point I'm learning command line verbage and will try to resolve this issue.
If any other info is required I will try to complete this quickly.

---

### Post by Zoot7 on 2009-12-24
> **mighty mouse said:**
> successfully booted into my ubuntu partition.....  :)
Thanks a llot !!!

When i restarted my laptop ...i couldn't find my windows 7 partition on the boot list.
what shouldi do now to get my windows partition back !!
Run this command to generate a new grub.cfg, it should find the Windows 7 install.
```
sudo update-grub
```

---

### Post by mighty mouse on 2009-12-24
> **Zoot7 said:**
> Run this command to generate a new grub.cfg, it should find the Windows 7 install.
```
sudo update-grub
```




:):guitar::)

I guess you know......  :) 
I got back my windows and linux partition.
Thank you very much !!! .......  Thanks !!    :)

---

### Post by Zoot7 on 2009-12-25
> **mighty mouse said:**
> :):guitar::)

I guess you know......  :) 
I got back my windows and linux partition.
Thank you very much !!! .......  Thanks !!    :)
Awesome! You're welcome! :)

---

