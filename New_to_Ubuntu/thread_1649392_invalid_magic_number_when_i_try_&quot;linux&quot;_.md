---
title: "invalid magic number when i try &quot;linux&quot; command to boot after an upgrade"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by asaaki on 2010-12-20
Hi,

I'm not sure if this is the right place to be posting this.
I'm not too good at linux, just installed ubuntu 9.10 once but continued using Windows. But then Windows crashed and since I never had the time to fix it I just switched to Ubuntu to run some urgent apps.

I was on ubuntu as usual, when i got some "install updates" message and I just went ahead and said okay, install. I never really saw what the upgrades were, but at one point it said some updates could not be found or installed or something, ignore and continue with the rest? i said fine, then it restarted, but now i end up on the grub interface. It's Grub 1.97 beta.

I've tried out the 7 steps of the grub rescue boot procedures, and discovered that (hd0,2) on my machine has my windows folder.

I'm a Wubi user and so I tried to follow instructions on the Grub Rescue Prompt Megathread [[http://ubuntuforums.org/showthread.php?t=1594052]](http://ubuntuforums.org/showthread.php?t=1594052]).

Everything's fine till Step 5. I run 
** insmod (loop0)/usr/lib/grub/i386-pc/linux.mod**

and get 'linux' already loaded.
Then, no matter what combination of sdXY I try in
**linux /vmlinuz /dev/sdXY ro**
I get:
**invalid magic number**.

And 
**initrd /initrd.img**
gives me "You must load the kernel first".

Not sure what to do? My Windows has a boot problem as well so I'm really stuck here.

---

### Post by asaaki on 2010-12-20
I've been searching around and apparently I can get the job done by replacing certain files in C:

However I don't have access to do that since my Windows is also unbootable.

---

### Post by oldfred on 2010-12-20
Look at this link, I thought they had fixed it in the newer verisons.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by asaaki on 2010-12-20
I checked the link out. "sudo" doesn't isn't working on my grub, neither is "mount". 


As per the old link 
[[http://ubuntuforums.org/showthread.php?t=1594052]](http://ubuntuforums.org/showthread.php?t=1594052])
loading linux simply wouldn't work, so then I tried a specific  kernel version as mentioned, and it finally worked, no more magic number issue. 

Now when I boot, it goes through the following:
[b]Begin: Mounting root file system... ...
Begin: Running /scripts/local-top... ...
Done.
Begin: Waiting for root file system... ...
Done.
Gave up waiting for root device. Common problems:
 -Boot args (cat /proc/cmdline)
   -Check root delay = (did the system wait long enough?)
   -Check root=(did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to shell!
[/b]

Then I end up in BusyBox.

So I tried searching around how to deal with this. Apparently I should change menu.lst or /etc/default/grub, but neither "sudo" nor "e" nor "vi" are working. How can I edit the file?

---

### Post by oldfred on 2010-12-20
Lets see if it is a boot issue first. Or it may be something after grub loads. If you hold shift key down from BIOS until menu, do you get a grub menu?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by asaaki on 2010-12-20
I'm getting a grub prompt by default, whenever I select Ubuntu from the dual boot, that's the only interface I get. Is that what you mean by the grub "menu"?

I did come across this boot info script but as I mentioned earlier, sudo or su aren't working. After loading linux, I graduated from the "sh-grub" prompt to a "initfms" prompt (or something similar), but I can't seem to find an alternative to the "su" or "sudo" command, and I'm still on a black-and-white prompt screen.

---

### Post by oldfred on 2010-12-20
You can use the liveCD to download and run the boot info script. If grub is failing, you will not get a menu. But if you only have Ubuntu on your system, then grub never shows a menu and starts Ubuntu. Errors then can be either before grub or after grub and it sometimes can be hard to tell. Boot script helps us evaluate the grub portion of boot errors.

---

### Post by asaaki on 2010-12-21
Thanks! I downloaded liveCD and booted from USB. Ran the script, here's the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

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
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847  de Dell Utility
/dev/sda2    *        224,910   312,689,159   312,464,250   7 HPFS/NTFS
/dev/sda3         312,689,160   468,921,284   156,232,125   7 HPFS/NTFS
/dev/sda4         468,921,285   625,137,344   156,216,060   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16131293184 bytes
25 heads, 25 sectors/track, 50410 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    31,506,431    31,504,384   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       f9e0ecaf-c1d9-4f2e-a288-15354c9edb07   ext4                                     
/dev/sda1        07D7-0A11                              vfat       DellUtility                   
/dev/sda2        BE387A9E387A54FD                       ntfs                                     
/dev/sda3        A8BC87AEBC87761A                       ntfs                                     
/dev/sda4        5A5CA9CC5CA9A2ED                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3433-3231                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/5A5CA9CC5CA9A2ED  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/A8BC87AEBC87761A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set be387a9e387a54fd
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set be387a9e387a54fd
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set be387a9e387a54fd
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set be387a9e387a54fd
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set be387a9e387a54fd
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   5.0GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.31-14-generic
   5.1GB: boot/initrd.img-2.6.31-22-generic
   1.5GB: boot/vmlinuz-2.6.31-14-generic
   4.6GB: boot/vmlinuz-2.6.31-22-generic
   5.1GB: initrd.img
   1.6GB: initrd.img.old
   4.6GB: vmlinuz
   1.5GB: vmlinuz.old


```

---

### Post by bcbc on 2010-12-21
If you're on Ubuntu 9.10 you need to replace the wubildr if you haven't already: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by asaaki on 2010-12-22
Thanks so much! i just replaced wubidr and it worked like a charm! :KS

---

