---
title: "issue with grub-2 in ubuntu/CentOS dual boot."
date: 2010-05-08
forum: New to Ubuntu
---

### Post by avee137 on 2010-05-08
I have ubuntu 9.10,win7 and CentOS installed on my system.CentOS was the last
one to be installed and it replaced the grub2 of ubuntu during installation.The grub 
of CntOS was not listing ubuntu in boot option hence i recovered the ubuntu grub 
thru live CD.And now ubuntu's GRUB-2 is not listing CentOS under boot option.
i am mentioning the disk partiotion on my system below along with the contents of 
/etc/default/grub and /etc/grub.d.
(41_custom in grub.d was created by me as an attempt of some correction.proved of no use!)

please help!! 




Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x695e1c35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1874    15048704   27  Unknown
/dev/sda2   *        1874        1887      102400    7  HPFS/NTFS
/dev/sda3            1887       12722    87031808    7  HPFS/NTFS
/dev/sda4           12723       38914   210380360+   f  W95 Ext'd (LBA)
/dev/sda5           15417       15807     3140707+  82  Linux swap / Solaris
/dev/sda6           27557       28470     7341673+  83  Linux
/dev/sda7           28471       38914    83884032    7  HPFS/NTFS
/dev/sda8           12723       15416    21639523+  83  Linux
/dev/sda9           15808       17052    10000431   83  Linux
/dev/sda10          17053       17065      104391   83  Linux
/dev/sda11          17066       27556    84268926   8e  Linux LVM

Partition table entries are not in disk order

/etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"




avi@avi-laptop:/etc/grub.d$ ls
00_header        10_linux       30_os-prober  41_custom
05_debian_theme  20_memtest86+  40_custom     README



avi@avi-laptop:/etc/grub.d$ cat 40_custom 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

avi@avi-laptop:/etc/grub.d$ cat 41_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the  M-@^ xec tail M-@^ line above.

menuentry "CentOS 5.5"{                   
       set root=(hd0,9)
        linux /xen.gz-2.6.18-164.el5
        linux/boot /vmlinuz-2.6.18-164.el5xen ro root=/dev/VolGroup00/LogVol00 $
        linux/boot /initrd-2.6.18-164.el5xen.img
        }

thanks in advance!!

---

### Post by cariboo on 2010-05-08
What output do you get when you run:

```
sudo update-grub
```

---

### Post by avee137 on 2010-05-08
> **cariboo907 said:**
> What output do you get when you run:

```
sudo update-grub
```


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

---

### Post by JerichoKru on 2010-05-08
> **avee137 said:**
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

Is the CentOS partition recognized by Ubuntu (as in, does it show up in Nautilus)?  If so, is it mounted?  Also, what filesystem is used for CentOS?

---

### Post by avee137 on 2010-05-08
> **JerichoKru said:**
> Is the CentOS partition recognized by Ubuntu (as in, does it show up in Nautilus)?  If so, is it mounted?  Also, what filesystem is used for CentOS?

no idea about Nautilus but CentOS partition does nt show up under 'Places' dropdown.file system used for CentOS is ext3.

---

### Post by dagdeniz on 2010-05-08
i'm not an expert, but here is what i can tell: 
the custom entry you created may be wrong and may be with wrong syntax (for example, i think, there should be a space before the bracket; there may be space after "linux" in the fourth line and no space in the path, etc.). secondly, you probably need the UUID of the partition that CentOS is installed. thirdly, you may need a separate initrd line. you should also indicate the partition number in "root=" query must either UUID or the partition number, which seems hda9 in your case.  so, the entry should be like this:
```

menuentry "CentOS 5.5" {
        insmod ext2
        set root='(hd0,9)'
        search --no-floppy --fs-uuid --set here-comes-the-uuid-number
        linux /boot/vmlinuz-2.6.18-164.el5xen  root=/dev/hda9 ro quiet
        initrd /boot/initrd-2.6.18-164.el5xen.img
}

```the fifthe line of the entry may also be 

```

        linux /boot/vmlinuz-2.6.18-164.el5xen  root=UUID=here-comes-the-uuid-number ro quiet

```the linux and the initrd lines indicate the vmlinuz and initrd files in the boot directory of centos; so, you can directly look if it's written right by navigating to that directory. you can find the uuid of the partition you want in the fstab file by printing "sudo nano /etc/fstab" in the terminal.

---

