---
title: "Unable to boot into lucid lynx after installing win 7"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by telovin on 2011-01-14
Hello All,
First of all a very happy new year to everyone who uses ubuntu!
I have switched to ubuntu from Nov 2009 and has been a faithful ubuntu user ever since. I recently installed win 7 ultimate.Now I am able to boot only to win 7 and when it boot up its not even showing the grub manager or an option to boot into ubuntu.Guess windows deleted grub manager. I have the live cd of karmic koala but not lucid lynx. Can i install grub manager from karmic koala live cd? Kindly help.
:confused:

---

### Post by wilee-nilee on 2011-01-14
Karmic uses the grub2 bootloader Lucid is as well, personally I would use a Lucid loaded thumb or cd, but it will probably work.

You have the Windows install disc correct, in case it doesn't, to reload its bootloader?

---

### Post by Hack.The.Pow. on 2011-01-14
here ya go

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by telovin on 2011-01-19
[SIZE=4]Hi,
I followed the ubuntu community link and tried reinstalling. But the result i got is given below.[/SIZE]

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/5CCC40A0CC407674 /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```
[SIZE=4]Also my disk partition is as follows. Kindly help.[/SIZE]

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19456   115322602+   f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686   83  Linux
/dev/sda6           10199       15297    40957686    7  HPFS/NTFS
/dev/sda7           15298       19456    33407136    7  HPFS/NTFS
```
[SIZE=4]Also in the community link it was given that .lst shows that i have grublegacy and if the version is 1.67 or hihger i should have grub2. My system boot/grub directory shows .lst but  when i checked in commmand i got the version below.
[/SIZE]
```
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
```
[SIZE="4"]Dunno what to do next[/SIZE]:confused:

---

### Post by rkillcrazy on 2011-01-19
While in Windows, if you go into **Computer Management** and then into **Disk Management** (under Storage), what drives do you see?  I'm curious if the Windows install blew away the just the boot partition or the boot partition AND the data partition(s).  From the looks of it, the boot partition has been blown away.  If that's the case, get your data off of the data drive (via a Live CD if needed) and then remove the old Linux partition(s).  Once that's complete, you may even be able to expand the system drive in Windows.  After all that, grab a copy of [Wubi]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") and give that a go.  If you go that route, you won't break boot partitions...  If that's not to your liking, you can run a full install and Ubuntu will recreate the Grub boot loader and correctly set it so you have the choice to boot into Windows or Linux.

---

### Post by telovin on 2011-01-19
Hi ,
I went to comp management n saw the partition. Pasting it here. I have karmic koala CD n upgraded it online to lucid lynx. I really don't wanna uninstall it n install it again. Is there any other way that i can install grub on MBR? Ubuntu is installed on sda5

---

### Post by Quackers on 2011-01-19
From the live cd/usb select "try ubuntu" and when the desktop loads open a terminal and run
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
You install grub to the mbr of the drive not to a partition (especially not to a Windows partition!)

---

### Post by telovin on 2011-01-19
[SIZE=4]I ran the command on the terminal and this is what I got. [/SIZE]

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
```
[SIZE=4]I have to change bios settings to boot from hard disk n see if i can see grub manager during startup. Keeping my fingers crossed[/SIZE].

---

### Post by telovin on 2011-01-19
[SIZE=2]I have the grub manager now, but its showing win xp(i have win7 now) and Iam unable to boot into ubuntu. A black screen comes up asks me to login n when I login it just doesn't do anything. Just sits there. :(.I am unable to log on to windows n ubuntu. Using live CD now :(
This is the first time i am logging onto lucid lynx after changing my motherboard n processor. Is that the reason i am unable to logon to ubuntu? I mean a black screen comes up n sits there
[/SIZE]

---

### Post by Quackers on 2011-01-19
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by telovin on 2011-01-19
[SIZE=3]Here is the boot script info:[/SIZE]

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea6eea6e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,560,639   230,645,205   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372  83 Linux
/dev/sda6         163,830,933   245,746,304    81,915,372   7 HPFS/NTFS
/dev/sda7         245,746,368   312,560,639    66,814,272   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5CCC40A0CC407674                       ntfs                                     
/dev/sda5        85a28086-45e8-476e-bd17-09e46e5ce2d5   ext3                                     
/dev/sda6        522867A5286786B7                       ntfs       works                         
/dev/sda7        80A8F33DA8F33070                       ntfs       projects                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=================== sda1: Location of files loaded by Grub: ===================


    hpGB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
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
search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set da34eea034ee7ebf
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  77.3GB: boot/grub/core.img
  77.3GB: boot/grub/grub.cfg
  77.3GB: boot/initrd.img-2.6.31-20-generic
  77.3GB: boot/initrd.img-2.6.32-23-generic
  77.2GB: boot/initrd.img-2.6.32-26-generic
  77.3GB: boot/vmlinuz-2.6.31-20-generic
  77.3GB: boot/vmlinuz-2.6.32-23-generic
  77.3GB: boot/vmlinuz-2.6.32-26-generic
  77.2GB: initrd.img
  77.3GB: initrd.img.old
  77.3GB: vmlinuz
  77.3GB: vmlinuz.old
```

