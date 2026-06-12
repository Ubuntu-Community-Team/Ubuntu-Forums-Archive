---
title: "External drive boots to grub&gt; command line"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by Grratch on 2010-12-02
I've installed Ubuntu 10.10 on an external USB drive. Had issues earlier with it not even doing anything but displaying a black screen with a cursor - nothing else happened.
 
I tried some instructions from an earlier post to load the external HD (sdb drive, sdb1 partition). From LiveCD, entered commands:
 
```
sudo mount /dev/sdb1 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
 
Now when I attempt to boot to the external HD, I get a promt that looks like "grub>". What do I do next?
 
 
Thanks in advance for any help.

---

### Post by wilee-nilee on 2010-12-02
Lets see the bootscript again, boot the live ubuntu cd and run the script in my signature. Click on the # in the reply window for code tags, and paste the text between. Make sure the HD is plugged in.

---

### Post by garvinrick4 on 2010-12-02
Do as previous post indicates and will be taken care of quickly: Without the script
no one can tell where the problem lies.

You are going to have to download this script to your DESKTOP and then  run the code given below and will put a file called RESULTS on your  desktop. Copy and paste it
to this thread of yours. After pasted you can highlight whole thing is long and hit the little
# sign in right of the Message box and will put in nice little box to be read easily.
Only takes 30 seconds or so. Users will be able to find any problem right away.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by Grratch on 2010-12-02
Ok, here are the results of the boot info script.  Thanks again for your help.
                   
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,787,924    16,787,862  1b Hidden W95 FAT32
/dev/sda2    *     16,787,925   798,205,589   781,417,665   7 HPFS/NTFS
/dev/sda3         798,205,590 1,953,520,064 1,155,314,475   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   939,911,167   939,909,120  83 Linux
/dev/sdb2         939,913,214   976,771,071    36,857,858   5 Extended
/dev/sdb5         939,913,216   976,771,071    36,857,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C1CB6951CB66A22                       ntfs       RECOVERY                      
/dev/sda2        904254E64254D298                       ntfs       WIN7                          
/dev/sda3        C07EDA877EDA759E                       ntfs       WIN7                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c4e8db4e-5242-468c-a2ce-bd1f458ad838   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        48f8900b-4579-4093-8fe6-79bd46a7cf5c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c4e8db4e-5242-468c-a2ce-bd1f458ad838 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c4e8db4e-5242-468c-a2ce-bd1f458ad838 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c1cb6951cb66a22
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 904254e64254d298
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=48f8900b-4579-4093-8fe6-79bd46a7cf5c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  55.9GB: boot/grub/core.img
 309.5GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-23-generic-pae
  55.9GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.1GB: initrd.img
  55.9GB: vmlinuz
```

---

### Post by garvinrick4 on 2010-12-02
#Looks good to me, just go into gparted and right click on sdb1 and go to manage flags right click on and add a boot flag.
If gparted not in System/administration to gparted then add.
# Like you did before for safe measure add code below:
```
sudo apt-get install gparted
``````
sudo mount /dev/sdb1 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
``````
sudo umount /mnt
``````
sudo reboot
```Go into sdb ubuntu install and:
```
sudo update-grub
```#os-prober will now go and fetch all installs and put them in grub2 menu.
When this is booted first will show all installs on both sda and sdb.
# When sda is booted first will just boot straight into Windows install
#Edit to boot into sdb line 6

---

### Post by Grratch on 2010-12-02
Ok,
1. Added the boot flag to sdb1 via gparted.
2. Ran each of the lines of code above in order

The first five lines of code gave me no troubles, however, after reboot to the external HDD, it still takes me to the **grub>** prompt just as it did before.  Also, I assume that for the instructions in #6, you meant "Go into [COLOR=Red]sdb1[/COLOR] on HDD" and not sda1?

Just to be thorough, here is the boot script info after performing the actions above:

