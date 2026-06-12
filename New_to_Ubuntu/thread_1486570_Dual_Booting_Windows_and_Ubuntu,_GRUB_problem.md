---
title: "Dual Booting Windows and Ubuntu, GRUB problem"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by fudgynubbles on 2010-05-18
I've been trying to dual boot Windows 7 and Ubuntu (I started with Ubuntu 10.04 first, then installed Windows). The partitions and installing went fine and was able to run Windows 7, but then I tried to fix the GRUB to dual boot, since Win 7 was automatically booting and wasn't giving me a choice. 

After fiddling for a while, my computer is back to booting Ubuntu automatically, but still not Grub boot option when I start the computer. Here's my boot info script. It seems like everything is OK, I just need to figure out how to do the GRUB. Thanks for any help.

```
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   165,581,954   165,579,907  83 Linux
/dev/sda2    *    165,582,848   165,787,647       204,800   7 HPFS/NTFS
/dev/sda3         165,787,648   306,620,415   140,832,768   7 HPFS/NTFS
/dev/sda4         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sda5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b2404888-fb89-4963-a7cd-62fb6f0c01c7   ext4                                     
/dev/sda2        48DCCF2BDCCF11DC                       ntfs       System Reserved               
/dev/sda3        4CC4D50AC4D4F6E4                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1376fc7-0460-45d5-9d2b-4484c3a95448   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


```

---

### Post by mikewhatever on 2010-05-18
Try running the following first:

sudo os-prober
sudo update-grub

Hopefully, the commands will find and add W7 to the boot menu.

If not, you can add a manual/custom entry.
It looks like sda2 is W7's boot partition. You'll need to edit a grub config file, /etc/grub.d/40_custome.
```
gksudo gedit /etc/grub.d/40_custome
```

then add the following to the end of the file:

```
menuentry "Windows 7 on /dev/sda2" {
        setroot (hd0,2)
        chainloader +1
}
```

When done, run **sudo update-grub**

---

### Post by wilee-nilee on 2010-05-18
Hopefully mikewhatever's options will work. You might notice though that when you reinstalled grub you put it in sda2 the windows boot as well this can cause problems. So in the future remember that grub goes in the MBR generally, (unless you really know what your doing) which is in this case sda, no numbers for partitions. I suspect that sda2 is the recovery partition so it may not really work so don't rely on it, and get a OEM DVD reinstall disk/disks if this was a purchased computer with W7.

Here is a link to grub2, the #11 instructions tells what should have been done reloading grub, don't try this now, it is just an example.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by oldfred on 2010-05-18
Linux sees capitals and lowercase differently. windows thinks they are the same.

You have this:
/bootmgr /Boot/BCD /boot/grub/core.img

The /boot/grub directory may confuse windows with /Boot/BCD
Delete the /boot directory - be sure not to modify the /Boot directory.

---

### Post by fudgynubbles on 2010-05-18
Thanks for the input guys. Mikewhatever's solutions didn't work though. When I run **sudo os-prober** it says:

```
sudo os-prober
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory

```

And when I run **sudo update-grub** it says:

```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

Oldfred, are you saying I need to delete the boot directory for Linux?

---

### Post by oldfred on 2010-05-19
No, It seems you have an extra one inside your windows partition. If concerned rename the one inside the windows partition so it does not say /boot/grub. Its windows seeing two /boots that  confuses it because it does not know /Boot from /boot.

---

### Post by ranch hand on 2010-05-19
If your problem is not getting a menu at boot time hit the "shift" key and hold it down.  The menu should come up.

Posting the entire boot info script results would help too.  At least I hope that is not all you got when you ran the script.

---

### Post by fudgynubbles on 2010-05-21
I got the menu pressing shift, but no Windows 7 shows up.

Here's the full boot script:

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   165,581,954   165,579,907  83 Linux
/dev/sda2    *    165,582,848   165,787,647       204,800   7 HPFS/NTFS
/dev/sda3         165,787,648   306,620,415   140,832,768   7 HPFS/NTFS
/dev/sda4         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sda5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b2404888-fb89-4963-a7cd-62fb6f0c01c7   ext4                                     
/dev/sda2        48DCCF2BDCCF11DC                       ntfs       System Reserved               
/dev/sda3        4CC4D50AC4D4F6E4                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1376fc7-0460-45d5-9d2b-4484c3a95448   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
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
search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b2404888-fb89-4963-a7cd-62fb6f0c01c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b2404888-fb89-4963-a7cd-62fb6f0c01c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b2404888-fb89-4963-a7cd-62fb6f0c01c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b2404888-fb89-4963-a7cd-62fb6f0c01c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2404888-fb89-4963-a7cd-62fb6f0c01c7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f1376fc7-0460-45d5-9d2b-4484c3a95448 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  23.5GB: boot/grub/grub.cfg
  25.9GB: boot/initrd.img-2.6.32-21-generic
  26.0GB: boot/initrd.img-2.6.32-22-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  26.0GB: boot/vmlinuz-2.6.32-22-generic
  26.0GB: initrd.img
  25.9GB: initrd.img.old
  26.0GB: vmlinuz
  25.9GB: vmlinuz.old

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
```

---

### Post by warfacegod on 2010-05-21
```
sudo apt-get install startupmanager
```

This will install Startup Manager for Ubuntu. With it you can set a GRUB2 timeout, screen res., or the Default OS for GRUB to boot from.

---

### Post by ranch hand on 2010-05-21
I am not sure that SUM is a good idea.  It was a nice app for the old grub but it does not work well with the new one yet.

If you have not installed it yet you can get your menu to show up by editing the /etc/default/grub file.

Yours currently has this;
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true

```
at about lines 3 through 5.

It needs changed to;
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true

```
You do that by;
```

gksudo gedit /etc/default/grub

```
and inserting the #, saving the file and running;
```

sudo update-grub

```
and then to check and see if it is on your generated menu;
```

sudo grub-mkcongif

```
This may also fix the lack of an entry for your MS as the update-grub command runs os-prober again.

This was done when grub was installed but does not always pick up every thing at that time.

Give it a whack even if you have installed SUM.  If MS does not show up, and you have SUM installed, please remove SUM and run the update-grub command again.

If MS still does not show up let us know.

Everything except the lack of that entry looks fine on you script results text although I have not ever seen the very last entry before.

This does not look like to tough a deal to get right.

---

### Post by warfacegod on 2010-05-21
I've had no problems with Startup Manager and GRUB2 on several different systems.

---

### Post by ranch hand on 2010-05-21
> **warfacegod said:**
> I've had no problems with Startup Manager and GRUB2 on several different systems.
It does seem to be getting better all the time.

The real problems seem to be when, as in this case, there is a problem with the menu not being generated correctly.  With SUM installed it seems to inhibit os-prober somehow, and then only sometimes.   I am sure this will be corrected.

---

### Post by oldfred on 2010-05-21
Until you fix the two boot directories in windows it will not work. You cannot have /Boot and /boot. There should not be grub boot directories/files in the windows root directory.

---

### Post by fudgynubbles on 2010-05-21
It works! I'm not sure if it was ranch hand's extra # symbol in the script or completely removing the boot files that didn't belong or both (I tried renaming earlier with no success, but I realized I might have forgotten to update the grub after I renamed the files). Anyway, it worked, and thank you all so much for helping me out. I now have a machine that dual boots with no problems at all.

On a side note, as a new Ubuntu user (and freshly addicted one at that), I am constantly impressed by the quality of the support, the product, and the forums. A big thanks to everyone who helps out the little newbs like me.

---

### Post by peterroots on 2010-08-28
I had almost the same problem.
I had Win7 and installed Ubuntu - all worked fine but at some point the Win7 loader option vanished from the grub menu (still had the vista one that i got on 2 machines that have win7 and ubuntu but not vista!)
Anyway the problem was, indeed, the /boot/grub folder in the win7 partition - renaming it and running grub-update seems to have fixed it.
The mystery remains, though, as to how it got there in the first place

---