---

### Post by Quackers on 2011-01-19
So Ubuntu boots ok, yes?
You have a Ubuntu boot file in with your Windows boot files, that probably won't go down well with Windows. Have you tried booting the Windows XP entry? What happens?

---

### Post by Quackers on 2011-01-19
So Ubuntu boots ok, yes?
You have a Ubuntu boot file in with your Windows boot files, that probably won't go down well with Windows. Have you tried booting the Windows XP entry? What happens?

---

### Post by hansolo4949 on 2011-01-19
Ouch. You completely wiped out GRUB when you installed windows 7. Quite frankly, i'd just save some grief and wipe everything clean. I have seen this happen time, and time again, someone has messed up their computer because they installed Windows AFTER Ubuntu, which is a big no-no. Then, everyone tries to help them, and it just ends up destroying their system, no disrespect intended to any forum members. I would try running sudo update-grub2, and see if that helps, if there is a way to do that from the livecd.

I hope we can sort this out!

---

### Post by Quackers on 2011-01-19
I've already replied to you in the last 10 minutes, but the post is not appearing. It is impossible at the moment to help you like this. I can't post anything at all, and will be surprised if you get this message. I apologise. Your problems are definitely fixable, so don't give up. I will return later in the evening to assist if I can make posts. If you get this message!

---

### Post by hansolo4949 on 2011-01-19
Ouch. You completely wiped out GRUB when you installed windows 7. Quite frankly, i'd just save some grief and wipe everything clean. I have seen this happen time, and time again, someone has messed up their computer because they installed Windows AFTER Ubuntu, which is a big no-no. Then, everyone tries to help them, and it just ends up destroying their system, no disrespect intended to any forum members. I would try running sudo update-grub2, and see if that helps, if there is a way to do that from the livecd.

I hope we can sort this out!

---

### Post by telovin on 2011-01-19
I tried booting into the win xp, it says no such device(I have win7 now). But I am able to log on to lucid lynx now. Unable to boot into win7 as grub manager shows win xp instead of 7. I guess lynx n win7 don't go together huh?

---

### Post by hansolo4949 on 2011-01-19
I think we're getting close!


You should boot Ubuntu and run sudo update-grub2.

See if that helps anything:)

---

### Post by telovin on 2011-01-19
I tried booting into the win xp, it says no such device(I have win7 now). But I am able to log on to lucid lynx now. Unable to boot into win7 as grub manager shows win xp instead of 7. I guess lynx n win7 don't go together huh?

---

### Post by telovin on 2011-01-19
I tried booting into the win xp, it says no such device(I have win7 now). But I am able to log on to lucid lynx now. Unable to boot into win7 as grub manager shows win xp instead of 7. I guess lynx n win7 don't go together huh?

---

### Post by telovin on 2011-01-19
[SIZE="3"]Thanks Quackers for being so patient  and helping me out.  
 I did try updating grub but i got the following result.[/SIZE]


```
head: cannot open `/boot/grub/video.lst' for reading: No such file or directory
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/Boot
boot: No such file or directory
done
```

---

### Post by telovin on 2011-01-19
[SIZE="3"]Thanks Quackers for being so patient  and helping me out. Its 10.30pm here. I login early morning. 
 I did try updating grub but i got the following result.[/SIZE]


```
head: cannot open `/boot/grub/video.lst' for reading: No such file or directory
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/Boot
boot: No such file or directory
done
```

---

### Post by telovin on 2011-01-19
[SIZE="3"]Thanks Quackers for being so patient  and helping me out. Its 10.30pm here. I login early morning. 
 I did try updating grub but i got the following result.[/SIZE]


```
head: cannot open `/boot/grub/video.lst' for reading: No such file or directory
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/Boot
boot: No such file or directory
done
```

---

### Post by telovin on 2011-01-19
[SIZE="3"]Thanks Quackers for being so patient  and helping me out. Its 10.30pm here. I login early morning. 
Hansolo I did try updating grub but i got the following result.[/SIZE]


```
head: cannot open `/boot/grub/video.lst' for reading: No such file or directory
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/Boot
boot: No such file or directory
done
```