Thanks for your patience.

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,787,924    16,787,862  1b Hidden W95 FAT32
/dev/sda2    *     16,787,925   798,205,589   781,417,665   7 HPFS/NTFS
/dev/sda3         798,205,590 1,953,520,064 1,155,314,475   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   939,911,167   939,909,120  83 Linux
/dev/sdb2         939,913,214   976,771,071    36,857,858   5 Extended
/dev/sdb5         939,913,216   976,771,071    36,857,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C1CB6951CB66A22                       ntfs       RECOVERY                      
/dev/sda2        904254E64254D298                       ntfs       WIN7                          
/dev/sda3        C07EDA877EDA759E                       ntfs       WIN7                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c4e8db4e-5242-468c-a2ce-bd1f458ad838   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        48f8900b-4579-4093-8fe6-79bd46a7cf5c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c4e8db4e-5242-468c-a2ce-bd1f458ad838 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c4e8db4e-5242-468c-a2ce-bd1f458ad838 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c1cb6951cb66a22
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 904254e64254d298
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=48f8900b-4579-4093-8fe6-79bd46a7cf5c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  55.9GB: boot/grub/core.img
 309.5GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-23-generic-pae
  55.9GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.1GB: initrd.img
  55.9GB: vmlinuz

```

---

### Post by garvinrick4 on 2010-12-02
#We are going to mount the drive get into root and install grub, update grub and while we are there just check dependencies and update and upgrade system.
#Use live cd and get internet connection and the copy and paste.



```


[CODE]sudo mount /dev/sdb1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt 
``````
grub-install --recheck --root-directory=/mnt /dev/sdb
``````
update-grub
```Now see if that updated grub and showed the grub menu items.
```
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
exit
```                    ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```[/code]Now boot into sdb drive. It should work if booting into sdb, it all looks fine to me.

---

### Post by oldfred on 2010-12-02
Script looks ok to me.

If you get to a grub> prompt can you manually boot?

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

---

### Post by Grratch on 2010-12-02
**garvinrick**:  Entered all of the code as you listed.  Still getting the grub> prompt when booting to sdb1.  Was I supposed to be reporting anything to you during any of the steps above?
**oldfred**: Is your code a contingency in case the previous upgrade/install didn't work?  Should I try that next?

Sorry - this is probably frustrating for you guys.  Thanks for sticking with me on this.

---

### Post by garvinrick4 on 2010-12-02
> **Grratch said:**
> **garvinrick**:  Entered all of the code as you listed.  Still getting the grub> prompt when booting to sdb1.  Was I supposed to be reporting anything to you during any of the steps above?
**oldfred**: Is your code a contingency in case the previous upgrade/install didn't work?  Should I try that next?

Sorry - this is probably frustrating for you guys.  Thanks for sticking with me on this.
When you entered update-grub did you get a report of kernels installed? Like 2.6.35-23 for instance:
Did it update and upgrade? Could you see a list of repositories on screen?

---

### Post by Grratch on 2010-12-02
I can't remember whether I got a report of kernels installed with the update-grub command.  It did appear to update and upgrade as it took about 30 min while it was downloading, unpacking, and installing stuff.

---

### Post by garvinrick4 on 2010-12-02
Everything is working fine? Why it will not boot is strange, your grub.cfg file looks so good
to me. 
#oldfred or anyone that can help this out jump in. Maybe you all can see something I do not see.
# hang on a minute and let someone else chime it, it has to be something silly that I cannot see.

---

### Post by drs305 on 2010-12-02
Is your BIOS a bit old? I see that most of the G2 files are early in the disk but currently the grub.cfg file is at 300GB. Some older BIOS cannot see past 137GB. Your OS can, so it would appear normal *once you boot*.

You can look at your BIOS settings and see what size it reports your external drive as. You may have an option for 'large drives' or something similar. A BIOS update may also be available, although I wouldn't do this unless you were pretty sure this was the issue and there wasn't a setting to change in your current BIOS setup.

Another thing you can try:
From the Grub2 menu, press "c" to get to the grub prompt (if you aren't already there).

Use the "ls" command to locate your Ubuntu drive, and then check to see if you can find the grub.cfg file. It should be:
```
ls (hd1,1)/boot/grub
```

If you find it, type this and press ENTER (Change hd1,1 to the correct values if different). It should boot, if not press CTRL-x:
```
configfile (hd1,1)/boot/grub/grub.cfg
```

---

### Post by Grratch on 2010-12-02
Alrighty then, here we go:

_BIOS_

[LIST]
[*] **Info**:  American Megatrends (?) Version 0221; Build Date 11/3/09 (Note: in the BIOS Tools menu, there is an option for ASUS Easy Flash 2 utility)
[*]**External Drive Size**: Not reported anywhere in BIOS, but the USB drive I am using is a 500GB device.
[*]**Settings**:  I don't see an option for "large drives", however,  diving in deep, I get to the USB Mass Storage Device Configuration  menu.  It is currently set to AUTO.  Here is what BIOS says about  this:  "[COLOR=DarkGreen]*If AUTO, devices less than 530MB will be emulated as floppy and  remaining as hard drive. Forced FDD option can be used to force a HDD  formatted drive to boot as FDD (Ex. ZIP drive).*[/COLOR]"
[/LIST]
  _Results from grub> prompt commands_

[LIST]
[*]**ls**:  (hd0) (hd0,msdos1) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1)
[*]**ls (hd1,1)/boot/grub**:  error: file not found
[/LIST]
Hope this is helpful.  Thanks for looking at this.

