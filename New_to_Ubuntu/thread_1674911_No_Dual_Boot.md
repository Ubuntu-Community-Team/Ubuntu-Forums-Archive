---
title: "No Dual Boot"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Notac on 2011-01-24
I have installed Ubuntu 64bit Desktop alongside a current XP installation.
After installing I got the message to reboot.
After rebooting, my machine boots directly into Win XP.
I do not get the screen that asks which OS you wish to boot into.

Any help would be appreciated.
Thank you

---

### Post by Quackers on 2011-01-24
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Notac on 2011-01-24
here are the results from the instructions you gave me


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   781,417,664   781,417,602   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   246,273,771   246,273,709   7 HPFS/NTFS
/dev/sdc2         246,274,046   488,396,799   242,122,754   5 Extended
/dev/sdc5         246,274,048   478,472,191   232,198,144  83 Linux
/dev/sdc6         478,474,240   488,396,799     9,922,560  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CA44F79A44F3544                       ntfs       PS3 Transfer                  
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        44C89FA8C89F96B0                       ntfs       Win XP Pro                    
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        ddc3880e-75ec-4613-8cc0-90c5e280b6f5   ext4                                     
/dev/sdc6        d6529498-fb97-49b6-be3f-7d8048be0c4d   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdc5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set ddc3880e-75ec-4613-8cc0-90c5e280b6f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set ddc3880e-75ec-4613-8cc0-90c5e280b6f5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set ddc3880e-75ec-4613-8cc0-90c5e280b6f5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ddc3880e-75ec-4613-8cc0-90c5e280b6f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set ddc3880e-75ec-4613-8cc0-90c5e280b6f5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ddc3880e-75ec-4613-8cc0-90c5e280b6f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set ddc3880e-75ec-4613-8cc0-90c5e280b6f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set ddc3880e-75ec-4613-8cc0-90c5e280b6f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 44c89fa8c89f96b0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=ddc3880e-75ec-4613-8cc0-90c5e280b6f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=d6529498-fb97-49b6-be3f-7d8048be0c4d none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


 147.9GB: boot/grub/core.img
 128.3GB: boot/grub/grub.cfg
 127.0GB: boot/initrd.img-2.6.35-22-generic
 147.9GB: boot/vmlinuz-2.6.35-22-generic
 127.0GB: initrd.img
 147.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  00 2c 00 00 4e 42 00 00  04 00 00 00 00 00 00 00  |.,..NB..........|
