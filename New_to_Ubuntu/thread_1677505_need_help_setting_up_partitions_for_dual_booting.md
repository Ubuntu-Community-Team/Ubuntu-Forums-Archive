---
title: "need help setting up partitions for dual booting"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by antiprice666 on 2011-01-28
I'm getting ready to install Ubuntu 10.04.1 LTS for the first time.  I want to dual boot with windows xp.  I have made the partitions needed but I am unclear as to how they should be set up.  
     As it stands right now I have 4 partitions on my HD.  sdb1 is the Windows partition.  I am unclear how to designate sdb2/3/4.  Right now I have all partitions as primary.  I am assuming this is wrong.  Also I'm not sure which file type the Ubuntu partitions should be.  As they are now: sdb2 31.5 GB (ntfs) :sdb3 4.3 GB (linux-swap) :sdb4 109.4 GB (ntfs).  I basically guessed at making sdb3 linux-swap seeing as how it is a swap partition which may be wrong.  If someone could shed a little light on which file system type I should be using for each partition that would be great.
     I am in the begining of the install process and am stuck.  I am at step 5 of 8 Prepare Partitions.  It lists all of my partitions but when I try to go to the next step it says "No Root File System is defined" and send me back to this screen again.

---

### Post by Nytram on 2011-01-28
Hi Antiprice666, I can recommend a partition setup for dual-booting, but I'll need some details from you:

-Is your computer a laptop or desktop?

-How much memory does your system have?

-Are you willing to change the sizes of your existing partitions, or do you want a "best fit" for what you already have?

---

### Post by antiprice666 on 2011-01-28
> **Nytram said:**
> Hi Antiprice666, I can recommend a partition setup for dual-booting, but I'll need some details from you:

-Is your computer a laptop or desktop?

-How much memory does your system have?

-Are you willing to change the sizes of your existing partitions, or do you want a "best fit" for what you already have?


-desktop....Installing Ubuntu 10.04.1 LTS
-4 gigs
-sure Ill change them to whatever you recommend.  I would also like recommendations for what file type each partition should be.  I'm not very tech savy so I don't know the difference between fat 32,ntfs, etc.
 
oh and I am dedicating 133 gigs total for Ubuntu.  My HD is 233 gigs but I have 100 gigs partitioned for Windows XP

---

### Post by oldfred on 2011-01-28
You cannot use NTFS for any Linux partitions, but it is a good idea to create a shared NTFS partition for any data you want to share between Windows & Linux. I do not recommend writing into another system's system partition, reading is ok and repairs if necessary are ok. But regular writing can lead to issues.

You can only have 4 primary partitions and the extended which can hold many logical partitions counts as one of the primary partitions.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Also how large is your hard drive and how much are you initially planning on allocating to Ubuntu?

My standard recommendation, but each user has different needs and it depends greatly on what you want. I only had / (root) and swap for a couple of years, but now have several installs of Ubuntu on different drives with many partitions.


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Nytram on 2011-01-28
This is what I'd go with:

sdb2 20gb  Ext4 Root partition, referred to as /
sdb3 109gb Ext4 Home partition, referred to as ~
sdb4 4gb   Swap

Partitioning isn't an exact science, some of it comes down to how you individually use your computer. Having 2 partitions for Windows is something I do, so if I reinstall Windows I don't lose all my data. To do that, you could have root and home as one partition, or create an extended partition.. it's courses for horses really.

---

### Post by Quackers on 2011-01-28
My personal choice would be to leave any existing recovery partition and XP partition alone. I would then create an extended partition, occupying the rest of the hard drive. Within that partition you can then create as many partitions as you want to. I would have a root partition (/), a /home partition, and, possibly a small swap partition ( or a 4.5GB swap partition, if you intend to use hibernation). This way you will not be in any danger of exceeding the 4 primary partitions limit of the disc.
I would create these new partitions in gparted on the Ubuntu Live cd/usb, or, during the installation of Ubuntu in the partitioning stage.

---

### Post by antiprice666 on 2011-01-28
ok this is where I am at now....


