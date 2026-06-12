---
title: "Grub Loading. Error: No such disk"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by djm227 on 2010-03-09
I must of messed something up, but I have no idea what.  I woke up this morning and found the update manager on my desktop.  I couldn't get it to do anything, and nothing else would open.   So I rebooted (manually), and ended up getting the dreaded
> GRUB loading
ERROR: No such disk
grub rescue>I'm not sure what could be the cause of this......I did recently install the real time kernel..or maybe it was the manual reboot.  I'm not sure, but some help would really be appreciated as I need this computer for my classes.

Thanks

---

### Post by kernco on 2010-03-09
If you can boot from a live cd and post your /boot/grub/grub.cfg (if you're using Grub 2) or /boot/grub/menu.lst (if you're using Grub 1), that would help.  If you don't know what you're using just post the one that exists or grub.cfg is both are there.

---

### Post by djm227 on 2010-03-09
When I input that I get
 > bash: /boot/grub/grub.cfg: No such file or directory
bash: /boot/grub/menu.lst: No such file or directory


Do I need to navigate to a certain directory before I run those commands?  If so...I've never been quite sure how to do that.

Thanks.

---

### Post by kernco on 2010-03-09
If you're on the live cd then /boot will be the boot directory for the CD, not for the system installed on your hard drive.  You need to look in the correct hard drive partition.  I think they show up in the Places menu, and will be called something like /dev/sda1

---

### Post by djm227 on 2010-03-09
My Ubuntu install is under extended partition /dev/sdc3...more specifically the partition under that which is /dev/sdc5.  So should I be inputting /dev/sdc5/grub/grub.cfg to the terminal?  If so, I'm still getting the bash error.

---

### Post by bcbc on 2010-03-09
Try the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by djm227 on 2010-03-09
Ok cool, that worked.  Here's what it says:

```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=136a8f67-42e0-40f1-9b89-69ec1ceed61c)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01c76a22

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,067,264   586,067,202   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b825087

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48af48af

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848    76,290,047    76,083,200   7 HPFS/NTFS
/dev/sdc3          76,292,685   156,296,384    80,003,700   5 Extended
/dev/sdc5          76,292,748   152,922,734    76,629,987  83 Linux
/dev/sdc6         152,922,798   156,296,384     3,373,587  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2032 MB, 2032664576 bytes
32 heads, 63 sectors/track, 1969 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e8da7

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     3,967,487     3,967,425   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       60c6f79b-29d4-4d6b-9869-6fe602f411e8   ext3                                     
/dev/sda1        585074A750748D8E                       ntfs       Local Disk                    
/dev/sdb1        A02ADBEB2ADBBD0A                       ntfs                                     
/dev/sdc1        52E04B06E04AF031                       ntfs       System Reserved               
/dev/sdc2        DA085C71085C4E9F                       ntfs                                     
/dev/sdc5        351dd340-ad27-4237-bf6e-b79ccd15a8fb   ext4                                     
/dev/sdc6        7d1e55ed-a786-41cd-aa87-3a33b33159f7   swap                                     
/dev/sdd1                                               vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root=(hd2,5)
search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 351dd340-ad27-4237-bf6e-b79ccd15a8fb
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb ro single 
    initrd    /boot/initrd.img-2.6.31-9-rt
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
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 52e04b06e04af031
    chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=351dd340-ad27-4237-bf6e-b79ccd15a8fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7d1e55ed-a786-41cd-aa87-3a33b33159f7 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


  53.3GB: boot/grub/grub.cfg
  39.7GB: boot/initrd.img-2.6.31-14-generic
  40.3GB: boot/initrd.img-2.6.31-16-generic
  40.2GB: boot/initrd.img-2.6.31-17-generic
  40.5GB: boot/initrd.img-2.6.31-19-generic
  53.4GB: boot/initrd.img-2.6.31-9-rt
  39.6GB: boot/vmlinuz-2.6.31-14-generic
  40.0GB: boot/vmlinuz-2.6.31-16-generic
  41.1GB: boot/vmlinuz-2.6.31-17-generic
  39.9GB: boot/vmlinuz-2.6.31-19-generic
  49.0GB: boot/vmlinuz-2.6.31-9-rt
  53.4GB: initrd.img
  40.5GB: initrd.img.old
  49.0GB: vmlinuz
  39.9GB: vmlinuz.old
```

