---
title: "Chromium OS Building"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by TheAJGman on 2011-02-27
Hi i am semi-new to ubuntu and im trying to build Chromium OS on my 64 bit 10.041 ubuntu hp pc. im having some problems with
 
*repo init -u [http://git.chromium.org/git/manifest](http://git.chromium.org/git/manifest)*

it comes out to

[I]user@Ubuntu-Laptop:~/chromiumos$ repo init -u [http://git.chromium.org/git/manifest](http://git.chromium.org/git/manifest)
No command 'repo' found, did you mean:
 Command 'rep' from package 'rep' (universe)
 Command 'repl' from package 'nmh' (universe)
 Command 'repl' from package 'mailutils-mh' (universe)
repo: command not found
user@Ubuntu-Laptop:~/chromiumo$[/I]

evern thought i installed depot_tools which should let me use the repo command

---

### Post by davidmohammed on 2011-02-27
I'm curious - why are you trying to compile?  Why not install it from software-centre/synaptic manager?

---

### Post by TheAJGman on 2011-02-27
> **davidmohammed said:**
> I'm curious - why are you trying to compile?  Why not install it from software-centre/synaptic manager?
did you not read my whole post im building **CHROMIUM OS** not google chrome the browser

---

### Post by davidmohammed on 2011-02-27
ahh yes - missed the "OS" part - thought you were trying to install chromium the browser...

---

### Post by davidmohammed on 2011-02-27
use the instructions here to [install]("http://source.android.com/source/git-repo.html") repo

---

### Post by TheAJGman on 2011-02-27
> **davidmohammed said:**
> use the instructions here to [install]("http://source.android.com/source/git-repo.html") repo
im building Chromium OS not Android OS

---

### Post by davidmohammed on 2011-02-27
very true - but you can install  repo using those instructions and then use

repo init -u [http://git.chromium.org/git/manifest](http://git.chromium.org/git/manifest)

to do your chromium stuff.

I believe google uses repo for both android and chromium.

---

### Post by TheAJGman on 2011-02-27
> **davidmohammed said:**
> very true - but you can install  repo using those instructions and then use

repo init -u [http://git.chromium.org/git/manifest](http://git.chromium.org/git/manifest)

to do your chromium stuff.

I believe google uses repo for both android and chromium.
yes but repo doesnt work even thought i have installed depot_tool correctly

---

### Post by TheAJGman on 2011-02-27
can someone help repo wont work yet all other commands work fine

---

### Post by TheAJGman on 2011-02-27
nev mind just installed updates repo works now

---

### Post by TheAJGman on 2011-03-01
great now it wont boot to chromium os after 27 hours of downloading and building chromium now i cant find it in grub can some one help here

---

### Post by davidmohammed on 2011-03-01
boot from a live CD and run the bootinfoscript [here]("http://bootinfoscript.sourceforge.net/") - paste the results in [CODE] tags.

---

### Post by TheAJGman on 2011-03-01
also i was wondering how could i boot to windows because when i installed ubuntu i couldn't boot to 7, im also attempting to re build chromium

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 18233775. But according to the info from 
                       fdisk, sda2 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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

/dev/sda2                  63   166,600,335   166,600,273   7 HPFS/NTFS
/dev/sda3         184,834,048   307,277,823   122,443,776  83 Linux
/dev/sda4         307,277,824   312,580,095     5,302,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        E41646191645ED5C                       ntfs                                     
/dev/sda3        4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce   ext4                                     
/dev/sda4        09a46343-28ec-45c4-84bd-dea73b9dcf07   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev             /home/adrian/chromiumos/chroot/dev none       (rw,bind)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=4535f1f9-d7a8-4e38-a39d-cfa9a881d5ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=09a46343-28ec-45c4-84bd-dea73b9dcf07 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 150.6GB: boot/grub/core.img
 150.6GB: boot/grub/grub.cfg
 150.8GB: boot/initrd.img-2.6.32-24-generic
 150.8GB: boot/initrd.img-2.6.32-28-generic
 150.8GB: boot/initrd.img-2.6.32-29-generic
 150.7GB: boot/vmlinuz-2.6.32-24-generic
 150.7GB: boot/vmlinuz-2.6.32-28-generic
 150.7GB: boot/vmlinuz-2.6.32-29-generic
 150.8GB: initrd.img
 150.8GB: initrd.img.old
 150.7GB: vmlinuz
 150.7GB: vmlinuz.old

```

---

### Post by Hedgehog1 on 2011-03-01
> **davidmohammed said:**
> boot from a live CD and run the bootinfoscript [here]("http://bootinfoscript.sourceforge.net/") - paste the results in [CODE] tags.

Now I may not be understanding this right, however:

According to what I read in the chromium developer guides  [http://www.chromium.org/chromium-os/developer-guide]("http://www.chromium.org/chromium-os/developer-guide") this build creates a virtual machine to work on chromium, not a partitioned OS that can be boot from Grub.

Am I mis-reading this?

***The Hedge***

:KS

---

### Post by TheAJGman on 2011-03-01
> **Hedgehog1 said:**
> Now I may not be understanding this right, however:

According to what I read in the chromium developer guides  [http://www.chromium.org/chromium-os/developer-guide]("http://www.chromium.org/chromium-os/developer-guide") this build creates a virtual machine to work on chromium, not a partitioned OS that can be boot from Grub.

Am I mis-reading this?

***The Hedge***

:KS
omg 32 hours for that is there any way to write an .img file to a flash drive

---

### Post by Hedgehog1 on 2011-03-01
> **TheAJGman said:**
> omg 32 hours for that is there any way to write an .img file to a flash drive

The instruction to move the image to a flash drive on this the same [http://www.chromium.org/chromium-os/developer-guide]("http://www.chromium.org/chromium-os/developer-guide") page, under the section titled: **Getting your image running on a computer without verified boot**

Perhaps you should take some time to read it and understand what you are committing to; it is a great project, but they are assuming a certain level of skill. You can acquire that skill by doing this, however.

Did you still want to know why your Windows 7 isn't booting?

:KS

---

### Post by TheAJGman on 2011-03-01
aaa i read that guide 20+ times how did i miss that aaaa. yes i want to know why 7 aint booting. all so im not planning to commit for a long time

---

### Post by Hedgehog1 on 2011-03-01
> **TheAJGman said:**
> aaa i read that guide 20+ times how did i miss that aaaa. yes i want to know why 7 aint booting. all so im not planning to commit for a long time

The Windows Partition is being referenced incorrectly from the boot sector:
```

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector **[COLOR="Red"]18233775[/COLOR]**. But according to the info from 
                       fdisk, sda2 starts at sector [COLOR="red"]**63**[/COLOR].
    Operating System:  
    Boot files/dirs: 
```

May I suggest you make a new thread asking how to resolve this?

Many folks who can help will likely skip the current thread.

:KS

---

### Post by TheAJGman on 2011-03-01
ok you can find it [here]("http://ubuntuforums.org/showthread.php?p=10510873#post10510873")

---