---

### Post by telovin on 2011-01-19
I have changed the boot priority to boot from hard disk.
Now when I boot up and look at grub manager, there is no entry of windows. Only Ubuntu entries n memtests are seen!

---

### Post by Quackers on 2011-01-19
Sorry for my absence!
So that we can see what has changed in your system, will you please re-run the boot script and post the new output, thanks.

---

### Post by telovin on 2011-01-20
[SIZE="3"]Here is the new boot script[/SIZE]

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,560,639   230,645,205   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372  83 Linux
/dev/sda6         163,830,933   245,746,304    81,915,372   7 HPFS/NTFS
/dev/sda7         245,746,368   312,560,639    66,814,272   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5CCC40A0CC407674                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        85a28086-45e8-476e-bd17-09e46e5ce2d5   ext3                                     
/dev/sda6        522867A5286786B7                       ntfs       works                         
/dev/sda7        80A8F33DA8F33070                       ntfs       projects                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=vinu)


=================== sda1: Location of files loaded by Grub: ===================


    hpGB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768x8
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
search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/11_memtest86+_proxy ###
### END /etc/grub.d/11_memtest86+_proxy ###

### BEGIN /etc/grub.d/12_os-prober ###
### END /etc/grub.d/12_os-prober ###

### BEGIN /etc/grub.d/13_custom_proxy ###
### END /etc/grub.d/13_custom_proxy ###

### BEGIN /etc/grub.d/14_custom_proxy ###
### END /etc/grub.d/14_custom_proxy ###

### BEGIN /etc/grub.d/15_custom_proxy ###
### END /etc/grub.d/15_custom_proxy ###

### BEGIN /etc/grub.d/16_custom_proxy ###
### END /etc/grub.d/16_custom_proxy ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  77.3GB: boot/grub/core.img
  77.2GB: boot/grub/grub.cfg
  77.3GB: boot/initrd.img-2.6.31-20-generic
  77.3GB: boot/initrd.img-2.6.32-23-generic
  77.2GB: boot/initrd.img-2.6.32-26-generic
  77.3GB: boot/initrd.img-2.6.32-27-generic
  77.3GB: boot/vmlinuz-2.6.31-20-generic
  77.3GB: boot/vmlinuz-2.6.32-23-generic
  77.3GB: boot/vmlinuz-2.6.32-26-generic
  77.2GB: boot/vmlinuz-2.6.32-27-generic
  77.3GB: initrd.img
  77.2GB: initrd.img.old
  77.2GB: vmlinuz
  77.3GB: vmlinuz.old
```

---

### Post by telovin on 2011-01-20
[SIZE="3"]Here is the new boot script[/SIZE]

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,560,639   230,645,205   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372  83 Linux
/dev/sda6         163,830,933   245,746,304    81,915,372   7 HPFS/NTFS
/dev/sda7         245,746,368   312,560,639    66,814,272   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5CCC40A0CC407674                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        85a28086-45e8-476e-bd17-09e46e5ce2d5   ext3                                     
/dev/sda6        522867A5286786B7                       ntfs       works                         
/dev/sda7        80A8F33DA8F33070                       ntfs       projects                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=vinu)


=================== sda1: Location of files loaded by Grub: ===================


    hpGB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768x8
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
search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
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

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 85a28086-45e8-476e-bd17-09e46e5ce2d5
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/11_memtest86+_proxy ###
### END /etc/grub.d/11_memtest86+_proxy ###

### BEGIN /etc/grub.d/12_os-prober ###
### END /etc/grub.d/12_os-prober ###

### BEGIN /etc/grub.d/13_custom_proxy ###
### END /etc/grub.d/13_custom_proxy ###

### BEGIN /etc/grub.d/14_custom_proxy ###
### END /etc/grub.d/14_custom_proxy ###

### BEGIN /etc/grub.d/15_custom_proxy ###
### END /etc/grub.d/15_custom_proxy ###

### BEGIN /etc/grub.d/16_custom_proxy ###
### END /etc/grub.d/16_custom_proxy ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=85a28086-45e8-476e-bd17-09e46e5ce2d5 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  77.3GB: boot/grub/core.img
  77.2GB: boot/grub/grub.cfg
  77.3GB: boot/initrd.img-2.6.31-20-generic
  77.3GB: boot/initrd.img-2.6.32-23-generic
  77.2GB: boot/initrd.img-2.6.32-26-generic
  77.3GB: boot/initrd.img-2.6.32-27-generic
  77.3GB: boot/vmlinuz-2.6.31-20-generic
  77.3GB: boot/vmlinuz-2.6.32-23-generic
  77.3GB: boot/vmlinuz-2.6.32-26-generic
  77.2GB: boot/vmlinuz-2.6.32-27-generic
  77.3GB: initrd.img
  77.2GB: initrd.img.old
  77.2GB: vmlinuz
  77.3GB: vmlinuz.old
```

