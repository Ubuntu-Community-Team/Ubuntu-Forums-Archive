---
title: "grub rescue;USB boot can login and runs very slowly"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by pleasurefish on 2010-12-07
hi,everyone.im noob.my laptop's dualboot system are XP and ubuntu9.10.
 
on Sundy,i want to recover XP to eliminate the laptop's uncompatible problem between 
 
XP and the Audio card with Ghost.
 
After the recovery,i can login ubuntu but can't login XP,im sorry i didn't stop.i just
 
recover the C partition again using the WinPE.
 
Now i can login neither.when the grub begins,it shows"error filesystem,grub
 
rescue".and i can login the USB live CD.please help me .
 
in the grub rescue ,i use "ls" and find "/boot/grub" at (hd0,13),(hd0,10) i also find 
 
"lost+u.."and "yubuntu(that is my account)"two file in (hd0,12),(hd0,9).
 
in the live CD,i use "sudo fdisk -l" and find 
 
[COLOR=red]"/dev/sda1""/dev/sda2"..."/dev/sda60"250GB [/COLOR]and "/dev/sdb1" 8455MB.
 
i only known a little syntax of the teminal, and have a live CD(in the USB).before i put 
 
this thread,i want to access and download the bootinfoscript but the connect seems to 
 
be always reset for in the live CD(USB),[COLOR=red]i can't get info of the boot[/COLOR].if file in the 
 
laptop survive,it would be very pleasure.what should i do or 
 
any suggestion.please help me.Thanks very much.

---

### Post by oldfred on 2010-12-08
Welcome to the forums.

It would be a big help if you could get the boot info script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Do you have two installs? sda10 & sda13? Which is your primary or the one you want to boot.

You should be able to manually boot if you have a grub prompt.

Change [COLOR=Red]10[/COLOR] to 13 if that it the one you want to boot:
set prefix=(hd0,[COLOR=Red]10[/COLOR])/boot/grub
insmod (hd0,[COLOR=Red]10[/COLOR])/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,[COLOR=Red]10[/COLOR])
linux /vmlinuz root=/dev/sda[COLOR=Red]10[/COLOR] ro
initrd /initrd.img
boot

---

### Post by pleasurefish on 2010-12-08
> **oldfred said:**
> Welcome to the forums.
 
It would be a big help if you could get the boot info script.
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.
 
Do you have two installs? sda10 & sda13? Which is your primary or the one you want to boot.
 
You should be able to manually boot if you have a grub prompt.
 
Change [COLOR=red]10[/COLOR] to 13 if that it the one you want to boot:
set prefix=(hd0,[COLOR=red]10[/COLOR])/boot/grub
insmod (hd0,[COLOR=red]10[/COLOR])/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,[COLOR=red]10[/COLOR])
linux /vmlinuz root=/dev/sda[COLOR=red]10[/COLOR] ro
initrd /initrd.img
boot
 
 Thanks very much for your replying.
 
i try my best to download the bootinfoscript but the connect always seems to be reset again by again since my laptop boot from USB live CD run very slowly.
 
in laptop there are 2.6.31-14-generic and 2.6.31-22-generic. 
 
i'm noob.there nothing important in ubuntu.
 
the reason i want to boot for one from them is that i want to access the memory so that i could copy some file which stored in WinXP and format the memory thoroughly ,then install the system again.
 
i follow your instruction and i can login the ubuntu.terrific!!!
 
one moment i try to download the bootinfoscript again though the laptop still run very slowly.Thanks very much.

---

### Post by pleasurefish on 2010-12-08
oh,the bash spends so much time,about one hour.
 
though i login the laptop,it response to my operation very slowly.
 
is it unusual?
 
should i stop?
 
thank you very much. :-)

---

### Post by oldfred on 2010-12-08
The boot script only takes a minute or two depending on your system. It should not be that slow. Do you have some hard drive or other system issues?

Even the USB boot will be slower than the Hard Disk install, but should run relatively quickly once an app is loaded. Only writes to a flash drive are slow especially if you have USB1.1 not USB2.

---

### Post by pleasurefish on 2010-12-09
sorry,there are bad things one by one,the network was unstable,so late to post a thread.
 
i also have windows_xp_professional_with_service_pack_3.just download from the ftp.
before i manually boot into the system,there is no error for ubuntu9.10.
 
USB memory is USB 2.0,8GB.i think the USB matters nothing.maybe my partition have destroyed for in terminal the result of "sudo fdisk -l" returns [COLOR=red]/dev/sda1,/dev/sda2,/dev/sda3...until /dev/sda60[/COLOR]and i only have 250GB
 