### Post by avee137 on 2010-05-08
> **dagdeniz said:**
> i'm not an expert, but here is what i can tell: 
the custom entry you created may be wrong and may be with wrong syntax (for example, i think, there should be a space before the bracket; there may be space after "linux" in the fourth line and no space in the path, etc.). secondly, you probably need the UUID of the partition that CentOS is installed. thirdly, you may need a separate initrd line. you should also indicate the partition number in "root=" query must either UUID or the partition number, which seems hda9 in your case.  so, the entry should be like this:
```

menuentry "CentOS 5.5" {
        insmod ext2
        set root='(hd0,9)'
        search --no-floppy --fs-uuid --set here-comes-the-uuid-number
        linux /boot/vmlinuz-2.6.18-164.el5xen  root=/dev/hda9 ro quiet
        initrd /boot/initrd-2.6.18-164.el5xen.img
}

```the fifthe line of the entry may also be 

```

        linux /boot/vmlinuz-2.6.18-164.el5xen  root=UUID=here-comes-the-uuid-number ro quiet

```the linux and the initrd lines indicate the vmlinuz and initrd files in the boot directory of centos; so, you can directly look if it's written right by navigating to that directory. you can find the uuid of the partition you want in the fstab file by printing "sudo nano /etc/fstab" in the terminal.

I managed to get CentOS in the grub menu but when i am trying to boot thru that option,it gives an error:load the kernel first.
I thought i had given the wrong disk option hence i changed to other available options but it gives the same error.output of "fdisk -l" and "blkid" is as below .Help me to figure out on what partition kernel of CentOS lies.Or,what else could be the possible solution to the issue.

avi@avi-laptop:~$ sudo blkid
[sudo] password for avi: 
/dev/sda1: UUID="26147F9A147F6BA5" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="C0AC8048AC803AC4" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda3: UUID="088481B88481A930" LABEL="Root" TYPE="ntfs" 
/dev/sda5: UUID="b9469d27-2d6d-4943-9b60-54b5bc4ea2b6" TYPE="swap" 
/dev/sda6: UUID="e001231b-e90c-4429-8137-4a16afc19757" TYPE="ext4" 
/dev/sda7: UUID="105ED5035ED4E310" LABEL="Funterland" TYPE="ntfs" 
/dev/sda8: UUID="92da5c74-97b0-4a4e-ae5c-4b6d66c2951e" TYPE="ext4" 
/dev/sda9: UUID="fec50e60-b629-4e51-9efd-eed9fbbe80df" TYPE="ext4" 
/dev/sda10: LABEL="/boot" UUID="e12c9a72-00bc-438f-bc49-4957e02da432" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="gL8kDi-k1d9-BVbv-hhf2-w2He-q0do-rEjS3W" TYPE="LVM2_member" 



avi@avi-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x695e1c35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1874    15048704   27  Unknown
/dev/sda2   *        1874        1887      102400    7  HPFS/NTFS
/dev/sda3            1887       12722    87031808    7  HPFS/NTFS
/dev/sda4           12723       38914   210380360+   f  W95 Ext'd (LBA)
/dev/sda5           15417       15807     3140707+  82  Linux swap / Solaris
/dev/sda6           27557       28470     7341673+  83  Linux
/dev/sda7           28471       38914    83884032    7  HPFS/NTFS
/dev/sda8           12723       15416    21639523+  83  Linux
/dev/sda9           15808       17052    10000431   83  Linux
/dev/sda10          17053       17065      104391   83  Linux
/dev/sda11          17066       27556    84268926   8e  Linux LVM

Partition table entries are not in disk order

plz help..its more than 48 hrs since i am trudging thru this issue!

---

### Post by dagdeniz on 2010-05-08
(everything i wrote disappeared because of not turning javascript on :mad:! the forum should not need yahooapis!) 

it will be useful to compare the grub.conf entry for CentOS in CentOS partition and the last form of the custom entry you created for CentOS in grub.cfg in Ubuntu. can you post both of them here? 

a small note: are you keeping in mind that grub legacy and grub2 are treating the partition numbers differently? i mean, while, e.g., "sda5" means "(hd0,4)" for grub legacy - numbers start from zero -, it means "(hd0,5)" for grub2 - numbers start from one. 

