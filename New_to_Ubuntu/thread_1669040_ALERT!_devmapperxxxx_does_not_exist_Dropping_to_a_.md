---
title: "ALERT! /dev/mapper/xxxx does not exist Dropping to a shell!"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by neoterryjoe on 2011-01-17
hi all, 

   My first post here! Just installed my first Ubuntu 10.04LTS server and this came up during first boot.

I've read this:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=813090](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=813090)

And found out that my UUIDs are correct by `blkid`, just a discrepancy:  the booting device in /proc/cmdline  root=/dev/mapper/myroot does not correspond to the info from my fdisk -l:

Device Boot ...
/dev/sda1 * ...
/dev/sda2   ...
/dev/sda5   ...


/dev/disk/by-uuid -la:

fd9e19ca-.... -> /dev/mapper/myroot
e5fec450-.... -> /dev/sda1
...

/etc/fstab:

proc /proc proc nodev,noexec,nosuid 0 0
/dev/mapper/myroot / ext4 errors=remount-ro 0 1
#/boot was on /dev/sda1 during installation
UUID=e5fec450-...   /boot ext2 defaults 0 2
...

So, I believe I'm supposed to use /dev/sda1 to boot but /proc/cmdline is using root=/dev/mapper/myroot

I tried to change /proc/cmdline to root=/dev/sda1 but seems like the file contents cant be changed even after sudo-ing and changing permissions.

Am I correct to say booting device is /dev/sda1 instead of /dev/mapper/myroot? Any suggestions?

Thanks a lot!

tj

---

### Post by oldfred on 2011-01-17
See this thread:

Fix LVM boot after 10.04 to 10.10 Jan 2011
[http://ubuntuforums.org/showthread.php?t=1661290](http://ubuntuforums.org/showthread.php?t=1661290)
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.

run boot script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by neoterryjoe on 2011-01-17
Thanks oldfred for the reply,

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

my-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

my-swap_1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 598.9 GB, 598879502336 bytes
255 heads, 63 sectors/track, 72809 cylinders, total 1169686528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758 1,169,684,479 1,169,182,722   5 Extended
/dev/sda5             501,760 1,169,684,479 1,169,182,720  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/my-root fd9e19ca-315d-4a9c-a45f-604bbe9da078   ext4                                     
/dev/mapper/my-swap_1 5cf91a19-19fa-4c8a-a3a0-326f56fff226   swap                                     
/dev/sda1        e5fec450-2c09-42e3-aec1-002576223d13   ext2                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        x01Kft-KsfY-Ddrx-gYdh-wKEf-MNn3-T4m4jz LVM2_member                               
/dev/sda: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
my-root
my-swap_1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/my-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext2       (rw)


============================= sda1/grub/grub.cfg: =============================

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
insmod lvm
insmod ext2
set root='(my-root)'
search --no-floppy --fs-uuid --set fd9e19ca-315d-4a9c-a45f-604bbe9da078
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
search --no-floppy --fs-uuid --set e5fec450-2c09-42e3-aec1-002576223d13
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e5fec450-2c09-42e3-aec1-002576223d13
	linux	/vmlinuz-2.6.32-24-server root=/dev/mapper/my-root ro   quiet
	initrd	/initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e5fec450-2c09-42e3-aec1-002576223d13
	echo	'Loading Linux 2.6.32-24-server ...'
	linux	/vmlinuz-2.6.32-24-server root=/dev/mapper/my-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e5fec450-2c09-42e3-aec1-002576223d13
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e5fec450-2c09-42e3-aec1-002576223d13
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-24-server
    .0GB: vmlinuz-2.6.32-24-server

============================= my-root/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/my-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e5fec450-2c09-42e3-aec1-002576223d13 /boot           ext2    defaults        0       2
/dev/mapper/my-swap_1 none            swap    sw              0       0

================= my-root: Location of files loaded by Grub: =================


    .0GB: initrd.img
    .0GB: vmlinuz

```

---

### Post by oldfred on 2011-01-18
I really do not know LVM, but your boot looks correct. You do not directly edit grub.cfg (except in an emergency).

When you have a separate /boot partition the set root & search lines have to refer to the /boot partition and the linux line root= has to refer to the / or system partition. Your UUIDs & partition settings look correct, others should review just to be sure.

If you reinstall grub you have to mount both /boot & / to reinstall.

If separate /boot
$ sudo mount /dev/mapper/my-root /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

Your fstab does not mount swap?  It still should boot but you will want to add that to fstab.

---

### Post by neoterryjoe on 2011-01-18
my /proc/cmdline is

```
BOOT_IMAGE=/vmlinuz-2.6.32-24-server root=/dev/mapper/my-root ro quiet
```

so is the root= location correct? I'm suspecting its should be /dev/sda1?

what should be the swap directory? /dev/mapper/my-swap_1 ?

Any other suggestions?

Thanks!

---

### Post by oldfred on 2011-01-19
If you look at the link in post#2 and that OP's results.txt in his post #6 you can see his entire boot stanza and fstab with a swap entry. His volume name was different but otherwise looks like your results.txt. After he reinstalled grub2 it then worked.

Again, set root is the /boot partition, but root= in the linux line is the actual root partition.

---

### Post by neoterryjoe on 2011-01-19
> If separate /boot
$ sudo mount /dev/mapper/my-root /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

I've tried this but its still the same after I rebooted. Just to clarify:

A silly question, is "separate" a command? I executed without the if statement..

When I saw the above statement, "ALERT! /dev/mapper/my-root does not exist Dropping to a shell!" appears and then I'm left with a prompt: (initramfs).  Am I supposed to execute the above reinstallation here? Or do I execute it after exiting and logging into my user account?

Thanks again!

---

### Post by oldfred on 2011-01-20
If separate is a comment, only the commands after the $ should be copied & pasted. If you are getting an error message you may have left off a space?

Just as commands:

```
sudo mount /dev/mapper/my-root /mnt
```
```
sudo mount /dev/sda1 /mnt/boot
```
```
grub-install --root-directory=/mnt /dev/sda 			 		
```

If you get errors then there is some other problem.

---

### Post by neoterryjoe on 2011-01-20
Probably there's some other problem then. Thanks for all the help! :)

---