---

### Post by bcbc on 2010-03-09
You have grub2 on sda and it looks for UUID=136a8f67-42e0-40f1-9b89-69ec1ceed61c which isn't one of the listed partitions. Is it possible you changed the order the drives boot because that would explain the 'no such disk'? 
Also it seems that sdb2 is reporting some discrepancy.

But bootinfoscript quite happily found your ubuntu partition and read everything - so that's a good sign. 

Try reinstalling grub2 to the MBR of sda so that it looks in the right place.

---

### Post by djm227 on 2010-03-09
Ok sounds good.  Came across a little problem in the process of doing that though.  

I'm following [this guide]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") to reinstall Grub2, but when I input:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt

```I get:
```
mount: you must specify the filesystem type
```I must be missing something small, but I'm not familiar with this so bear with me.

I did not rearrange the boot order of the drives prior to getting the grub error, but I did after in order to boot from the Ubuntu Live USB disk.

Thanks for the help, I appreciate it.

---

### Post by djm227 on 2010-03-09
Ok I was able to proceed by adding ext4 at the end of the string...but after that I am still completely lost.  Is there a similar way to restore grub, or could somebody walk me through the steps?

Thanks, sorry for being such a noob

---

### Post by bcbc on 2010-03-09
I haven't done it myself :) but I believe this is how:
```
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

1st command mounts your ubuntu system
2nd installs grub2 to mbr on sda

---

### Post by djm227 on 2010-03-09
Ok, it feels like we're getting a little bit closer.

Here's what I got after the first command (which I assume worked fine):

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc5 /mnt ext4
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

Here's what it said after the second command, which is where I believe the problems lie:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
grub-probe: error: cannot find a device for /mnt//boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 

```

---

### Post by bcbc on 2010-03-09
> **djm227 said:**
> Ok, it feels like we're getting a little bit closer.

Here's what I got after the first command (which I assume worked fine):

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc5 /mnt ext4

```


Try both commands again, but leave off the "ext4" on the end of the 1st.

---

### Post by djm227 on 2010-03-09
Prior to running the two commands, if I left the filesystem (ext4) off of the first string, I would get:
mount: you must specify the filesystem type
Now if I do it without the ext4 I get:
```
mount: /dev/sdc already mounted or /mnt busy

```

Then I get the same thing I did before after running the second command:
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
grub-probe: error: cannot find a device for /mnt//boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ grub-probe --help
Usage: grub-probe [OPTION]... [PATH|DEVICE]

Probe device information for a given path (or device, if the -d option is given).

  -d, --device              given argument is a system device, not a path
  -m, --device-map=FILE     use FILE as the device map [default=/boot/grub/device.map]
  -t, --target=(fs|fs_uuid|drive|device|partmap|abstraction)
                            print filesystem module, GRUB drive, system device, partition map module or abstraction module [default=fs]
  -h, --help                display this message and exit
  -V, --version             print version information and exit
  -v, --verbose             print verbose messages

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ 

```

---

### Post by bcbc on 2010-03-09
Just unmount it first and try again. The reason it failed the first time is you didn't specify the partition: you typed "sudo mount /dev/sda /mnt".

---

### Post by djm227 on 2010-03-09
you, sir, are a genius.

---

### Post by Miljet on 2010-03-09
The mount command keeps telling you that you must specify the partition type like this: ```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sdc5 /mnt 
```

---

### Post by bcbc on 2010-03-09
Glad it all worked out :)

---

