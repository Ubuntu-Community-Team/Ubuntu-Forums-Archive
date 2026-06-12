---
title: "GRUB 2 problems"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by zharless92 on 2010-09-21
So I dual booted Windows and Ubuntu. I installed windows first. GRUB kept saying "gave up waiting for device". I edited it using 'e' when the boot menu popped up and was able to boot into Ubuntu. But when I use the 'update-grub' command it works but doesn't update the grub. Any suggestions?

---

### Post by duanedesign on 2010-09-21
try the direct command instead:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Does that update the file?

Do you get any error messages?

~duanedesign

---

### Post by zharless92 on 2010-09-21
it gives the same result as when i use 'update-grub'. it says it finds the OS's and then done. But when i reboot i still have to go in and change the 'root=.....' to 'root=/dev/sda5'.

---

### Post by psusi on 2010-09-21
FYI, it is the initrd that says that, not grub.  You say you have to change the root to sda5?  what was it before?  It should be the UUID of your root partition, which you can check with sudo blkid.

---

### Post by zharless92 on 2010-09-21
When i use that command this is what i get.

```

/dev/sda1: UUID="A2DC14C6DC14971F" TYPE="ntfs" 
/dev/sda5: UUID="20194843-1bc2-42d8-87eb-9964e3652734" TYPE="ext4" 
/dev/sda6: UUID="de13a5be-eef4-4a3e-9dd4-08a6a3de7c91" TYPE="swap" 

```

---

### Post by psusi on 2010-09-22
> **psusi said:**
> FYI, it is the initrd that says that, not grub.  You say you have to change the root to sda5?  **what was it before?**  It should be the UUID of your root partition, which you can check with sudo blkid.

It should be UUID=20194843-1bc2-42d8-87eb-9964e3652734.

---

### Post by drs305 on 2010-09-22
Would you run and post the results of the bootinfo script? It will help us figure out what is going on.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Normally you can edit the Grub files to change from UUID to sdXY by editing /etc/default/grub and removing the # symbol from the line:
> **[COLOR="DarkRed"]#[/COLOR]**GRUB_DISABLE_LINUX_UUID=true

However, if updating grub isn't working, this may be something you have to defer until later...

---

### Post by zharless92 on 2010-09-22
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,086,345,484 2,086,345,422   7 HPFS/NTFS
/dev/sda2       2,086,346,750 2,930,276,351   843,929,602   5 Extended
/dev/sda5       2,086,346,752 2,918,201,343   831,854,592  83 Linux
/dev/sda6       2,918,203,392 2,930,276,351    12,072,960  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A2DC14C6DC14971F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        20194843-1bc2-42d8-87eb-9964e3652734   ext4                                     
/dev/sda6        de13a5be-eef4-4a3e-9dd4-08a6a3de7c91   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/A2DC14C6DC14971F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
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
search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=20194843-1bc2-42d8-87eb-9964e3652734 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=20194843-1bc2-42d8-87eb-9964e3652734 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=20194843-1bc2-42d8-87eb-9964e3652734 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=20194843-1bc2-42d8-87eb-9964e3652734 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 20194843-1bc2-42d8-87eb-9964e3652734
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a2dc14c6dc14971f
    drivemap -s (hd0) ${root}
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
UUID=20194843-1bc2-42d8-87eb-9964e3652734 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=de13a5be-eef4-4a3e-9dd4-08a6a3de7c91 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


1298.1GB: boot/grub/core.img
1459.2GB: boot/grub/grub.cfg
1298.2GB: boot/initrd.img-2.6.32-21-generic
1298.2GB: boot/initrd.img-2.6.32-24-generic
1068.3GB: boot/vmlinuz-2.6.32-21-generic
1298.2GB: boot/vmlinuz-2.6.32-24-generic
1298.2GB: initrd.img
1298.2GB: initrd.img.old
1298.2GB: vmlinuz
1068.3GB: vmlinuz.old

```

---

### Post by psusi on 2010-09-22
Looks fine.  Is that the working version or the not working version?

---

### Post by drs305 on 2010-09-22
Did Ubuntu work on this computer previously? Is this an older computer?

The Grub2 files look ok. I ask the above just because there was a BIOS limitation on where the boot files could be located on older computers. 

Other than a possible problem related to the above, I would probably try reinstalling Grub2 by completely removing and reinstalling it. It only takes about a minute but you need a stable Internet connection and power supply since you will be without a bootloader for that time.

If you have made customizations of the Grub2 menu you might want to make copies of /etc/default/grub and the /etc/grub.d folders before uninstalling if you decide to reinstall.

With a good power supply and Internet connection:
```

sudo apt-get update  # Test your connection. [COLOR="Red"]Don't proceed if it doesn't work.[/COLOR]
sudo apt-get purge grub-common
```
You will be warned that you will be without a bootloader. It will uninstall *grub-pc* and *grub-common*.

```
sudo apt-get install grub-pc
```
This will install *grub-pc* and *grub-common*.

You will be asked for any additions you would like to add to the grub kernel line. If you don't know, just TAB to "OK" and ENTER.
When asked, install grub2 to the *drive* (sda) **not** to a partition.
If the drive isn't selected (*), cursor to it and press the SPACE bar to select it. TAB to "OK" and press ENTER.

That should install Grub2. You shouldn't need to run "sudo update-grub" again unless it didn't find your Windows install the first time.

---

### Post by zharless92 on 2010-09-22
Ok so I did that and still nothing worked. But, when I put in my live cd of ubuntu 10.04 i was going to just reformat the ubuntu partition and just leave it blank until i felt like messing with it again. But when i ran Gparted I noticed that my windows partition had the 'boot' flag. I instead just changed the boot flag to my sda2 (the overall linux partition) and now it boots fine.

---

### Post by psusi on 2010-09-22
> **zharless92 said:**
> Ok so I did that and still nothing worked. But, when I put in my live cd of ubuntu 10.04 i was going to just reformat the ubuntu partition and just leave it blank until i felt like messing with it again. But when i ran Gparted I noticed that my windows partition had the 'boot' flag. I instead just changed the boot flag to my sda2 (the overall linux partition) and now it boots fine.

The boot flag only means anything to the Windows boot loader.  Changing it has no effect on grub.

---

### Post by zharless92 on 2010-09-22
Idk then, it worked for me.

---