[SIZE="3"]I also downloaded start up manager( i dint find any good use with that) and grub customizer. There is a portion which says new entries but i dunno which script to add there so that win 7 entry comes up on grub.[/SIZE]

---

### Post by Quackers on 2011-01-20
Does Ubuntu boot normally now?
If so, please open a terminal and run ```
sudo update-grub
```
and watch to see if the Windows Loader is picked up.
If it is, please reboot and try booting Windows.
The Windows Loader may not be picked up because you now have /boot/grub/core.img
 in with your Windows boot files. It may cause a problem. We'll see!

---

### Post by telovin on 2011-01-20
[SIZE="3"]Wow, its such a relief to see u online! Posting the results of sudo update grub. Looks like no windows entry.[/SIZE]

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
```

---

### Post by Quackers on 2011-01-20
Your boot script output is not entirely standard.
In particular, your sda5/boot/grub/grub.cfg: output lists
```
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/11_memtest86+_proxy ###
### END /etc/grub.d/11_memtest86+_proxy ###

### BEGIN /etc/grub.d/12_os-prober ###
### END /etc/grub.d/12_os-prober ###

### BEGIN /etc/grub.d/13_custom_proxy ###
### END /etc/grub.d/13_custom_proxy ###

### BEGIN /etc/grub.d/14_custom_proxy ###
### END /etc/grub.d/14_custom_proxy ###

### BEGIN /etc/grub.d/15_custom_proxy ###
### END /etc/grub.d/15_custom_proxy ###

### BEGIN /etc/grub.d/16_custom_proxy ###
### END /etc/grub.d/16_custom_proxy ###
```
which are all non-standard to my knowledge. Do any of these file names ring a bell to you? Have you created them?

I am unsure, but suspect this is the reason for the following output from update-grub
```
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
```
which is also non-standard.
os-prober is normally  /etc/grub.d/30_os-prober ###

---

### Post by telovin on 2011-01-20
[SIZE="3"]No Idea, I never created them.  I did use grub customizer yesterday to remove memtests from grub. There were too many entries on grub.[/SIZE]

---

### Post by Quackers on 2011-01-20
Please go to System > Admin > Synaptic Package Manager and in the search box enter ```
os-prober
```
It will appear in the main window. Does it have a green box on its left (is it installed, in other words)?

---

### Post by telovin on 2011-01-20
[SIZE="3"]It does have a green mark. Seems like its installed![/SIZE]

---

### Post by Quackers on 2011-01-20
I really don't know what to suggest for the moment. I have attempted to enlist professional help for you. Watch this space!

---

### Post by telovin on 2011-01-20
[SIZE="3"]Ok. Thanks for being so patient n thanks a lot for helping me out.[/SIZE]

---

### Post by Quackers on 2011-01-20
I want to know why it's not working as well :-)

---

### Post by telovin on 2011-01-20
[SIZE=3]Meanwhile I'll try finding ways to add win7 boot entry to grub through grub customizer.(If ever its possible!)[/SIZE]

---

### Post by telovin on 2011-01-20
[SIZE="3"]I am looking at grub customizer, and under os prober,new entries, i am unable to add win boot loader script. Dunno what to do next??[/SIZE] :(

---

### Post by Quackers on 2011-01-20
Sorry telovin, I contacted a member and asked for his help yesterday, but I forgot to include a link for him. I'm really sorry for the delay!
Hopefully guidance will appear soon :-)

---

### Post by drs305 on 2011-01-20
> 
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done[/code]
which is also non-standard.
os-prober is normally  /etc/grub.d/30_os-prober ###

This is normally caused by the problem identified earlier in the thread - having core.img in the Windows boot partition.

From Ubuntu or a LiveCD or however else you can access your systems, you need to delete the /boot folder *from sda1 (Windows)*.

You should be able to do this from a normally-running Ubuntu OS, or to do this from a LiveCD, mount the Windows partition, then open a file browser as root and remove the /boot folder (make sure you get the correct one, which should have a "grub" subfolder and contains the "core.img" file).

```
sudo mount /dev/sda1 /mnt
gksu nautilus /mnt
```
You should see /boot. That is the folder you need to remove. Once you do so the os-prober file should work as it is supposed to. 

Unmount sda1, then mount your Ubuntu partition again (if you are on the LiveCD) and make sure grub is looking at the correct folders/files. It should already be doing so, but do it anyway:
```
sudo umount /dev/sda1
sudo mount /dev/sda5 /mnt # If on the LiveCD only
sudo grub-install --root-directory=/mnt /dev/sda  # If on the LiveCD only
sudo grub-install /dev/sda # If on normal Ubuntu