another small note: now you, at least, are able to create a kernel panic after grub (that's grub2 sees the CentOS entry). you can now highlight CentOS entry in grub menu and press "e" to edit the entry (temporarily), so you can see the results immediately. sometimes a very small syntax fault may create a kernel panic.

---

### Post by oldfred on 2010-05-08
It looks like you boot is in sda10 and your install is in sda11 an LVM. Part of your entry has to be the boot directory and part has to be the root directory.

I would look at the centos boot entry even if it is old grub based which then has slightly different format and partition numbering.

Another alternative is chainbooting where you install Centos boot loader to its boot partition and chainboot from grub2.

To see entire system:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by avee137 on 2010-05-08
> **oldfred said:**
> It looks like you boot is in sda10 and your install is in sda11 an LVM. Part of your entry has to be the boot directory and part has to be the root directory.

I would look at the centos boot entry even if it is old grub based which then has slightly different format and partition numbering.

Another alternative is chainbooting where you install Centos boot loader to its boot partition and chainboot from grub2.

To see entire system:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

```

avi@avi-laptop:~$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda11: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x695e1c35

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,099,455    30,097,408  27 Hidden HPFS/NTFS
/dev/sda2    *     30,099,456    30,304,255       204,800   7 HPFS/NTFS
/dev/sda3          30,304,256   204,367,871   174,063,616   7 HPFS/NTFS
/dev/sda4         204,378,991   625,139,711   420,760,721   f W95 Ext d (LBA)
/dev/sda5         247,658,040   253,939,454     6,281,415  82 Linux swap / Solaris
/dev/sda6         442,687,203   457,370,549    14,683,347  83 Linux
/dev/sda7         457,371,648   625,139,711   167,768,064   7 HPFS/NTFS
/dev/sda8         204,378,993   247,658,039    43,279,047  83 Linux
/dev/sda9         253,939,518   273,940,379    20,000,862  83 Linux
/dev/sda10        273,940,443   274,149,224       208,782  83 Linux
/dev/sda11        274,149,288   442,687,139   168,537,852  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       e12c9a72-00bc-438f-bc49-4957e02da432   ext3       /boot                         
/dev/sda11       gL8kDi-k1d9-BVbv-hhf2-w2He-q0do-rEjS3W LVM2_member                               
/dev/sda1        26147F9A147F6BA5                       ntfs       Recovery                      
/dev/sda2        C0AC8048AC803AC4                       ntfs       System Reserved               
/dev/sda3        088481B88481A930                       ntfs       Root                          
/dev/sda5        b9469d27-2d6d-4943-9b60-54b5bc4ea2b6   swap                                     
/dev/sda6        e001231b-e90c-4429-8137-4a16afc19757   ext4                                     
/dev/sda7        105ED5035ED4E310                       ntfs       Funterland                    
/dev/sda8        92da5c74-97b0-4a4e-ae5c-4b6d66c2951e   ext4                                     
/dev/sda9        fec50e60-b629-4e51-9efd-eed9fbbe80df   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 92da5c74-97b0-4a4e-ae5c-4b6d66c2951e
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
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 92da5c74-97b0-4a4e-ae5c-4b6d66c2951e
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=92da5c74-97b0-4a4e-ae5c-4b6d66c2951e ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 92da5c74-97b0-4a4e-ae5c-4b6d66c2951e
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=92da5c74-97b0-4a4e-ae5c-4b6d66c2951e ro single  splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 92da5c74-97b0-4a4e-ae5c-4b6d66c2951e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=92da5c74-97b0-4a4e-ae5c-4b6d66c2951e ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 92da5c74-97b0-4a4e-ae5c-4b6d66c2951e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=92da5c74-97b0-4a4e-ae5c-4b6d66c2951e ro single  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 26147f9a147f6ba5
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set c0ac8048ac803ac4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=92da5c74-97b0-4a4e-ae5c-4b6d66c2951e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=fec50e60-b629-4e51-9efd-eed9fbbe80df /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b9469d27-2d6d-4943-9b60-54b5bc4ea2b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 109.2GB: boot/grub/core.img
 105.6GB: boot/grub/grub.cfg
 104.9GB: boot/initrd.img-2.6.31-14-generic
 105.6GB: boot/initrd.img-2.6.31-21-generic
 105.3GB: boot/vmlinuz-2.6.31-14-generic
 104.9GB: boot/vmlinuz-2.6.31-21-generic
 105.6GB: initrd.img
 104.9GB: initrd.img.old
 104.9GB: vmlinuz
 105.3GB: vmlinuz.old

============================ sda10/grub/grub.conf: ============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,9)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,9)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-164.el5xen)
    root (hd0,9)
    kernel /xen.gz-2.6.18-164.el5 
    module /vmlinuz-2.6.18-164.el5xen ro root=/dev/VolGroup00/LogVol00 rhgb quiet
    module /initrd-2.6.18-164.el5xen.img
title Other
    rootnoverify (hd0,1)
    chainloader +1

=================== sda10: Location of files loaded by Grub: ===================


 140.2GB: grub/grub.conf
 140.2GB: grub/menu.lst
 140.2GB: grub/stage2
 140.2GB: initrd-2.6.18-164.el5xen.img
 140.2GB: vmlinuz-2.6.18-164.el5xen



```

this is what i got.seems like all information to fix this issue but being new to linux i can't do much.plz help me to come out of this.It has taken a lot of time though i learned a bit while tackling this issue!

---

### Post by dagdeniz on 2010-05-08
it's installed on sda10.

```
menuentry "CentOS 5.5" {
        insmod ext2
        set root='(hd0,10)'
        search --no-floppy --fs-uuid --set e12c9a72-00bc-438f-bc49-4957e02da432
        linux /boot/vmlinuz-2.6.18-164.el5xen  root=/dev/hda10 ro quiet
        initrd /boot/initrd-2.6.18-164.el5xen.img
}
```or
```
menuentry "CentOS 5.5" {
        insmod ext2
        set root='(hd0,10)'
        search --no-floppy --fs-uuid  --set e12c9a72-00bc-438f-bc49-4957e02da432
        linux /boot/vmlinuz-2.6.18-164.el5xen  root=UUID=e12c9a72-00bc-438f-bc49-4957e02da432
        initrd /boot/initrd-2.6.18-164.el5xen.img
}
```(by the way, i've noticed that i've forgotten the "set" parameter on the above post.)
do any of these two work?

i don' think adding the kernel line* will be necessary (i've not seen such a line in grub2 so far) but you may still add it between search and linux line if the above entry doesn't work. 

