---
title: "GRUB: No Such Disk"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by M_Z on 2010-02-01
I tried to install Ubuntu on my exisitng Windows 7 machine.

I have Windows 7 on an SATA drive, and I added a ATA drive that I wanted to install Ubuntu on.  

After the install I got the error on bootup "Grub:  No Such Disk"

I searched the forum for help, and while I tried a few of the commands suggested, they did not work.  I also tried reinstalling Ubuntu again and that failed.

I was getting nervous, so I used the Windows Repair tool to get Windows back up and running.

My question,  Is there a way I can try and install Ubuntu again without this bug happening again?  

My goal is to install Ubuntu without having to go to the command line.

---

### Post by zeroseven0183 on 2010-02-01
How did you install Ubuntu in Windows 7?

You can actually install Ubuntu using [Wubi]("https://help.ubuntu.com/community/Wubi") inside Windows. A guided installation on Windows will give you a choice where to install.


This [Dual Boot Ubuntu and Windows Documentation]("https://help.ubuntu.com/community/WindowsDualBoot") might help you. Browse to the section where it says "Install Ubuntu after Windows". Please make sure you backup all your data first just to be sure everything is fine (Yeah, of course, you have the recovery partition with you)

---

### Post by kansasnoob on 2010-02-02
> **M_Z said:**
> I tried to install Ubuntu on my exisitng Windows 7 machine.

I have Windows 7 on an SATA drive, and I added a ATA drive that I wanted to install Ubuntu on.  

After the install I got the error on bootup "Grub:  No Such Disk"

I searched the forum for help, and while I tried a few of the commands suggested, they did not work.  I also tried reinstalling Ubuntu again and that failed.

I was getting nervous, so I used the Windows Repair tool to get Windows back up and running.

My question,  Is there a way I can try and install Ubuntu again without this bug happening again?  

My goal is to install Ubuntu without having to go to the command line.

Ubuntu is probably installed just fine. It's more likely a matter of sorting out the boot order and which drives mbr grub was installed to.

Anyway, with all drives plugged in, boot the Ubuntu Live CD and choose "Try without changes ........". Then from the Live Desktop post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

There's a very good chance we can get this sorted for you.

---

### Post by M_Z on 2010-02-05
Here are the results:

> 
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe1ade1ad

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   226,902,059   226,885,995   f W95 Ext d (LBA)
/dev/sda5              16,128   226,902,059   226,885,932   7 HPFS/NTFS
/dev/sda2    *    226,902,060 1,905,292,934 1,678,390,875   7 HPFS/NTFS
/dev/sda3       1,905,292,935 2,930,272,064 1,024,979,130   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd34ad34a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   781,420,543   781,418,496   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a6c4430

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   468,744,569   468,744,507  83 Linux
/dev/sdc2         468,744,570   488,392,064    19,647,495   5 Extended
/dev/sdc5         468,744,633   488,392,064    19,647,432  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                 249     3,967,487     3,967,239   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        369CD0E39CD09F25                       ntfs       New Volume                    
/dev/sda3        CC78ACE178ACCC10                       ntfs       New Volume                    
/dev/sda5        8854D20B54D1FC3E                       ntfs                                     
/dev/sdb1        8090E03D90E03AF4                       ntfs       New Volume                    
/dev/sdc1        28de4018-1047-43c3-bd0b-2b7d6c9c57da   ext4                                     
/dev/sdc5        c5e851a9-b2cb-446b-8727-449f63e3a603   swap                                     
/dev/sdf1        3632-3433                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdf1        /media/3632-3433         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows XP Professional x64 Edition" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set 28de4018-1047-43c3-bd0b-2b7d6c9c57da
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 28de4018-1047-43c3-bd0b-2b7d6c9c57da
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=28de4018-1047-43c3-bd0b-2b7d6c9c57da ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 28de4018-1047-43c3-bd0b-2b7d6c9c57da
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=28de4018-1047-43c3-bd0b-2b7d6c9c57da ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 369cd0e39cd09f25
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=28de4018-1047-43c3-bd0b-2b7d6c9c57da /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=c5e851a9-b2cb-446b-8727-449f63e3a603 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdg 




---

### Post by Leppie on 2010-02-05
ubuntu and grub2 *seem* to be installed normally, you probably only need to set your ubuntu ide drive to boot first in your bios.

---

### Post by presence1960 on 2010-02-05
if sdc is set to boot first in BIOS and you get the error, is the error GRUB no such device?