```

Reboot if on the LiveCD, run "sudo update-grub" and os-prober should work and add Windows to your Grub2 menu.

---

### Post by Quackers on 2011-01-20
Thanks drs305, I'll know next time :-)

---

### Post by telovin on 2011-01-21
Hi,
 sorry Drs305 n quackers, i just saw ur posts now. Yesterday, I tried adding a custom menu to grub (I had followed some source page to add a custom.cfg. I guess i messed it up somewhere) . After that, my grub was not seen n when starting up computer, it was directly going to ubuntu .I didn't try going back to default grub as i was frustrated. So I tried to upgrade it to maverick. 

So by the time I saw both of ur posts, maverick installation was stuck at the following meassage for almost 6-7 hours.
```
 unpacking kcast about 12 minutes remaining 
```So I restarted the system n now it shows
```
 install problem. Was not able to configure gnome smthing smthing.
```So I am currently logged in using live cd.
 

Drs305,I followed your instructions through live cd. I deleted the /boot folder from sda1.
The result I got is given below.
```

ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
ubuntu@ubuntu:~$
```

---

### Post by Quackers on 2011-01-21
Did you do this part first?
"From Ubuntu or a LiveCD or however else you can access your systems, you need to delete the /boot folder from sda1 (Windows).

You should be able to do this from a normally-running Ubuntu OS, or to do this from a LiveCD, mount the Windows partition, then open a file browser as root and remove the /boot folder (make sure you get the correct one, which should have a "grub" subfolder and contains the "core.img" file)."
```
sudo mount /dev/sda1 /mnt
gksu nautilus /mnt
```
"You should see /boot. That is the folder you need to remove. Once you do so the os-prober file should work as it is supposed to. "

---

### Post by telovin on 2011-01-21
Yes I did delete /boot with grub subfolder n core.img from sda1(through live cd).

---

### Post by Quackers on 2011-01-21
Well that's good then :-)
I suspect that the failed upgrade to 10.10 will have made a mess of things and that it will be necesary to re-install 10.04 (or 10.10) over the top of whatever is left of 10.04. If you use the same partitions, there shouldn't be a problem, choosing to format them again.

---

### Post by telovin on 2011-01-21
Aww. It is so disheartening to hear that I have to format the current ubuntu partition! Can't I just tweak something so that i can resume the 10.10 installation or just go back to 10.04?

---

### Post by Quackers on 2011-01-21
If the upgrade has partly run I suspect that damage has been done. I may be wrong, but if I am, I wouldn't know what to do about it :-(
There's worse news. When you had Ubuntu booting direct (no grub menu) that was what was supposed to happen at that point. 
Nevermind. If you need to get files backed up you may be able to get to them via the live cd desktop.
Windows should be ok as long as you take care not to over-write it during installation.

Aha! I see from your other thread that there is hope :-)  Good luck with that! I hope you can save it.

---

### Post by telovin on 2011-01-21
I am copying my home folder to windows desktop n let me start with the installation. :(

Thanks a lot Quackers, wilee nilee, Drs305 n everyone else who tried to help me.
God bless you all!

---

### Post by Quackers on 2011-01-21
You're welcome.
Didn't your other thread help you to save it?

---

### Post by telovin on 2011-01-21
[SIZE="3"]You Know what Quackers?I saw the other thread after posting my reply here. I tried what the other thread had suggested and it worked! It not only completed my installation to latest version but also loads a beautiful Grub with windows and Ubuntu entries! I logged on to Ubuntu and win7 without any problems! 
Thanks a lot to You n Drs305 for identifying my problem n helping me out. Deleting the /boot folder from sda1(win 7 partition) helped os-prober to recognize the win 7 entry I guess.(If I wouldn't have deleted the /boot folder from win7, i guess my os prober and grub still won't be recognizing the win7)
At last Ubuntu n Win7 Go hand in hand just like old times!
Loving this :)

Many Thanks to Quackers, drs305, wileenilee n many others who tried to help me out!
Esp. Loads of thanks to Quackers[/SIZE] :D

---

### Post by Quackers on 2011-01-21
You're very welcome :-)
Have fun!

---