---

### Post by oldfred on 2010-12-02
Is grub and script drives reversed?
Your ls shows hd1,1, 1,2, & 1,3 but sdb only has hd0,1 or sdb1 has  sdb2 is extended and sdb3 is swap. And sda has the three valid windows partitions.

Try 
**ls (hd[COLOR=Red]0[/COLOR],1)/boot/grub**

---

### Post by Grratch on 2010-12-03
Ran **ls (hd0,1)/boot/grub**.  Something happened this time as it vomited out an entire screen of what appeared to be file names.  Things such as: *font.mod*, *fshelp.mo*d,* command.lst*,* crypto.lst*, *kernel.img*, etc. ...

The very last filename in the list was* grub.cfg*

Sounds like we're getting closer?

---

### Post by oldfred on 2010-12-03
Back to my post #8 on manual booting except use (hd0,1) not (hd1,1).
Edit:
and change to sda1 from sdb1.
or
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot



But it does not make sense that drives are reversed. What drive do you have set as boot drive in BIOS. And have you changed it? Or did you change the SATA ports drives are plugged into?

I have seen mixed IDE and SATA sometimes change and it seemed to be a timing issue.

---

### Post by Grratch on 2010-12-03
The only way I know how to force it to boot to the USB drive is to change the boot sequence in BIOS.  I put the USB (external HD) second in the sequence after the CD ROM drive since I'm having to continually boot to the LiveCD.  This puts the internal SATA third in the sequence list.  What order should the boot sequence be?

---

### Post by oldfred on 2010-12-03
Almost all new BIOS have two settings for boot order. One is type of device HD, CD, floppy, USB etc. Another is then which hard drive. Some have it as a total different place in the BIOS menu and some just have it as part of the device select but have a submenu under hard drive.

You want to leave it as it is for now. Later you may want to make primary boot drive first to speed up booting slightly and only use one time select key (often f12) to choose alternative device when needed.

---

### Post by drs305 on 2010-12-03
I was surprised a bit when I was rooting around my BIOS settings that to select a small thumb drive to boot first I had to select an option under 'hard drives'. Upon reflection, I suppose it makes sense because it just as well could have been a 500GB USB external drive as far a BIOS was concerned.

---

### Post by Grratch on 2010-12-03
Well, I ran the manual boot from grub> with the revised parameters as per oldfred above using* hd0,1* and *sda1* where indicated.  Here are the messages I received:

[COLOR=Navy][FONT=Courier New]Begin: Running /scripts/local-bottom ... done. done.
Begin: Running /scripts/init-bottom mount: mounting /dev on /root/dev failed: No such file or directory. done.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: /proc on /root/proc failed: No such file or directory.
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg[/FONT].[/COLOR]

Thoughts?...        Thanks.

---

### Post by oldfred on 2010-12-03
It seems like it is starting to boot but then gets lost. Like the hd0,1 is correct but /dev/sda1 is not.

Try this (which should not work, but then your first entry should not have gotten as far as it did)

linux (hd0,1)/vmlinuz root=/dev/sd[COLOR=Red]b1[/COLOR]

This says to boot from hd0,1 as that is how grub sees it but once it starts to boot Ubuntu will see it as sdb1. I do not see how this could work, but... maybe worth a try.

---

### Post by Grratch on 2010-12-03
Actually, I don't see the typo you were referring to - both lines originally had (hd0,1) and that's how I entered them.  However, I went and re-ran the commands just in case.  Same messages as before.

One thing I forgot to mention before is that I'm left with a (initramfs) prompt after all of the messages finish displaying.

---

### Post by oldfred on 2010-12-03
Something weird just happen. Did you see my post where I had thought I had a typo. That was a correction to the one that now posted above.

The one I now see above is just an experiment while we are here to see if grub thinks the drive is hd0 while once Ubuntu starts to boot it knows it is sdb which should not happen.