sdb2 31.5gb mountpoint / primary ext4
sdb3 109gb mountpoint /home primary ext4
sdb4 4gb primary swap (wasnt given the option of setting a mountpoint during the Ubuntu installation.)


I tried, before the installation, to change sdb3 and 4 to logical instead of primary with gparted but wasn't able highlight logical in the dropdown menu.  I could only highlight primary or extended so I kept them both primary.  Does this matter?


I was able to finish the installation with the way I have the partitions set up now...but when I restarted windows booted.  Am I suppose to be getting an option of which OS I want to boot?

Also for some reason my USB stick won't boot now I get "Geom error"....and yes I did change the boot order back to USB to boot from my stick.  8^)

USB stick fixed.

---

### Post by Quackers on 2011-01-28
No, Ubuntu is supposed to boot up directly at first.
The only trouble with all primary partitions is the lack of flexibility in the future. Now if you want a new partition, you may need to delete one first. With an extended partition that wouldn't be a problem.
I would suggest you get the stick booting again (I don't know what Geom error is) and then load up the live desktop and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by antiprice666 on 2011-01-29
here is the code that was requested. 
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     7,837,695     7,837,664   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620   266,229,179    61,432,560  83 Linux
/dev/sdb3         266,229,180   480,198,914   213,969,735  83 Linux
/dev/sdb4         480,198,915   488,392,064     8,193,150  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       5e679113-2457-2841-a012-0b20eab9862c   ext2       casper-rw                     
/dev/sda1        A8DC-A953                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CA5818085817F1C5                       ntfs                                     
/dev/sdb2        2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9   ext4                                     
/dev/sdb2        2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9   ext4       /                             
/dev/sdb3        4c4a1ff2-5f92-455c-9b4f-bfaaf05db61e   ext4       /home                         
/dev/sdb4        388154be-b4a4-4d68-af6e-b0e19f4b88d6   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9
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
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ca5818085817f1c5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=2dc235fd-a9a1-4bd8-810c-30e2e91e5fc9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=4c4a1ff2-5f92-455c-9b4f-bfaaf05db61e /home           ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=388154be-b4a4-4d68-af6e-b0e19f4b88d6 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 131.0GB: boot/grub/core.img
 124.3GB: boot/grub/grub.cfg
 131.0GB: boot/initrd.img-2.6.32-24-generic
 131.0GB: boot/vmlinuz-2.6.32-24-generic
 131.0GB: initrd.img
 131.0GB: vmlinuz 
```


Sorry it took so long.  Hope this is what you need.

---

### Post by Quackers on 2011-01-29
Yes, thanks.
It appears that you forgot to install grub :-)
If you boot from the live usb (which appears to be sda here) and select "try ubuntu" you can fix that up.
When the desktop loads open up a terminal and copy/paste these commands into it one line at a time and pressing enter after each line.
```
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Then reboot and Ubuntu should boot directly. When it does, please open a terminal and run ```
sudo update-grub
``` which should pick up the Windows Loader. If it does, reboot and boot Windows from your shiny new grub menu :-)

---

### Post by supererki on 2011-01-29
Are you already finished with partitioning ? 

Since partition table is only 64 bytes, you can create only four primary partitions. You shouldn't use them all, considering that only /boot needs to be on a primary partition. 

You should consider setting up LVM. It has some serious benefits : 
1. easy to resize
2. unlimited number of partitions.
3. logical disk doesn't have 1-1 dependency with the disk. It means you can make 1 big partition which is actually laying on 3 physical harddrives. 
4. You can create snapshots.

Downside is that you cant boot from logical device. 

So if it is not a server machine, I would create 3 partitions for linux :
/boot
/
/home

---

### Post by antiprice666 on 2011-01-29
I installed Grub and have rebooted to check.  Everything is working fine as far as I can tell....so far :P.
I know my partitioning may be sloppy but this is my first try at dual booting.  I can clean things up when I am more knowledgeable.  I'm sure I will be breaking this down and restarting a couple times.
Thanks to all that have helped.  This forum is great.  I'm sure I will be back when I get into loading drivers and customizing.

---

