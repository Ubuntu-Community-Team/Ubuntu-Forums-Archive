---
title: "How can Ubuntu find its new partitions?"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Lewian on 2010-08-30
Hi there!
I have just killed (on purpose!) Windows XP on my laptop. I did it the following way: I have Ubuntu 9.04. I used a GParted Live CD. There were two partitions for Windows (one ntfs, one fat32). I deleted them both. Then I created new ext3 partitions on the now free space. 
Note that GParted didn't offer me to define "extended partitions", and when I clicked "resize" on the already existing Linux/ext3 partitions, I was only offered to make them smaller, not larger, which I wanted. So it seemed that the way to go is to create new partitions because I didn't find out how to enlarge the existing ones.

The problem now is that in Ubuntu (using df) I only see the old Linux partitions and don't know how to access the new ones. Also GRUB still offers me to boot Windows, although this is gone. What do I need to do to make all partitions accessible to Linux and erase the last deceptive Windows remains?
(If somebody tells me how to enlarge the old Linux partitions, if necessary I'd also delete the new ones again, as there is nothing on it yet.)

---

### Post by papibe on 2010-08-30
I believe that df only displays partitions that are mounted. Try this:
```
$ sudo fdisk -l
```
Probably it is there, but it's not mounted (assuming everything went well with gparted).
Regards.

---

### Post by oldfred on 2010-08-30
I do not like to move partitions 'left'. It is slightly higher risk than normal partition changes and takes a long time as it has to copy & verify everything.

To update to boot menu:
sudo update-grub

You need to create a mount point and mount the new partition(s). If you want permanent mounting on boot you need to edit fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Some are now recommending mountmanager also in synaptic:

---

### Post by Lewian on 2010-08-30
For the moment just thanks - will have a look at this tomorrow.

---

### Post by Miljet on 2010-08-30
What I would do at this point is combine the new partitions into one and use the new partition to create a separate /home. A couple of links

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Lewian on 2010-08-31
I now used pysdm and was able to mount the new partitions. Thanks.
However, although I also did 
sudo update-grub
Windows is still offered there, and also /etc/fstab has still entries referring to /dos and /windows, which I thought should have been overwritten by the new partitions (which are now there as well).
I'll meditate about Miljet's posting when I understand why my Windows won't go.

---

### Post by oldfred on 2010-08-31
I do not think anything auto deletes entries in fstab. You will have to delete them.

sudo cp -a /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a

if sudo mount -a returns to the command line it is ok, otherwise it will give error message that  you must fix before rebooting as it may prevent rebooting.

---

### Post by Lewian on 2010-09-01
Well, I did this and also sudo update-grub, and there were no apparent problems. However, GRUB still offers to boot Windows. Perhaps I should just not bother? It doesn't exactly hurt... if it only didn't give me the feeling that something may have gone wrong...

---

### Post by oldfred on 2010-09-01
Just to see what is where and document the system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Lewian on 2010-09-02
Thanks for your efforts... this doesn't look too dodgy, does it?
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb47eb47

Partition  Boot         Start           End          Size  Id System

/dev/sda1          65,590,560    78,140,159    12,549,600  83 Linux
/dev/sda2               2,048    27,547,647    27,545,600  83 Linux
/dev/sda3          41,172,992    65,589,247    24,416,256  83 Linux
/dev/sda4          27,548,640    41,171,759    13,623,120   5 Extended
/dev/sda5          27,548,703    39,145,679    11,596,977  83 Linux
/dev/sda6          39,145,743    41,171,759     2,026,017  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b668f2a5-836a-4ec6-b3fb-341170c62afc   ext3                                     
/dev/sda2        7000f0aa-9331-4843-b154-f878fa5a2981   ext3                                     
/dev/sda3        2277a269-2990-49e7-934c-7949fb8cddd1   ext3                                     
/dev/sda5        26fa6e1a-d79e-4488-9001-638034e79b22   ext3                                     
/dev/sda6        90fd5966-8d07-49a6-badc-2566289b1f4f   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda5        /home                    ext3       (rw,relatime)
/dev/sda2        /media/sda2              ext3       (rw,errors=remount-ro)
/dev/sda3        /media/sda3              ext3       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b668f2a5-836a-4ec6-b3fb-341170c62afc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b668f2a5-836a-4ec6-b3fb-341170c62afc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Microsoft Windows XP Professional
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                            0  0  
# / was on /dev/sda1 during installation
UUID=b668f2a5-836a-4ec6-b3fb-341170c62afc  /               ext3         relatime,errors=remount-ro          0  1  
# /dos was on /dev/sda3 during installation
# UUID=A4A0DB03A0DADB3E                      /dos            ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
# /home was on /dev/sda5 during installation
UUID=26fa6e1a-d79e-4488-9001-638034e79b22  /home           ext3         relatime                            0  2  
# /windows was on /dev/sda2 during installation
# UUID=7AEE-60DE                             /windows        vfat         utf8,umask=007,gid=46               0  1  
# swap was on /dev/sda6 during installation
UUID=90fd5966-8d07-49a6-badc-2566289b1f4f  none            swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8            0  0  
/dev/sda2                                  /media/sda2     ext3         errors=remount-ro                   0  0  
/dev/sda3                                  /media/sda3     ext3         errors=remount-ro                   0  0  

=================== sda1: Location of files loaded by Grub: ===================


  35.0GB: boot/grub/menu.lst
  34.9GB: boot/grub/stage2
  35.0GB: boot/initrd.img-2.6.28-11-generic
  34.9GB: boot/initrd.img-2.6.28-15-generic
  35.0GB: boot/initrd.img-2.6.28-16-generic
  35.0GB: boot/initrd.img-2.6.28-17-generic
  35.1GB: boot/initrd.img-2.6.28-18-generic
  35.1GB: boot/initrd.img-2.6.28-19-generic
  34.9GB: boot/vmlinuz-2.6.28-11-generic
  34.9GB: boot/vmlinuz-2.6.28-15-generic
  35.0GB: boot/vmlinuz-2.6.28-16-generic
  35.0GB: boot/vmlinuz-2.6.28-17-generic
  34.9GB: boot/vmlinuz-2.6.28-18-generic
  37.9GB: boot/vmlinuz-2.6.28-19-generic
  35.1GB: initrd.img
  35.1GB: initrd.img.old
  37.9GB: vmlinuz
  34.9GB: vmlinuz.old


```

---

### Post by oldfred on 2010-09-02
I had forgotten that old grub was not too good at finding windows, so it probably is not good at deleting it.

Just go into menu.lst and delete the windows entry.

gksudo gedit /boot/grub/menu.lst

---

### Post by Lewian on 2010-09-03
Worked (and made me also figure out another thing that I was interested in some time ago). Thanks a lot!

---