00000010  12 98 91 00 db 1f 45 00  00 00 00 00 36 03 06 00  |......E.....6...|
00000020  00 00 00 00 37 03 06 00  ac 30 05 00 9b 96 02 00  |....7....0......|
00000030  a8 28 07 00 00 00 00 00  38 b1 02 00 00 00 00 00  |.(......8.......|
00000040  00 20 11 00 00 00 00 00  91 52 00 00 4f 42 00 00  |. .......R..OB..|
00000050  05 00 00 00 00 00 00 00  57 98 91 00 f4 b3 43 00  |........W.....C.|
00000060  01 00 00 00 39 03 06 00  00 00 00 00 3a 03 06 00  |....9.......:...|
00000070  b3 30 05 00 3a 84 02 00  00 00 00 00 00 00 00 00  |.0..:...........|
00000080  c6 ab 00 00 00 00 00 00  00 30 0a 00 00 00 00 00  |.........0......|
00000090  cf b3 00 00 50 42 00 00  05 00 00 00 00 00 00 00  |....PB..........|
000000a0  81 98 91 00 db 1f 45 00  00 00 00 00 3c 03 06 00  |......E.....<...|
000000b0  00 00 00 00 3d 03 06 00  b5 30 05 00 9c 96 02 00  |....=....0......|
000000c0  a9 28 07 00 00 00 00 00  72 a5 02 00 00 00 00 00  |.(......r.......|
000000d0  00 30 11 00 00 00 00 00  2f 52 00 00 51 42 00 00  |.0....../R..QB..|
000000e0  05 00 00 00 00 00 00 00  ce 98 91 00 2e f8 4b 00  |..............K.|
000000f0  00 00 00 00 3f 03 06 00  00 00 00 00 40 03 06 00  |....?.......@...|
00000100  b8 30 05 00 9d 96 02 00  af 28 07 00 00 00 00 00  |.0.......(......|
00000110  1c f6 3f 00 00 00 00 00  00 f0 7b 01 00 00 00 00  |..?.......{.....|
00000120  69 49 00 00 52 42 00 00  04 00 00 00 00 00 00 00  |iI..RB..........|
00000130  99 99 91 00 f4 b3 43 00  01 00 00 00 42 03 06 00  |......C.....B...|
00000140  00 00 00 00 43 03 06 00  d2 30 05 00 9f 96 02 00  |....C....0......|
00000150  00 00 00 00 00 00 00 00  36 6e 0c 00 00 00 00 00  |........6n......|
00000160  00 20 96 00 00 00 00 00  ae ed 00 00 53 42 00 00  |. ..........SB..|
00000170  04 00 00 00 00 00 00 00  dc 99 91 00 2e f8 4b 00  |..............K.|
00000180  00 00 00 00 45 03 06 00  00 00 00 00 46 03 06 00  |....E.......F...|
00000190  d8 30 05 00 a0 96 02 00  b3 28 07 00 00 00 00 00  |.0.......(......|
000001a0  c6 8b 43 00 00 00 00 00  00 50 a9 01 00 00 00 00  |..C......P......|
000001b0  38 82 00 00 54 42 00 00  04 00 00 00 00 00 00 fe  |8...TB..........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 d7 0d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 10  d7 0d 00 70 97 00 00 00  |...........p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I hope this makes sense to you and thank you for your help.

---

### Post by Quackers on 2011-01-24
Grub has been installed to your 400GB hard drive (sda) instead of to your 250GB hard drive (sdc).
To correct this you should install grub to sdc (assuming no drives have been disconnected since the boot script was run!).
Please boot from the Ubuntu live cd and copy/paste the following commands into the terminal, one at a time and pressing enter after each line.
```
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
```
Then reboot.
Ubuntu should then load directly (no menu). If it does, please open a terminal and run
```
sudo update-grub
```
and watch as grub.cfg is run, to confirm that the Windows loader is picked up.
If it is, reboot and try to boot Windows from your shiny new grub menu :-)

---

### Post by Notac on 2011-01-25
Thank you Quackers, that has cured by Boot issue.

I now have a slightly different issue in so much as I now get offered 4 linux options as I have run the update manager.

My boot screen now offers me a normal and recovery mode but with 2 different kernels.

Would you be able to help with this or do I need to set a new post.

Again thank you for fixing my Boot issue

---

### Post by runeh76 on 2011-01-25
Hi
Just choose the top one  :)

---

### Post by Quackers on 2011-01-25
I'm glad that fixed it :-)
Your new problem is a common matter. Every time a new kernel is installed, 2 new entries will appear in the grub menu. Some users advocate you should keep the latest 2 kernels so as to have a backup, in case of a failure to boot. 
Others advocate deleting the older kernel as soon as you confirm that the new kernels works ok. The choice is yours.
If you wish to delete kernels you can enter the kernel number in synaptic package manager's search box and remove it that way (2 entries for each kernel in synaptic).
Then run sudo update-grub in a terminal.
If you want to get rid of the recovery mode entries you can run this in a terminal
```
sudo sed s/'#GRUB_DISABLE_LINUX_RECOVERY="true"'/'GRUB_DISABLE_LINUX_RECOVERY="true"'/g -i /etc/default/grub
```
And if you want to delete the Memtest entires you can run this
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

Both the above entries come courtesy of drs305's excellent guide below
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

There is also a new GUI tool for changing grub details, see here
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Notac on 2011-01-26
Thank you Quackers for all your help.:D

Have had a quick look at the 2 links, both very informative.
I am hoping to be converted from Windows, but taking small steps 1st.

Next on my todo list are ssh, remote access from a windows box and hopefully a working installation of handbrake.

Many thanks:D

---

### Post by Quackers on 2011-01-26
You're welcome :-)
Please mark the thread as solved using the Thread Tools near the top of the page.

---

### Post by Static17 on 2012-01-16
Hello!
I have the same propblem of laptop booting in windows. I've done the steps but it seems I have some other problem. 
Please, Help!


>             Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 221967017 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   137,789,504   137,789,442   7 NTFS / exFAT / HPFS
/dev/sda2         137,789,505   963,961,379   826,171,875  83 Linux
/dev/sda3         963,962,878   976,771,071    12,808,194   5 Extended
/dev/sda5         963,962,880   976,771,071    12,808,192  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5BE44A069319B386                       ntfs       Win7
/dev/sda2        bfee268f-80ac-4fb1-ad94-57961fc7e06d   ext4       
/dev/sda5        5ee3ac1a-de25-449e-a6b8-a50fd3f8d106   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error



---