If so at the GRUB menu highlight Ubuntu- don't press enter but rather press "e" to edit. use the arrow keys to navigate to the ```
--no-floppy
``` text and delete it. When that is deleted press Ctrl + x to boot. Once in ubuntu open a terminal and run ```
gksu gedit /usr/lib/grub/grub-mkconfig_lib
```
Scroll down to the line with --no-floppy and delete --no-floppy. Click Save on toolbar and close file. In terminal run ```
sudo update-grub
```

---

### Post by M_Z on 2010-02-09
I got it to boot.

And Ubuntu started the first time.  I downloaded the updates, now when I go to start Ubuntu I get the following error from GRUB,.

Error out of disk 

Failed to boot default entries

(I gave ubuntu an entire 250 gb hard drive)

---

### Post by Leppie on 2010-02-10
follow the solution here: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by M_Z on 2010-02-10
I booted with the live CD (no idea how to boot into the hard drive copy of Ubuntu).  

I edited the file, but when I run 
sudo update-grub, I get 
 grub-probe: error: cannot find a device for /

---

### Post by Leppie on 2010-02-10
booting off a livecd, do this:
```
sudo -i
mkdir -p /mnt/temp/boot
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
gedit /etc/grub.d/10_linux
```
look for the following section and comment out the last line like this:
```
menuentry "$1" {
 recordfail=1
# if  [ -n \${have_grubenv} ]; then save_env recordfail; fi
```
save and exit the file, run update-grub and reboot:
```
update-grub
exit
reboot
```

---

### Post by Mike Green9 on 2010-02-10
This may or may not be relevant - but I had quite a bit of difficulty booting from my Ubuntu 9.10 hard disk.
 
I currently am able to dual boot Windows 7 or Ubuntu.
 
When I installed Ubuntu, I did not let it go near the MBR on disk 0. Instead, there is an ADVANCED tab which I selected, and I chose to have Ubuntu install GRUB in it's own partition (in my case /dev/sdb4). (I used a Mount point of "/".)
 
I then booted W7, ran EasyBCD 2.0.0.76 and added a GRUB2 entry. It searched out the Partition Boot Record on the partition Ubuntu is residing in, and bingo, I can boot either.
 
 
Hope this helps.
 
 
M....

---

### Post by meierfra. on 2010-02-10
> no idea how to boot into the hard drive copy of Ubuntu). 

Opps. I   edited my How-To. It now includes instruction how to boot into Ubuntu:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

PS. Leppie's chroot method  from the LiveCD should work,too

---

### Post by M_Z on 2010-02-11
I tried the instructions per the Wiki.

However now when I boot I just get:

GNU GRUB version 1.97~beta4

sh:grub>


No idea of what to do now.

---

### Post by Leppie on 2010-02-12
you can boot your system like this:
```
set root=(hd0,6)
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda6 ro
initrd /intird.img
boot
```
once logged in, regenerate your grub.cfg:
```
sudo update-grub
```

---

### Post by M_Z on 2010-02-12
The code you provided did not work.  Please help, I'm about ready to give up on trying to get Ubuntu to work.  

I get 

error: file not found when I get to 
linux /vmlinuz root=/dev/sda6 ro

---

### Post by meierfra. on 2010-02-12
> I tried the instructions per the Wiki.
So you were able to boot into Ubuntu after deleting the line

 if  [ -n \${have_grubenv} ]; then save_env recordfail; fi

at boot up?

> 
I get
error: file not found when I get to
linux /vmlinuz root=/dev/sda6 ro 


 Try

```

search -f --set /vmlinuz
probe -u --set=uuid $root
linux /vmlinuz root=UUID=$uuid ro
initrd /initrd.img
boot 
```

If that does not work, report all error messages you got and try

```
set root=(hd0,1)
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sdc1 ro
initrd /initrd.img
boot
```

Once you booted in Ubuntu, run "sudo update-grub". If that did not solve your problem, run the boot info script again and post the new "RESULTS.txt".

---

### Post by M_Z on 2010-02-12
search -f --set /vmlinuz

error:  no such device:  /vmlinuz

probe -u --set=uuid $root

error:  couldn't open device

linux /vmlinuz root=UUID=$uuid ro

error:  no such partition

initrd /initrd.img

error:  you need to load the kernel first.

boot

---

### Post by khjui on 2010-02-12
I used Wubi and burned it onto a disk. I would say to run Wubi without getting that error (I got it), right click on the disk drive in My Computer (With the disk in), and select "Explore". Then select "Wubi.Exe", right click it and press "Run As Administrator".
That worked for me.

---

### Post by M_Z on 2010-02-12
I can't boot into windows and my only computer right now is a netbook so i can't burn any cds.

---

### Post by meierfra. on 2010-02-12
Did you try my second suggestion?
Could you post a new RESULTS.txt?
Were you able to boot into Ubuntu following the "temporary  solution" in the Wiki?

Could also post the output of

```
ls

set
```

at the "grub sh?" prompt.

---

### Post by M_Z on 2010-02-12
at set root hd(0,1) I get

error:  not an assignment

For ls

(hd0) (hd0,5) (hd0,3) (hd0,2) (hd1) (hd1,1) (hd2) (hd2,1) (fd0)

for set
?=0
color_highlight=
color_normal=
pager=
prefix=(UUID-28d.......etc..)/boot/grub
root=UUID=28........

---

### Post by meierfra. on 2010-02-12
> at set root hd(0,1) I get

error: not an assignment
The  command is


```
set root[COLOR="Red"]=[/COLOR](hd0,1)

```

---

### Post by meierfra. on 2010-02-12
Also try the same commands with

```
set root=(hd2,1)
```

and again with

```
set root=(hd1,1)
```

And if you aren't sick of trying yet, 
see what happens if you set your Bios to boot from the Ubuntu drive.

---

### Post by M_Z on 2010-02-12
at 
linux /vmlinuz root=/dev/sdc1 ro

I get error:  file not found

for both of the options you suggested

---

### Post by meierfra. on 2010-02-12
> I get error: file not found

for both of the options you suggested 
both?  did your try all three:

set root=(hd0,1)
set root=(hd1,1)
set root=(hd2,1)

---

### Post by M_Z on 2010-02-12
all of them

---

### Post by meierfra. on 2010-02-12
Ok . Try booting from the Ubuntu drive. And if  that does not help, boot from the LiveCD and create a new RESULTS.txt

---

