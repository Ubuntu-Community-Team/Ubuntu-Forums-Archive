---
title: "WIndows 7 not booting."
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Andrew Jeyaraj on 2011-03-22
I initially had windows 7 dual-booted with windows xp.Recently i installed Ubuntu on the drive that used to have windows xp(formatted it as well). Now when i start up the system,there is no option between win7 and Ubuntu. Ubuntu boots straight off. Is it something to do with the bootloader?
Can i repair the bootloader with a windows 7 disc?

---

### Post by Hero1969 on 2011-03-22
The windows 7 disk will repair the windows boot loader.

bootrec.exe /fixboot

bootrec.exe /fixmbr

Boot into win7.  Make sure everything is working.  You might even want to delete unused partitions through disk management, but don't format them.

Boot using Ubuntu live CD.  Install and be happy.

---

### Post by Rubi1200 on 2011-03-22
Do yourself a favor and run this command from within Ubuntu before taking the steps suggested by the previous poster (no disrespect intended to the advice there).

Go to Applications > Accessories > Terminal

```
sudo fdisk -lu
```
lowercase L not 1

Post the output here please.

---

### Post by Andrew Jeyaraj on 2011-03-22
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08bb08ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    98119679    49058816   83  Linux
/dev/sda2        98121726   625121279   263499777    f  W95 Ext'd (LBA)
/dev/sda5       102400000   266242047    81921024    7  HPFS/NTFS
/dev/sda6       266245308   329012741    31383717    7  HPFS/NTFS
/dev/sda7       430092243   625121279    97514518+   7  HPFS/NTFS
/dev/sda8        98121728   102399999     2139136   82  Linux swap / Solaris

Partition table entries are not in disk order

ill try the WIN7 disc method

---

### Post by Rubi1200 on 2011-03-22
Before you do that, since it may not be necessary, do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Andrew Jeyaraj on 2011-03-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 1690. But according to the info from fdisk, 
                       sda5 starts at sector 102400000.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

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

/dev/sda1    *          2,048    98,119,679    98,117,632  83 Linux
/dev/sda2          98,121,726   625,121,279   526,999,554   f W95 Ext d (LBA)
/dev/sda5         102,400,000   266,242,047   163,842,048   7 HPFS/NTFS
/dev/sda6         266,245,308   329,012,741    62,767,434   7 HPFS/NTFS
/dev/sda7         430,092,243   625,121,279   195,029,037   7 HPFS/NTFS
/dev/sda8          98,121,728   102,399,999     4,278,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        58c77555-6345-433e-b4ac-d2b357f55bdb   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        AA8C5C378C5BFBEF                       ntfs                                     
/dev/sda6        B0981E61981E267E                       ntfs       New Volume                    
/dev/sda7        E0AC28D7AC28AA4C                       ntfs       New Volume                    
/dev/sda8        f2371bab-3359-484b-96b4-b35ab935bee8   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 58c77555-6345-433e-b4ac-d2b357f55bdb
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 58c77555-6345-433e-b4ac-d2b357f55bdb
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 58c77555-6345-433e-b4ac-d2b357f55bdb
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=58c77555-6345-433e-b4ac-d2b357f55bdb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 58c77555-6345-433e-b4ac-d2b357f55bdb
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=58c77555-6345-433e-b4ac-d2b357f55bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 58c77555-6345-433e-b4ac-d2b357f55bdb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 58c77555-6345-433e-b4ac-d2b357f55bdb
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=58c77555-6345-433e-b4ac-d2b357f55bdb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=f2371bab-3359-484b-96b4-b35ab935bee8 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
  17.4GB: boot/initrd.img-2.6.32-21-generic
    .2GB: boot/vmlinuz-2.6.32-21-generic
  17.4GB: initrd.img
    .2GB: vmlinuz