*kernel line in your grub.conf: 
```
        kernel /xen.gz-2.6.18-164.el5 
```

hope it helps, see you tomorrow, i'm going to sleep now ;)

---

### Post by oldfred on 2010-05-08
I think dagdeniz is close. The boot info script does not show the centOS kernels in /boot so I would try without that. What I do not know is when grub2 stops being in control of start up and centos takes over.

Again these are just guesses, copy into 40_custom and run update grub to see if either works. The root=with a LVM - I do not know if it should be a UUID or the VolGroup entry:

menuentry "CenOS (2.6.18-164.el5xen)" {
set root=(hd0,9)
linux /vmlinuz-2.6.18-164.el5xen ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd /initrd-2.6.18-164.el5xen.img
}

menuentry "CenOS (2.6.18-164.el5xen)" {
set root=(hd0,9)
linux /vmlinuz-2.6.18-164.el5xen ro root=UUID=gL8kDi-k1d9-BVbv-hhf2-w2He-q0do-rEjS3W rhgb quiet
initrd /initrd-2.6.18-164.el5xen.img
}


If these do not work I know we can install grub to the /boot centos partition and add this to 40_custom:

This requires Centos' grub in sda10.

menuentry "Chainload Other System on sda10" {
set root=(hd0,10)
chainloader +1

---

### Post by avee137 on 2010-05-09
> **oldfred said:**
> I think dagdeniz is close. The boot info script does not show the centOS kernels in /boot so I would try without that. What I do not know is when grub2 stops being in control of start up and centos takes over.

Again these are just guesses, copy into 40_custom and run update grub to see if either works. The root=with a LVM - I do not know if it should be a UUID or the VolGroup entry:

menuentry "CenOS (2.6.18-164.el5xen)" {
set root=(hd0,9)
linux /vmlinuz-2.6.18-164.el5xen ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd /initrd-2.6.18-164.el5xen.img
}

menuentry "CenOS (2.6.18-164.el5xen)" {
set root=(hd0,9)
linux /vmlinuz-2.6.18-164.el5xen ro root=UUID=gL8kDi-k1d9-BVbv-hhf2-w2He-q0do-rEjS3W rhgb quiet
initrd /initrd-2.6.18-164.el5xen.img
}


If these do not work I know we can install grub to the /boot centos partition and add this to 40_custom:

This requires Centos' grub in sda10.

menuentry "Chainload Other System on sda10" {
set root=(hd0,10)
chainloader +1

i tried the codes suggested by you and dagdeniz but its not working.it gives the same error 'kernel not found'

---

### Post by oldfred on 2010-05-09
I do not know centOS enough to know an exact entry. I would suggest installing centOS grub to the centos partition and add the chainboot entry.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Re-Install GRUB, if file locations are un-known
long story

1. Boot your computer up with Live CD
2. Open a terminal window (or switch to a tty ).
3. Type 'sudo grub'.
   Should get text of which last line is "grub>"
4. Type "find /boot/grub/stage1".
   You'll get a response like "(hd0,9)".
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,9)" ( what you got in step #4 hard disk + boot partition )
6. Type
       "setup (hd0)", to install GRUB to MBR, prefered method
OR     "setup [COLOR=Red](hd0,9[/COLOR])" (whatever your hard disk + partition # is)
                       to install GRUB to a  partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

then add this to the grub2 40_custom:
This requires Centos' grub in sda10.

menuentry "Chainload CentOS on sda10" {
set root=(hd0,10)
chainloader +1

---

### Post by avee137 on 2010-05-09
> **oldfred said:**
> I do not know centOS enough to know an exact entry. I would suggest installing centOS grub to the centos partition and add the chainboot entry.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Re-Install GRUB, if file locations are un-known
long story

1. Boot your computer up with Live CD
2. Open a terminal window (or switch to a tty ).
3. Type 'sudo grub'.
   Should get text of which last line is "grub>"
4. Type "find /boot/grub/stage1".
   You'll get a response like "(hd0,9)".
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,9)" ( what you got in step #4 hard disk + boot partition )
6. Type
       "setup (hd0)", to install GRUB to MBR, prefered method
OR     "setup [COLOR=Red](hd0,9[/COLOR])" (whatever your hard disk + partition # is)
                       to install GRUB to a  partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

then add this to the grub2 40_custom:
This requires Centos' grub in sda10.

menuentry "Chainload CentOS on sda10" {
set root=(hd0,10)
chainloader +1

'grub command not found'
is what i get when i type 'sudo grub' in terminal.
however, when i installed CentOS i lost my ubuntu grub and i restored the ubuntu grub using a similar method with live CD and after that this issue started.Even if i re-install the GRUB on MBR and Chainload CentOS in 40_custom,probably the scenario won't change.

---

### Post by dagdeniz on 2010-05-09
(to oldfred)
is grub installed by default in the live cd? isn't a ```
sudo apt-get install grub
``` required? i'm not sure but i kinda remember same kind of a problem...

---

### Post by oldfred on 2010-05-09
dagdeniz is correct if you use the new Ubuntu, I guess I thought to install the CentOS grub the OP would use the CentOS CD.

---

### Post by avee137 on 2010-05-13
Nothing was working out well so i wiped out CentOS and ubuntu partitions and reinstalled everything once again.I installed CentOS first with its grub on its / partition rather than on MBR of the disk.Then i installed ubuntu by creating a / and a /home partition on the empty part of the disk.Even though the installation completed successfully, -when I am booting the pc, I am ending up with grub rescue prompt.  - i tried to recover grub using live ubuntu cd by mounting the / ubuntu partition.when i  moved to /boot/grub directory,its empty.  -Further besides,when i see the disk thru disk utility on ubuntu, i do not see / and /home mount point for CentOS partitions,though partitions exist.  I know I have messed up badly.Please suggest what should i do.

---

### Post by oldfred on 2010-05-13
With multiple operating systems you need to know and use this tool:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by ublintu on 2010-08-04
Hi,
After several install and a few kernel panic message, I could successfully dual booted with Ubuntu 10.04 and centos5.5 :
1. I installed every OS, Ubuntu was the last one (except centos)
2. I left an unpartitioned free place for centos
3. During centos installation, at partitioning, choose "create custom layout"
4. Choose the free place as / and on the next screen you can choose to do NOT install grub.

5. Reboot > in grub choose Ubuntu 10.04 (in my case centos5 already was listed there, but don't go there), because we need to edit the grub.cfg file in ubuntu
My original grub.cfg file, centos part was like this:

menuentry "CentOS release 5.5 (Final) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bc47e87e-88c6-4756-8f47-361298b23a16
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sdb3
}

I changed it for this:

menuentry "CentOS release 5.5 (Final) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set bc47e87e-88c6-4756-8f47-361298b23a16
    linux /boot/vmlinuz-2.6.18-194.el5 root=UUID=bc47e87e-88c6-4756-8f47-361298b23a16
        initrd /boot/initrd-2.6.18-194.el5.img
}

save, restart and this time I could boot in to centos

---