also in Disk Utility i've seen [COLOR=red]/dev/sda188[/COLOR].oh my god.
 
thanks for your help.
 
when i login,first it show a character interface (like the cmd prompt),and i input accout and password.it entered.
then it show GNOME,it also allow me to input the password.finally it slowly get into the system.
 
the first account is yubuntu. and in GNOME the account is yUbuntu.maybe it is helpful to the question.
 
thank you very much. :-)
 
i tried to recover the grub with rescatux_cdrom_usb_hybrid_i386_486-amd64_2010_12_06,and it login.but the laptop also run very slowly,then i power off the laptop.
 
 
and type"df -h"and it return :
```
filesystem size Used Mounted on
/dev/sda13 15G 3.4G /
udev 1005M 1.3M /dev
none 1005M 408k /dev/shm
none 1005M 72k /var/run
none 1005M 0 /var/ lock
none 1005M 0 /lib/init/rw
/dev/sda222 31G 457M /home

```

---

### Post by oldfred on 2010-12-09
How do you have so many partitions?
/dev/sda[COLOR=Red]222 [/COLOR]                 31G       457M      /home

That may explain why script is so slow as it has to process every partition.

run this, but if it is as long as you say be sure to post in code tags (the # in edit menu above as you post). Either click on # and paste between the code code tags or highlight and then click on # and it will auto add tags at start & end of highlighted script.
```

sudo fdisk -lu
```

---

### Post by pleasurefish on 2010-12-09
> **oldfred said:**
> How do you have so many partitions?
/dev/sda[COLOR=red]222 [/COLOR]31G 457M /home
 
That may explain why script is so slow as it has to process every partition.
 
run this, but if it is as long as you say be sure to post in code tags (the # in edit menu above as you post). Either click on # and paste between the code code tags or highlight and then click on # and it will auto add tags at start & end of highlighted script.
```

sudo fdisk -lu
```
 
there're many partition,maybe 255,surprisingly.
 
after type "sudo fdisk -lu",it returns
```

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x624aa2e0
Device Boot Start End Blocks Id System
/dev/sda1 * 63 51424064 25712001 c W95 FAT32 (LBA)
/dev/sda2 51424065 488392064 218484000 f W95 Ext'd (LBA)
/dev/sda5 51424128 212041934 80308903+ 7 HPFS/NTFS
/dev/sda6 212041998 274358069 31158036 7 HPFS/NTFS
/dev/sda7 372659868 402653159 14996646 83 Linux
/dev/sda8 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda9 308351673 424083869 57866098+ b W95 FAT32
/dev/sda10 274358133 304351424 14996646 83 Linux
/dev/sda11 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda12 308351673 424083869 57866098+ b W95 FAT32
/dev/sda13 274358133 304351424 14996646 83 Linux
/dev/sda14 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda15 308351673 424083869 57866098+ b W95 FAT32
/dev/sda16 274358133 304351424 14996646 83 Linux
/dev/sda17 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda18 308351673 424083869 57866098+ b W95 FAT32
/dev/sda19 274358133 304351424 14996646 83 Linux
/dev/sda20 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda21 308351673 424083869 57866098+ b W95 FAT32
/dev/sda22 274358133 304351424 14996646 83 Linux
/dev/sda23 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda24 308351673 424083869 57866098+ b W95 FAT32
/dev/sda25 274358133 304351424 14996646 83 Linux
/dev/sda26 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda27 308351673 424083869 57866098+ b W95 FAT32
/dev/sda28 274358133 304351424 14996646 83 Linux
/dev/sda29 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda30 308351673 424083869 57866098+ b W95 FAT32
/dev/sda31 274358133 304351424 14996646 83 Linux
/dev/sda32 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda33 308351673 424083869 57866098+ b W95 FAT32
/dev/sda34 274358133 304351424 14996646 83 Linux
/dev/sda35 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda36 308351673 424083869 57866098+ b W95 FAT32
/dev/sda37 274358133 304351424 14996646 83 Linux
/dev/sda38 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda39 308351673 424083869 57866098+ b W95 FAT32
/dev/sda40 274358133 304351424 14996646 83 Linux
/dev/sda41 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda42 308351673 424083869 57866098+ b W95 FAT32
/dev/sda43 274358133 304351424 14996646 83 Linux
/dev/sda44 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda45 308351673 424083869 57866098+ b W95 FAT32
/dev/sda46 274358133 304351424 14996646 83 Linux
/dev/sda47 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda48 308351673 424083869 57866098+ b W95 FAT32
/dev/sda49 274358133 304351424 14996646 83 Linux
/dev/sda50 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda51 308351673 424083869 57866098+ b W95 FAT32
/dev/sda52 274358133 304351424 14996646 83 Linux
/dev/sda53 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda54 308351673 424083869 57866098+ b W95 FAT32
/dev/sda55 274358133 304351424 14996646 83 Linux
/dev/sda56 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda57 308351673 424083869 57866098+ b W95 FAT32
/dev/sda58 274358133 304351424 14996646 83 Linux
/dev/sda59 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda60 308351673 424083869 57866098+ b W95 FAT32
Partition table entries are not in disk order
 

```
 
thanks a lot. :-)

---

### Post by oldfred on 2010-12-09
Warning: omitting partitions after #60.

It did not even give us the entire list. Some have been asking how many partitions they can have and we say 16 or maybe more. Now we can say a lot more.

How did you get to this point. Have you reinstalled Linux a bunch of times, or are you testing every version of linux? It also looks like the partition table has major errors as the numbers of start & end repeat.
These start & ends repeat every three partitions.
/dev/sda8 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda9 308351673 424083869 57866098+ b W95 FAT32
/dev/sda10 274358133 304351424 14996646 83 Linux

The partition entries for logical partitions are a linked list and it looks like you have a bad link.

I think it is time to think about starting over. Testdisk can often repair partition entries so if you want to try that you can.

Another thing to try:
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by pleasurefish on 2010-12-10
> **oldfred said:**
> Warning: omitting partitions after #60.
 
It did not even give us the entire list. Some have been asking how many partitions they can have and we say 16 or maybe more. Now we can say a lot more.
 
How did you get to this point. Have you reinstalled Linux a bunch of times, or are you testing every version of linux? It also looks like the partition table has major errors as the numbers of start & end repeat.
These start & ends repeat every three partitions.
/dev/sda8 304351488 308351609 2000061 82 Linux swap / Solaris
/dev/sda9 308351673 424083869 57866098+ b W95 FAT32
/dev/sda10 274358133 304351424 14996646 83 Linux
 
The partition entries for logical partitions are a linked list and it looks like you have a bad link.
 
I think it is time to think about starting over. Testdisk can often repair partition entries so if you want to try that you can.
 
Another thing to try:
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
 
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
 
i only update ubuntu9.10 from 2.6.31-14-generic to 2.6.31-22-generic.no more version.
 
many thanks,i'll have a try.:-)

---

### Post by pleasurefish on 2010-12-10
after i installed testdisk and repair the /dev/sda,the laptop work very quickly after i manually boot into the ubuntu9.10,smile.but if i booted into the system manually,it seems very troublesome.so oldfred,i need your help.RESULT.txt is followed. thank you.
```

                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
sda1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sda6: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
sda7: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda8: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda9: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   
sda10: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x624aa2e0
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    51,424,064    51,424,002   c W95 FAT32 (LBA)
/dev/sda2          51,424,065   488,392,064   436,968,000   f W95 Ext d (LBA)
/dev/sda5          51,424,128   212,041,934   160,617,807   7 HPFS/NTFS
/dev/sda6         212,041,998   274,358,069    62,316,072   7 HPFS/NTFS
/dev/sda7         274,358,133   304,351,424    29,993,292  83 Linux
/dev/sda8         304,351,488   308,351,609     4,000,122  82 Linux swap / Solaris
/dev/sda9         308,351,673   372,659,804    64,308,132  83 Linux
/dev/sda10        372,659,868   488,392,064   115,732,197   c W95 FAT32 (LBA)

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda10       046D-B7C4                              vfat       BACKUP                        
/dev/sda1        8886-CCB9                              vfat                                     
/dev/sda5        2A88274388270D3F                       ntfs       SOFTWARE                      
/dev/sda6        323C95593C951945                       ntfs       MEDIA                         
/dev/sda7        f306bef1-932e-4a87-89bb-96cd3f5fb5cf   ext4                                     
/dev/sda8        1a460ac1-52d7-4317-9973-48651478c162   swap                                     
/dev/sda9        9c7fe485-8922-453b-9ea0-6fdbe0673bbe   ext4                                     
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /DETECTHAL
=========================== sda7/boot/grub/grub.cfg: ===========================
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
search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd0,8)
 search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro   quiet splash
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd0,8)
 search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro single 
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd0,8)
 search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd0,8)
 search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
 insmod ntfs
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set d83c880a3c87e1bc
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda7/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=9c7fe485-8922-453b-9ea0-6fdbe0673bbe /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=1a460ac1-52d7-4317-9973-48651478c162 none            swap    sw              0       0
=================== sda7: Location of files loaded by Grub: ===================

 140.9GB: boot/grub/core.img
 143.0GB: boot/grub/grub.cfg
 142.4GB: boot/initrd.img-2.6.31-14-generic
 144.8GB: boot/initrd.img-2.6.31-22-generic
 142.5GB: boot/vmlinuz-2.6.31-14-generic
 144.5GB: boot/vmlinuz-2.6.31-22-generic
 144.8GB: initrd.img
 142.4GB: initrd.img.old
 144.5GB: vmlinuz
 142.5GB: vmlinuz.old

```

---

### Post by pleasurefish on 2010-12-10
and then i run with the instructions followed:
```
sudo grub-install /dev/sda
sudo update-grub

```
 
the XP system could login .
the setup havenot finished.
 
Thanks a lot . oldfred.

---

### Post by oldfred on 2010-12-10
Not sure I totally understand. Did the reinstall of grub to the MBR fix your issues. The results.txt showed it was booting from sda8 but your install is in sda7. Perhaps you deleted a partition? The reinstall of grub that you then posted should have fixed that.

Partition table looks a whole lot better.:) Glad testdisk was able to fix it.