---

### Post by Grratch on 2010-12-03
It appears I did see your post where you thought you had a typo.  That post is different now.  Weird indeed...
So, I ran the commands in the edited post and, as you suspected, it didn't work.  Here is the output of the messages
if it is helpful:

[FONT=Courier New][COLOR=Navy]VFS: Cannot open root device "sdb1" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
[/COLOR][/FONT][INDENT][FONT=Courier New][COLOR=Navy]      0800     976762584 sda drive: sd[/COLOR][/FONT]
[FONT=Courier New][COLOR=Navy]      0801     8393931 sda1[/COLOR][/FONT]
[FONT=Courier New][COLOR=Navy]           0802     390708832 sda2[/COLOR][/FONT]
[FONT=Courier New][COLOR=Navy]           0803     577657237 sda3[/COLOR][/FONT]
[FONT=Courier New][COLOR=Navy]           0b00     1048575 sr0 driver: sr[/COLOR][/FONT]
[/INDENT][FONT=Courier New][COLOR=Navy] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/COLOR][/FONT]

Then the whole thing hung.  Had to do a hard reboot.

---

### Post by oldfred on 2010-12-03
That is saying you do not have a sdb?

They used to have a file in the grub folder. I think they only used it for a few versions and now it is not required.

/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

Do you have the above file and does it show both drives like the one I posted. If not add the hd1 line.

---

### Post by Grratch on 2010-12-03
Apologies - I'm not following what it is you want me to do here.  How do I find whether I have the file (/boot/grub/device.map)?  Or are those commands you're wanting me to enter?

---

