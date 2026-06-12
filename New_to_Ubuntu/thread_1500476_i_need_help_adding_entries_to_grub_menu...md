---
title: "i need help adding entries to grub menu.."
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Tryer(ForLife) on 2010-06-03
Ok, don't ask me why, but i have windows 7, windows XP and ubuntu on 1 machine, on 1 hard drive, which you can see from this

> zoro@zvir:~$ sudo blkid
/dev/sda1: LABEL="XP" UUID="A060FD1A60FCF7BC" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="3E7CFD087CFCBC29" TYPE="ntfs" 
/dev/sda5: UUID="67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd" TYPE="ext4" 
/dev/sda6: UUID="dd2c9031-55a2-4d8f-ae02-007346a96d2c" TYPE="swap" 
/dev/sdb1: LABEL="Prijenosni" UUID="18E4D853E4D834AA" TYPE="ntfs" After some problems i lost grub, and i couldn't access OS's, i managed to get the grub back, but i can't add windows XP to the list, i have Ubuntu and windows 7, but i don't know what i have to add to grub.cfg in order to have Win XP, this entry is for Windows 7, that much i know

> menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a060fd1a60fcf7bc
    chainloader +1
}

what doesn't make sense is that according to blkid on /dev/sda1 i have XP, how in the world is Win7 loading i don't know.

and what do these lines mean?
> search --no-floppy --fs-uuid --set a060fd1a60fcf7bc
    chainloader +1

---

### Post by philinux on 2010-06-03
Don't edit grub.cfg instead click the grub2 link below and sort out which files you need to edit.

Also see this.
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)

---

### Post by Tryer(ForLife) on 2010-06-03
i did read that, and i believe it's the same thing, if i do the edit of *40_custom* file and then run grub update for it to enter it into grub.cfg, or if i just add the entree directly into grub.cfg.

I know how to add the entry, i can see it in the menu, i just don't know what i should enter in order for my Win XP to boot, no matter what i enter Win 7 always turns on...i only once managed to add XP to the boot list, and it worked, but then Win7 was giving problems...something about not being able to find ntldr.

Both Windows installations are ok.

---

### Post by wojox on 2010-06-03
> **Tryer(ForLife) said:**
> i did read that, and i believe it's the same thing, if i do the edit of *40_custom* file and then run grub update for it to enter it into grub.cfg, or if i just add the entree directly into grub.cfg.

I know how to add the entry, i can see it in the menu, i just don't know what i should enter in order for my Win XP to boot, no matter what i enter Win 7 always turns on...i only once managed to add XP to the boot list, and it worked, but then Win7 was giving problems...something about not being able to find ntldr.

Both Windows installations are ok.

Every time you run **sudo update-grub** it creates a new grub.cfg

So you need to add the entry to 40_custom

---

### Post by philinux on 2010-06-03
> **Tryer(ForLife) said:**
> i did read that, and i believe it's the same thing, if i do the edit of *40_custom* file and then run grub update for it to enter it into grub.cfg, or if i just add the entree directly into grub.cfg.

I know how to add the entry, i can see it in the menu, i just don't know what i should enter in order for my Win XP to boot, no matter what i enter Win 7 always turns on...i only once managed to add XP to the boot list, and it worked, but then Win7 was giving problems...something about not being able to find ntldr.

Both Windows installations are ok.

Get this and post back the result.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Tryer(ForLife) on 2010-06-03
> **philinux said:**
> Get this and post back the result.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    34,330,904    34,330,842   7 HPFS/NTFS
/dev/sda2          34,330,905    62,910,539    28,579,635   7 HPFS/NTFS
/dev/sda3          62,912,510    78,163,967    15,251,458   5 Extended
/dev/sda5          62,912,512    77,406,207    14,493,696  83 Linux
/dev/sda6          77,408,256    78,163,967       755,712  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,445   488,392,383   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A060FD1A60FCF7BC                       ntfs       XP                            
/dev/sda2        3E7CFD087CFCBC29                       ntfs       Windows 7                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd   ext4                                     
/dev/sda6        dd2c9031-55a2-4d8f-ae02-007346a96d2c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        18E4D853E4D834AA                       ntfs       Prijenosni                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Prijenosni        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /kernel=kernel1.exe 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a060fd1a60fcf7bc
    chainloader +1
}
menuentry "Windows XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set A060FD1A60FCF7BC
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=67c902ff-9aee-4bb9-8f7a-6fdb6a9071fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dd2c9031-55a2-4d8f-ae02-007346a96d2c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  32.2GB: boot/grub/core.img
  32.7GB: boot/grub/grub.cfg
  34.8GB: boot/initrd.img-2.6.32-21-generic
  35.5GB: boot/initrd.img-2.6.32-22-generic
  34.7GB: boot/vmlinuz-2.6.32-21-generic
  35.5GB: boot/vmlinuz-2.6.32-22-generic
  35.5GB: initrd.img
  34.8GB: initrd.img.old
  35.5GB: vmlinuz
  34.7GB: vmlinuz.old
```

---

### Post by Irony on 2010-06-03
Go to *etc/grub.d/40_custom* and add the following;

```
menuentry "Windows XP on /dev/sda2" {
    insmod ntfs
    set root='(hd0,2)'
    chainloader +1
}
```

And then do;

```
sudo update-grub
```

Now reboot, you should see the entry on the last line of your grub window, see if you can boot to XP.

---

### Post by Mark Phelps on 2010-06-03
IF what you're trying to do is have two GRUB2 menu entries, one for Win7, the other for XP, and be able to select each one individually -- that's not going to work.

BOTH your XP and Win7 loader files are on the same partition -- which is the default when you install Win7 after XP.

All that GRUB can do is hand off control to a partition and the loader in that partition. Trying to boot from your second partition will NOT work because there are no boot loader files there.

Unless you go to a LOT of work to move the Win7 loader files into a separate partition, you're going to have to live with the MS Windows OS selection menu.

---

### Post by Tryer(ForLife) on 2010-06-03
> **Irony said:**
> Go to *etc/grub.d/40_custom* and add the following;

```
menuentry "Windows XP on /dev/sda2" {
    insmod ntfs
    set root='(hd0,2)'
    chainloader +1
}
```And then do;

```
sudo update-grub
```Now reboot, you should see the entry on the last line of your grub window, see if you can boot to XP.

no i have an error,

NTLDR is missing
Press Ctrl+Alt+Del to continue

And then it restarts....

I'm guessing that boot loader for Win XP is messed up, but it worked for me yesterday when i was trying on different entries in grub.cfg...

---

### Post by Tryer(ForLife) on 2010-06-03
> **Mark Phelps said:**
> IF what you're trying to do is have two GRUB2 menu entries, one for Win7, the other for XP, and be able to select each one individually -- that's not going to work.

BOTH your XP and Win7 loader files are on the same partition -- which is the default when you install Win7 after XP.

All that GRUB can do is hand off control to a partition and the loader in that partition. Trying to boot from your second partition will NOT work because there are no boot loader files there.

Unless you go to a LOT of work to move the Win7 loader files into a separate partition, you're going to have to live with the MS Windows OS selection menu.

Yes i'm also starting to think that it's not possible to add it directly in the GRUB.
I managed to add XP option in the Windows 7 bootloader and i can now access it from there.

I will edit this post with links that helped me in recovery....

---