---

### Post by pleasurefish on 2010-12-13
i hurried to recover my lost data,and make no eye on this thread,sorry to response to your post so late,oldfred.it seems as that you had infered.the RESULTS.txt followed below.oh,i never del a partition,but i may del a partition in nonsense state.hope this helps you.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0b1ebb0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,424,064    51,424,002   c W95 FAT32 (LBA)
/dev/sda2          51,424,065   488,392,064   436,968,000   f W95 Ext d (LBA)
/dev/sda5          51,424,128   212,041,934   160,617,807   7 HPFS/NTFS
/dev/sda6         212,041,998   274,358,069    62,316,072   7 HPFS/NTFS
/dev/sda7         274,358,133   304,351,424    29,993,292  83 Linux
/dev/sda8         304,351,488   308,351,609     4,000,122  82 Linux swap / Solaris
/dev/sda9         308,351,673   372,659,804    64,308,132  83 Linux
/dev/sda10        372,659,868   488,392,064   115,732,197   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       046D-B7C4                              vfat       BACKUP                        
/dev/sda1        8886-CCB9                              vfat                                     
/dev/sda5        2A88274388270D3F                       ntfs       SOFTWARE                      
/dev/sda6        323C95593C951945                       ntfs       MEDIA                         
/dev/sda7        f306bef1-932e-4a87-89bb-96cd3f5fb5cf   ext4                                     
/dev/sda8        1a460ac1-52d7-4317-9973-48651478c162   swap                                     
/dev/sda9        9c7fe485-8922-453b-9ea0-6fdbe0673bbe   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set f306bef1-932e-4a87-89bb-96cd3f5fb5cf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8886-ccb9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=f306bef1-932e-4a87-89bb-96cd3f5fb5cf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=9c7fe485-8922-453b-9ea0-6fdbe0673bbe /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=1a460ac1-52d7-4317-9973-48651478c162 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 140.7GB: boot/grub/core.img
 143.0GB: boot/grub/grub.cfg
 142.4GB: boot/initrd.img-2.6.31-14-generic
 144.8GB: boot/initrd.img-2.6.31-22-generic
 142.5GB: boot/vmlinuz-2.6.31-14-generic
 144.5GB: boot/vmlinuz-2.6.31-22-generic
 144.8GB: initrd.img
 142.4GB: initrd.img.old
 144.5GB: vmlinuz
 142.5GB: vmlinuz.old
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo1/sda10: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```
thank you for your selfless help.

---

### Post by oldfred on 2010-12-13
Boot script looks normal to me. I can see you moved a partition around but the UUIDs seem to match fstab.

Does it boot ok now?

I do not recommend FAT for partitions anymore. NTFS is better for windows & shared partitions with windows. FAT has a limit of 4GB for files and does not have a journal.
Only if you have a xbox or need to format a small memory card for compatiblity with a camera or other device should you use FAT32.

---

### Post by pleasurefish on 2010-12-14
Yes,it can boot ok now.
 
although the Audio card problem still exists.
 
the partition was ntfs,i think the WinPE(a recovery tool,we can install winXP in it)may format the C partition with the fat32 format.i would change the format some days later.  :-)

---

### Post by oldfred on 2010-12-14
Glad you are working.

I do not know about audio issues. 

My audio works under Ubuntu and under windows every time I installed an updated driver it would stop working. I found I had to unplug everything & plug it back in and the windows driver sensed it and worked. But not if already plugged in. The Linux driver just works. Some older versions of Ubuntu had the audio turned off (mute) or turned down and just setting volume up worked.

---