### Post by drs305 on 2010-12-03
Let's try this - from the grub prompt:
```

search -f --set /vmlinuz
probe -u --set=uuid $root

```
That should let Grub2 search for and set the parameters if it finds what it's looking for.
Then run the following and note what it shows as the device (hdX,Y) for root and prefix. Jot them down, as well as the first few digits of the UUID.
```
set
```
Note if the prefix and root are the same partition. Prefix will include /boot/grub.
Finally, just use the (hdX,Y) values in the following and see if Grub can view grub.cfg. If it can, it should return the contents of grub.cfg. If you get nothing, then "ls (hdX,Y)/boot/grub/grub.cfg", which should return "grub.cfg" You can do the same for device.map ("ls (hdX,Y)/boot/grub/device.map"  (This is only if you start with a grub prompt and never see the grub menu.):
```
cat (hdX,Y)/boot/grub/grub.cfg
```
Press ESC and then "e" to edit the first menuentry.
Make sure the (hdX,Y) values are the same as what "set" displayed. If they are different, change them to match "set" values. Also make sure the UUID is the same as the one in set.
When they match, CTRL-x to boot.

---

### Post by oldfred on 2010-12-03
Sorry, I want you to see if you have the file device.map in /boot/grub and what its contents are. It should look like what I posted, just a list of grub type drive number and Ubuntu equivalents. Sometimes it also has the floppy drive as fd0 also.

---

### Post by Grratch on 2010-12-03
Ok,
Ran the initial commands you gave and then ran the **set** command.  Here is what I saw:

[FONT=Courier New][COLOR=Navy]prefix=(hd0,msdos1)/mnt/boot/grub
root=hd0,msdos1
uuid=e4e8db4e-...[/COLOR][/FONT]

So, prefix and root are the same and prefix included /boot/grub.

Ran the next command: **cat (hd0,1)/boot/grub/grub.cfg**.  I'm guessing it couldn't view*  grub.cfg* as I ended up with
a screenful of unintelligible output; mostly digits surrounded by "<" and ">" (eg, <0>, <14>, etc.).

Couldn't continue with any other of the instructions after that.

I appreciate you guys hanging in there with me.

---

### Post by drs305 on 2010-12-03
I don't know where it got the prefix address got the "/mnt" from, assuming these results were from a normal boot stuck at the grub prompt (or menu).  Once more form the top.... Let's try it without the "/mnt". Not being able to read grub.cfg could be the reason for the failure to boot a menu entry.

```
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

---

### Post by Grratch on 2010-12-03
[FONT=Arial]Ran commands 1-5 without any errors.  When I ran the "boot" command, I received the same messages as in post #21:[/FONT]

[FONT=Courier New][SIZE=2][COLOR=Navy]Begin: Running /scripts/local-bottom ... done. done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory. done.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: /proc on /root/proc failed: No such file or directory.
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2]
[/SIZE][/FONT] [FONT=Arial]
[/FONT] [FONT=Arial]What do you think?[/FONT]

---

### Post by oldfred on 2010-12-03
We were just in another thread where the user had a very large hard drive and just root & swap. I wonder if grub does have trouble with searching the large drive to find its files.

My suggest is to reinstall with a smaller root partition and let the large space be /home and/or a /data partition.

Or use gparted just to shrink the / (root) to a much smaller partition and create additional partitions. Reinstall is probably easier.

For the total amount of space for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical
Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by drs305 on 2010-12-04
> **oldfred said:**
> We were just in another thread where the user had a very large hard drive and just root & swap. I wonder if grub does have trouble with searching the large drive to find its files.

That is what I was suspecting when I saw the grub.cfg was at the 300GB+ point of the drive. It's why I asked him to cat the (hd0,1)/boot/grub/grub.cfg file - to see if it could find and read it.  Of course, I didn't understand the result - it found it but couldn't read it, which made me think the file was corrupted.

The BIOS disk size limitation is pretty insidious. The OS can see the entire drive's contents but BIOS may not be able to. Additionally, Grub could work fine for a long time, only to fail when the grub files are rewritten and suddenly core.img or grub.cfg is saved beyond the BIOS limit. I get suspicious any time a grub failure occurs after an update and the core.img or grub.cfg file is well beyond the location of the other grub files.

A separate boot partition early in the disk is a definite option, as are BIOS updates. One thing I have had some success with is to have the user clear out all their trash and empty the download cache (sudo apt-get clean) and immediately run update-grub. Often the grub files are then saved to a earlier location on the disk and Grub starts working again. Unfortunately, that is a temporary fix as eventually the files will probably end up outside the BIOS limit at some point.

If Grratch *could* boot into his system or uses the LiveCD to chroot into it, I would try emptying all trash, especially root's, then clean the download cache, and then update-grub just to see if moving the location of the grub.cfg file worked. I'd already recommended he try a purge/reinstall in a separate conversation.

@ Grratch,

If you do attempt the purge/reinstall I recommended, after you chroot into your Ubuntu partition (sudo chroot /mnt/temp) following the link I provided, *and before you run the install commands*, do this:
```
apt-get clean
```
This will possibly clean out some space on the Ubuntu system and perhaps allow the grub files to be stored earlier on the partition.

You can also check your BIOS for a "large drive" setting or check the reported disk sizes. If you find that it says the drive is 137GB or smaller, you have a BIOS limitation that is preventing it from seeing files past the 137GB limit.

---

### Post by Grratch on 2010-12-04
Last night I did a purge/reinstall of Grub 2 with **chroot** from the LiveCD without effect.  I re-ran the process
again this morning using the **apt-get clean** command inserted at the appropriate spot in the sequence as
suggested.  Again, nothing.  I checked BIOS again for a large drive setting and didn't find one.  From an
earlier post of mine regarding my computer's BIOS:

> BIOS

    * Info: American Megatrends (?) Version 0221; Build Date 11/3/09 (Note: in the BIOS Tools menu, there is an option for ASUS Easy Flash 2 utility)
    * External Drive Size: Not reported anywhere in BIOS, but the USB drive I am using is a 500GB device.
    * Settings: I don't see an option for "large drives", however, diving in deep, I get to the USB Mass Storage Device Configuration menu. It is currently set to AUTO. Here is what BIOS says about this: "If AUTO, devices less than 530MB will be emulated as floppy and remaining as hard drive. Forced FDD option can be used to force a HDD formatted drive to boot as FDD (Ex. ZIP drive)."I'll be honest, I'm more than a little hesitant to try and re-install Ubuntu. When I initially started this whole
process a week ago, the install corrupted the MBR of my Windows 7 drive.  It took me 3 days to get that
fixed (mostly because I didn't know what I was doing and ended up making it worse before it finally got
fixed - by my brother-in-law).  I'm sort of feeling "once bitten, twice shy" right about now.

---

### Post by drs305 on 2010-12-04
> **Grratch said:**
> I'll be honest, I'm more than a little hesitant to try and re-install Ubuntu. 

I'm sorry the Grub purge/reinstall didn't work. As far as a full reinstallation of Ubuntu and it's effect on Windows, I don't think you need be as concerned as you state (of course, it's not my machine).

I really don't know what else we can try to restore your system. I got into the thread a bit late but didn't see anything that was missed unless you once had some unusual setup with RAID, other filesystems, etc.

Most of us are pretty comfortable with the Grub/Windows interface and having *oldfred* in this thread means your efforts are being monitored by someone who really knows his way around the Windows boot process.

In fact, by merely having Windows on one drive and Ubuntu on another you can keep both bootloaders on their respective drives but still allow Grub to see and boot to Windows. And if you are paranoid about it, you could disconnect your Windows drive while you install Ubuntu.

Of course, that decision is up to you. If you decide to reinstall Ubuntu you might want to make the partition smaller than the entire drive. A 2009 BIOS almost certainly can handle large drives, but it wouldn't hurt to have an Ubuntu system partition of less than 100GB.

And there are things you can do to make a reinstall easier, such as copying your home folder somewhere else before you reformat the drive, and exporting a list of installed apps through Synaptic so you can easily add any additional programs back into your system.

---

### Post by oldfred on 2010-12-04
When you install to a hard drive that is not sda whether internal or external grub will install to sda as it assumes you boot from that. With externals then that is a real problem.

The only way to avoid that now with Maverick is to use manual install which gives the combo box that lets you choose to install grub to sdb (or sdc etc). I always create partitions in advance, so I have not seen the installer but I understand you can relatively easily create the partitions as part of manual install.

---

### Post by Grratch on 2010-12-04
Well, I could try again and would probably open up the box and disconnect the hard drive as you mentioned
(yes, I am paranoid...).  In regards to messing up my Windows 7 on my other drive, a forum member by the
handle of C.S. Cameron stated: "[COLOR=DarkGreen][I]This sort of thing never happens if you disconnect your internal hard drive
before installing to USB drive.[/I][/COLOR]", in response to a different thread of mine when my computer was really
messed up with the initial install.

If I re-install, will Ubuntu give me options to make a smaller partition during the process?  I don't recall what
happened when I started this all a week ago.

@oldfred:  how do I get to the manual install?

---

### Post by drs305 on 2010-12-04
> **Grratch said:**
> If I re-install, will Ubuntu give me options to make a smaller partition during the process?  I don't recall what
happened when I started this all a week ago.

The easiest way is to create the partitions with Gparted (LiveCD) so you have them set up the way you want. Note the designations and sizes, then start the installation. When you get to the partitioning section, choose manual partitioning.

Once in the manual partitioning section, you will choose:
Partition
Filesystem: ext3, ext4, etc
Format - yes or no (for you, yes) (For /swap, you don't designate the format)
Mountpoint - / (root), /home, /swap etc  If you want a separate home, this is where you would designate a partition and select /home as the mountpoint.
I can't remember if a swap partition is automatically created if you don't specify it.

---

### Post by Grratch on 2010-12-04
Well, you've talked me into it.  This may take me the weekend since I'll be in and out a lot today and tomorrow.  I'll be checking in at various points if I have questions, although I think you've given me everything I need to get it re-installed.  I'll just re-read everything again you and oldfred have provided very carefully before I get started.

---

### Post by oldfred on 2010-12-04
I think for the last year I politely disagreed with C.S. Cameron on unplugging drive. But it was a little confusing as the 'Advanced' button was really 'where to I want to install grub button' and most missed it. 
Now with only the advanced install even giving a choice C.S. Cameron is more correct:) especially for those who are not sure what they are doing which is most doing new installs.

I like drs305 like to format in advance. Everyone has different recommendations and none are really wrong as it depends a lot on your usage. System install does not have to be very large. I have lots of programs installed and have used about 6GB.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.

More advanced:
But, I like to have several 25GB roots if hard drive is large enough, for testing other installs or even the next Ubuntu install.  I prefer separate /data over /home but that requires a little more configuration after the install to set up.

To understand partitioning:
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by drs305 on 2010-12-04
One more thought on partitioning if you aren't well-versed in its finer points.

You can have only 4 primary partitions, one of which should be an extended partition. You can have an almost unlimited number of logical partitions, which are contained in the extended partition.

(primary #1) (primary #2) (( extended   (logical) (logical) (logical) ... ))

If you have the extra space, I'd make at least one empty primary with enough space to put Windows on later (you never know), and the other partitions logical ones. The reason I'd keep an empty primary is that Windows requires a primary partition. Ubuntu/linux can be put anywhere and logical partitions provide more flexible options.

Again, just personal preference.

---

### Post by Grratch on 2010-12-04
Re-install is in progress.  Tried to do the fancy disc formatting suggested, but it seems I can only enter some things from   the install and not from GParted no matter where I looked (eg, setting "/", "/home", "/swap") and after I read the materials by oldfred.  So I did the basic setup suggested by oldfred:

20 GB Mountpoint / primary
Mountpoint /home (logical)
2 GB swap area

I've gotten to the "Who are you?" portion of the install and it seems to have hung.  The progress meter is about 5/6 complete and there is a message that says "Ready when you are..."  Ready for what?  Also, the Forward button on this screen is grayed out.  Nothing has moved in a while so I seem stuck...

---

### Post by oldfred on 2010-12-04
You cannot use Grratch but grratch as your name. The name does not like capitals nor special characters.

---

### Post by Grratch on 2010-12-04
Ahh, thanks.  That was it.  Install has resumed...  Will let you know the outcome.

---

### Post by Grratch on 2010-12-04
Success at long last!  Installation has completed on my external drive and it is functioning well. For the record, and if this may help anyone else, here is the order of events for the reinstall:

[LIST=1]
[*]Attempted a repartitioning of the external HD and had it set up with linux partitions as recommended, plus an empty primary and a few 20 Gb logicals, a large drive space and a swap area.  I got it looking pretty close to how drs305 and oldfred recommended in their previous posts.
[*]Shut down computer and then opened up my box and disconnected the internal SATA which has Windows 7 installed on it.
[*]Restarted computer booting to Ubuntu 10.10 LiveCD
[*]Initiated installation process.
[*]Because I didn't set mount points correctly in the original repartitioning and got errors, I went ahead and repartitioned the external drive from the install options.  This time, I gave it a 20 GB  primary with a mountpoint of "/", a 2 GB swap, and set the remaining space as a logical partition with the mountpoint as "/home" - very basic.  From the information in oldfred's posts, it appears I can do some partition tweaking after the install with Gparted from the LiveCD if I wish.  Will look into that.
[*]Install proceeded nicely until it hung.  Checked in with the forum and oldfred noted that the name you wish to use cannot have caps or special characters in it.  Corrected the name to comply as per previous statement.
[*]Installation completed normally.
[*]Rebooted machine to the external drive, removed LiveCD.  It booted properly into the new external drive formatted with Ubuntu.
[*]Played around a bit and ran several tests.  Downloaded and installed updates.  All appeared in order.
[*]Shut down and unplugged machine.  Re-connected internal SATA drive.
[*]Powered up and booted into Windows 7 appropriately - no problems!
[*]Rebooted again and from BIOS, selected the new external drive; it booted into Ubuntu as appropriate.  All is well.
[/LIST]
Well, it's been a week-long journey and more than 20 hours spent trying to get Ubuntu working properly on the new external USB drive, but it's finally there.  My most heartfelt thanks goes out to all those who  helped me and a special shout-out goes to **oldfred** and **drs305** for hanging in there and helping me get Ubuntu set up and running when all appeared hopeless (at least to me).  I know you two spent several hours between the both of you helping me and I really appreciate it.  I had pretty much resigned myself to remaining a Windows user, but no more!

Thanks again! :D

---

### Post by oldfred on 2010-12-05
Glad it is working.:)

Since you had window drive unplugged you need to do a bit of house keeping.

This will add windows to the grub menu on the external so if the external is plugged in you still can boot windows.

sudo update-grub

Grub remembers where it installed and it probably thinks it installed to sda or hd0. You need to to know on updated not to install to sda or it will overwrite your windows boot.

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

The above may not be true any more. It used to save by sda, sdb etc, but I just ran this which I got from drs305 and it looks like it saves by drive id.
sudo debconf-show grub-pc
My entry:
grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD6400AACS-00G8B1_WD-WCAUF1779071

Edit - While it identifies my sdc drive correctly I have two identical 160GB sda & sdb drives. It does not show a difference in /var/cache/debconf/config.dat

---

### Post by wilee-nilee on 2010-12-05
Yipee, some times it takes the knowing ones to get the job done.;)

---

### Post by Grratch on 2010-12-05
@wilee-nilee:  Thank you and thanks for your help on my other thread where I couldn't boot to Windows.

@oldfred:  Housekeeping done; grub updated and it appears that after running **debconf-show** command, the
**dpkg-reconfigure** command run earlier has set future update installs to appropriate drive.

Thanks!

---