```

---

### Post by coffeecat on 2011-03-23
Hi. The problem is that when you installed Ubuntu, you must have replaced a primary partition that was used by both your Windows installations for booting.

You have Windows 7 in a logical partition, sda5. Partitions sda6 and sda7 have XP boot sectors but no operating system. Are they data partitions? 

Having Windows on a logical partition is unusual  but not a problem if there is a primary partition with boot files   to boot from. I think what's happened is that XP's C: drive was originally where sda1 is now but that when you installed Windows 7 it installed its own boot files to the XP partition, sda1. That's normal for a Windows installer if you install to a logical partition. Windows cannot boot from a logical partition and will happily co-opt any primary partition it can find for this purpose - usually without telling you!

The situation now is that when you installed Ubuntu, grub could not detect Windows 7 to add to a boot menu  because grub looks for Windows boot files - which are not there.

You need a small primary partition for the Windows 7 boot files. To create that you need either to shrink your Ubuntu sda1 partition or erase it and create two primary partitions in its place, a small one for Windows 7's use, and an Ubuntu one. Because I'm not sure how to install Windows boot files into a newly created primary partition for use by a pre-existing Windows partition, I'll pm someone who might be able to help.

**EDIT** Just to clarify: I'd be happy to help with shrinking the Ubuntu sda1 partition and creating the small partition for Windows, but for the installation of the Windows boot files, I'd rather await the advice of the person I've just pm'd. They're offline at the moment, so I'm afraid you'll have to be patient.

---

### Post by oklokl on 2011-03-23
[http://snoopybox.co.kr/1390](http://snoopybox.co.kr/1390)
url ->Middle
Window cd launch(Original version)
Shift + F10
cmd mode
bootsect.exe

bootsect /nt60 sys /mbr
bootcfg /rebuild
bootrec /fixboot
bootrec /fixmbr

---

### Post by Mark Phelps on 2011-03-23
For future reference ... when you add a second, newer, Windows OS to a PC that already has one installed, at least with Vista and Win7, they wrote their boot loader info into the "older" OS partition.  Thus, when you deleted or overwrote the "older" partition, you wiped out the boot loader for Vista/Win7.

---

### Post by oldfred on 2011-03-23
It is much better to have windows in a primary partition. 

I have not recreated after the fact a boot partition for windows. You would have to have a primary NTFS partition with the boot flag. Then run the windows repairs on that partition to get it to add back these two files. bootmgr is a boot file & the BCD is a file that has all the info on where your install is.

/bootmgr /Boot/BCD

Some of these links are to Vista but the repair process is similar. Ignore any old grub references.

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Andrew Jeyaraj on 2011-03-23
sda 6 and sda 7 are data partitions. Thanks for all the help. i can wait a while. Should i try booting from the Win7 DVD and running repairs?

---

### Post by Andrew Jeyaraj on 2011-03-23
Is there any way to fix my this without re -installing windows.As it has quite a lot of my stuff on it and i need it for work etc.?

---

### Post by oldfred on 2011-03-23
Did you try creating the small NTFS primary partition sda3 or sda4 with a boot flag? And then running windows repairs?
The normal win7 boot partition is 100MB.

---

### Post by Andrew Jeyaraj on 2011-03-23
should i do this from the live cd?

---

### Post by coffeecat on 2011-03-23
> **Andrew Jeyaraj said:**
> should i do this from the live cd?

You can create the small NTFS partition with Gparted in the live CD session. You have to use the live CD rather than a Windows disc because it looks as though you are going to have to shrink the Ubuntu sda1 partition to do this. Shrink sda1 and then create a primary NTFS partition in the freed-up space. As oldfred said, it will be numbered sda3 or sda4. Don't forget to add the boot flag to the new NTFS partition you make before you quit Gparted.

---

### Post by Andrew Jeyaraj on 2011-03-23
ok. ill try it.

---

### Post by Andrew Jeyaraj on 2011-03-24
i shrunk the ubuntu partition and created a 100mb ntfs partition.However the option of "Manage Flags" wasn't available.

---

### Post by oldfred on 2011-03-24
I think it is right click on the partition to manage flags in gparted.

There is a way to set it as active (boot flag) in windows but I never saved that. I am sure any windows instructions would include that also.

You can also set it from command line:

set boot flag on for sda[COLOR=Red]3[/COLOR] (off for others)
```
sudo sfdisk -A[COLOR=Red]3[/COLOR] /dev/sda


```If you created sda4 change the above to A[COLOR=Red]4[/COLOR].

---

### Post by Andrew Jeyaraj on 2011-03-24
ok. so i created an ntfs(100mb) partition "sda3" and set the boot flag.now what do i do?

---

### Post by coffeecat on 2011-03-24
See oldfred's post #10.

---

### Post by Andrew Jeyaraj on 2011-04-10
Thanks A Lot. Finally Got It Fixed!!

---

