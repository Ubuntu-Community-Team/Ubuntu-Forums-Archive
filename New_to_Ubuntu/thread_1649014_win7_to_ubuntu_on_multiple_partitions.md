---
title: "win7 to ubuntu on multiple partitions"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Mystake on 2010-12-19
having had enough of win7, I've began the process of changing over to Linux.

I have a specific 130gb partition that I wanted to use. I've skipped on using a swap partition as I have 4gb of ram, I'll upgrade more as time needs it (hence using 64bit).

I actually have been thinking of restarting over and simply using a 15gb partition for Linux and then the remaining 115gb as the /home directory. I've read something along the lines that it's basically identical to installing windows on a separate partition, if windows corrupts the files are still separate and safe.

Here's the settings vis-a-vis hd's;
130gb partition for Linux
120gb remaining of that hard drive with my windows 7 installation and all associated files (i don't want to touch this drive, at all)
a 500gb drive
a 750gb drive

My windows 7 is, for the most part, history at this point. Everything is still there but Grub's taken over and only has Linux as an option to boot into. I don't mind this, I don't want to re-use Win7.

Here's the issue, if I try to boot into the Live CD I get a straight green screen, nothing more.

if I try to boot into Linux using Grub, the system sits with the cursor flashing on a black screen.

from what I can gather, it seems the mapping is all off for the hd's. 

I used the option of installing Grub to the same drive that Linux was being installed to.

In grub, it tries to load hd(0), at least thats what I think it's doing.
In supergrubdisk, the partition I'm after is hd(1). The 2nd 120gb partition though is (1,4) (wouldn't it be 1,1?)

And that's all I know. I know not of where to go from here. 

if anyone is willing to do this with me over MSN, that'd be great.
user name @ gmail.com is where I'm at. Elsewise, I'm very new to Linux... I really don't know anything about it and have tons and tons to learn.

Thank you

---

### Post by PhantmKllr on 2010-12-19
Is your BIOS set to boot from a live CD? If so, then maybe your live CD is bad. You should then download a new one from the Ubuntu website (never from anywhere else, you may end up with a dud).

---

### Post by Mystake on 2010-12-19
afaik the Live CD is perfectly fine.

Would it have to do with having an Nvidia graphics card?

And what do you mean set to boot from a live cd? Don't you mean from a CD-Rom? Yes, it is set that way.

The problem isn't getting into the CD, its if I want to boot Linux from the CD, I then get the green screen.

Instead, I go through the menus of installing Linux. That all goes well, it's when I then try to boot into Linux, off my hard drive that I'm getting the problem that I mention all the hd(0) stuff at. This is specifically what I'm looking to solve (though I'm curious about the liveCD too)

---

### Post by oldfred on 2010-12-19
Often related to video issues.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

If you have boot issues that are not the video issue.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by PhantmKllr on 2010-12-19
If you're having an issue booting Linux from the CD, then it's probably bad. You shouldn't have any issues booting from a CD...

---

### Post by candtalan on 2010-12-19
Booting from an Ubuntu (or any other ) live CD should simply work. It uses the CD drive, and it uses the RAM, and not much else. If it does not boot fully then the CD burn is suspect. Such images are required to be more perfect that normal burns. The md5 from a trusted origin should be used to check the download image and also the burned CD. When booting in the target drive, the boot option 'check CD for errors' will verify that the target drive is reading the CD correctly. 

If you cannot get that far with a known good CD and a known good CD target drive, then video compatibilityy issues are the next possibility.

---

### Post by Mystake on 2010-12-19
> **candtalan said:**
> Booting from an Ubuntu (or any other ) live CD should simply work. It uses the CD drive, and it uses the RAM, and not much else. If it does not boot fully then the CD burn is suspect. Such images are required to be more perfect that normal burns. The md5 from a trusted origin should be used to check the download image and also the burned CD. When booting in the target drive, the boot option 'check CD for errors' will verify that the target drive is reading the CD correctly. 

If you cannot get that far with a known good CD and a known good CD target drive, then video compatibilityy issues are the next possibility.

I don't know anything about md5.

Also I deal with a slight motherboard issue, usb keyboard doesn't usually turn on until an OS has loaded. Once that happens, hitting the reset button on the case will keep the usb ports on, if I go Reboot or shut it all down, no more usb.

It's strange, I don't know why it works like that. I haven't figured out what it is I've been doing that has gotten it to work without going into an OS but it involves hitting the reset button a lot and changing usb ports frequently.

Aaaaaanyway,

I did have to install Linux using nomodeset, so possibly that's why the LiveCD won't work (video compatibility issues?)

But back to the actual installation itself,
I re did it all over, did a swap partition, a / partition and a /home partition. Linux installed to /, Grub was set to install to the harddrive itself and not any specific partition.

No Linux. Just that blinking cursor, so I can't even get to a green screen if I tried.

---

### Post by oldfred on 2010-12-19
If you had to use nomodeset to boot CD, then you will have to use it on your first boot. See my previous post.

---

### Post by Mystake on 2010-12-19
> **oldfred said:**
> If you had to use nomodeset to boot CD, then you will have to use it on your first boot. See my previous post.

haha and see mine just above your more recent one.

I've got more than one issue...

---

### Post by oldfred on 2010-12-19
If this is the only system or if it has not found your windows so it thinks it is the only system, you do not get a grub menu and just start booting. To get menu, you have to hold shift key from BIOS to menu. Then you can add the nomodeset by editing the grub menu.

If you are having USB keyboard and mouse issues that is most often a BIOS setting. Windows and Ubuntu used to ignore BIOS and just work. It seems grub actually looks at BIOS and says you do not have USB mouse enabled, do not even try to use it.

---

### Post by Mystake on 2010-12-19
> **oldfred said:**
> If this is the only system or if it has not found your windows so it thinks it is the only system, you do not get a grub menu and just start booting. To get menu, you have to hold shift key from BIOS to menu. Then you can add the nomodeset by editing the grub menu.

If you are having USB keyboard and mouse issues that is most often a BIOS setting. Windows and Ubuntu used to ignore BIOS and just work. It seems grub actually looks at BIOS and says you do not have USB mouse enabled, do not even try to use it.



I simply took my computer apart for a short little minute here and pulled the cmos battery. Keyboard worked on turn on, so that's good.

When I installed Linux I told it to be the only OS on my computer. Yes, Windows 7 IS there but Grub doesn't show it as an option. SuperGrubDisk recognizes it though on hd(0,5). Linux is shown as being on hd(0,0)

---

### Post by oldfred on 2010-12-19
If your windows is in a logical partition it is not bootable. Only from a primary partition windows can you boot a windows in a logical partition. Did you  have another install of windows in the primary partition?

Windows also has moved all the boot files from the windows install in the logical partition to the install in the primary partition. If you delete the install in the primary partition, you also delete the boot files. If the second install of windows is in a primary partitition, then it would be repairable, not not in a logical. Windows will not let you fix XP either but some here have work arounds to get xP to boot in a logical partition.

---

### Post by Mystake on 2010-12-19
I don't want windows, I just want Linux. I don't care that I've killed off my windows installations. 


My computer was XP, before I created a partition and dual booted to 7. Somewhere, 7 corrupted XP.

The XP Partition was formatted and is now being used to host Linux. 7 is HISTORY. All I care about that partition are the files on it. I don't want Windows anymore.

However, this is a HEAD ACHE to install. I miss Windows where you can literally pop in a CD, install onto whatever partition you want and be DONE.


tinkered around with SuperGrubDisk, Grub no longer shows itself... yay... and basically every and any option in it ends with an error. I'm assuming Grub never fully installed properly.

---

### Post by oldfred on 2010-12-19
If it is a grub boot related issue this will usually tell us. But the video issue is after grub has booted.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Mystake on 2010-12-19
I can't get into Linux, how do I run that script?



...edit nvm this, got into the liveCD...

---

### Post by Mystake on 2010-12-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    39,440,383    39,438,336  83 Linux
/dev/sda3          39,442,430   488,392,064   448,949,635   f W95 Ext d (LBA)
/dev/sda5         283,578,431   488,392,064   204,813,634   7 HPFS/NTFS
/dev/sda6          49,205,248   283,578,367   234,373,120  83 Linux
/dev/sda7          39,442,432    49,203,199     9,760,768  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,145,135 1,465,145,073   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        fa7d658c-bfea-4b88-aace-63cada5be054   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        E09CA7609CA72FC8                       ntfs       Windows 7                     
/dev/sda6        3329bc37-2c7f-486e-96db-f3c8d80dbf2e   ext4                                     
/dev/sda7        43e54fb7-ddd5-4d54-a108-cc5b676dec98   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CA427D7B427D6CD7                       ntfs       HD VOLUME                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6CF6DE72F6DE3C50                       ntfs       Media Drive                   
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fa7d658c-bfea-4b88-aace-63cada5be054
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fa7d658c-bfea-4b88-aace-63cada5be054
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa7d658c-bfea-4b88-aace-63cada5be054
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fa7d658c-bfea-4b88-aace-63cada5be054 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa7d658c-bfea-4b88-aace-63cada5be054
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fa7d658c-bfea-4b88-aace-63cada5be054 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa7d658c-bfea-4b88-aace-63cada5be054
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa7d658c-bfea-4b88-aace-63cada5be054
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fa7d658c-bfea-4b88-aace-63cada5be054 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=3329bc37-2c7f-486e-96db-f3c8d80dbf2e /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=43e54fb7-ddd5-4d54-a108-cc5b676dec98 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.6GB: boot/grub/core.img
  15.4GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
   6.6GB: boot/vmlinuz-2.6.35-22-generic
   1.0GB: initrd.img
   6.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  5e f8 ca a3 ec f6 73 e8  78 f9 7c 1e 5c fb 70 92  |^.....s.x.|.\.p.|
00000010  55 dc 79 30 b2 65 46 9f  d0 e0 68 e8 f1 f8 67 73  |U.y0.eF...h...gs|
00000020  99 99 c0 e7 f4 b4 77 72  77 64 a8 1c 01 1b e1 64  |......wrwd.....d|
00000030  ee 76 1f 4c a7 23 a5 40  97 63 cc c1 7f ae 2d 9c  |.v.L.#.@.c....-.|
00000040  a9 59 1e 2e db 90 6c af  5d 5b 12 cd f8 c4 3f 92  |.Y....l.][....?.|
00000050  17 ff 7d 22 43 e1 57 b6  19 91 4b bc 3f f7 f5 24  |..}"C.W...K.?..$|
00000060  34 76 b9 a5 d3 46 82 2b  60 5b 55 ac 2e 2d 7c 59  |4v...F.+`[U..-|Y|
00000070  fc bc c9 f9 85 77 8e 58  bf bf 87 76 6f 31 70 f8  |.....w.X...vo1p.|
00000080  19 9e ae 65 03 48 d9 d9  e9 11 24 4d 2e 36 06 67  |...e.H....$M.6.g|
00000090  07 43 47 9b a3 bc d0 cf  d1 e5 74 b9 79 f4 39 fc  |.CG.......t.y.9.|
000000a0  fb 46 a7 16 d2 43 7d ab  bd a4 8c 79 4f e3 38 d8  |.F...C}....yO.8.|
000000b0  ee 3a 7b 1d 8b ab d6 d6  cd f0 ef 6e 2e 26 51 95  |.:{........n.&Q.|
000000c0  c5 10 c9 21 ac 28 5b fb  eb ce ff c0 c9 bc 28 52  |...!.([.......(R|
000000d0  de 92 ed df 1f fd bd 22  80 8e ca 75 8b 01 f9 54  |......."...u...T|
000000e0  8a 14 24 40 b5 43 0b 7a  2e 99 97 3a 40 7b ac 43  |..$@.C.z...:@{.C|
000000f0  d6 f3 2d 35 f8 78 19 7b  ae 67 0f 79 b6 ec 1b 25  |..-5.x.{.g.y...%|
00000100  b6 b1 64 cd 8f 77 1b 2e  85 0c df 2b cb e3 7a bc  |..d..w.....+..z.|
00000110  fe 76 87 2c cf 3f 5f ed  de 28 20 e5 b1 fb f8 3e  |.v.,.?_..( ....>|
00000120  6c 1f c1 e0 ed 21 15 89  79 ea fb 1e 47 91 8c 68  |l....!..y...G..h|
00000130  9c 89 81 9f eb dd c6 87  8b bc de 4f ce f2 b9 bc  |...........O....|
00000140  4c 9e 7f 37 d2 fc de 97  a9 d1 e4 ee f2 a6 60 ed  |L..7..........`.|
00000150  3c 3f cd fa 78 85 01 d3  01 0f 62 93 57 8c 90 1b  |<?..x.....b.W...|
00000160  c7 34 30 15 5f 8f e3 f3  3a 61 a9 76 91 a3 79 9e  |.40._...:a.v..y.|
00000170  9e 5e cf c4 fc 3d 1f 77  d5 f6 fd 7f 6f d1 f1 0d  |.^...=.w....o...|
00000180  27 91 87 e5 68 e8 f1 4e  c7 8b d7 7a 1f 9f df f6  |'...h..N...z....|
00000190  bd bd 2b de f5 ff 5f c3  fb 7a 4a d6 da 49 2a fb  |..+..._..zJ..I*.|
000001a0  61 1b eb c1 d9 3e 82 07  c2 f3 75 f7 be f7 47 7b  |a....>....u...G{|
000001b0  8d c0 e2 e1 ef 39 77 34  33 b3 b7 9a 3a 1a 00 ef  |.....9w43...:...|
000001c0  fc ff 07 fe ff ff 41 38  8d 0e 42 35 35 0c 00 fe  |......A8..B55...|
000001d0  ff ff 05 fe ff ff 02 f0  94 00 00 48 f8 0d 00 00  |...........H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-12-19
You need to reinstall grub2 to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Mystake on 2010-12-20
Keeping in mind that I'm for the most part computer literate,

I'm not clear on the links posted, about mounting /media/sda5 (using the examples as an example). 
don't I want grub to be installed straight to the drive and not a partition?

---

### Post by oldfred on 2010-12-20
The short (as opposed to full chroot) method of reinstall of grub2, just requires you to tell it where the rest of the grub files are and then install the boot loader to the MBR of the drive.

Since your install is in sda1.
```
sudo mount /dev/sda1 /mnt
```Now grub2 knows where the grub.cfg and other grub files are.
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note that you install to sda (the drive) not sda1 or any other partition.

---

### Post by Mystake on 2010-12-29
Hey,

just checking back in. Holidays are over and I am back home. I will get to this now :)

---

### Post by Mystake on 2010-12-29
black screen with flashing cursor when trying to go into Linux. have put in nomodeset.

should I try to install from within the LiveCD?

i followed your instructions and the install went without a hitch?

---

### Post by Mystake on 2011-01-12
bump

---

### Post by Mystake on 2011-01-20
bump :\

---

### Post by Mystake on 2011-01-27
bump...

---

### Post by oldfred on 2011-01-30
What is the issue? Flashing cursor in the upper left corner is normal if it is only for a minute. Some have other issues and have to wait a long time. Try replacing quiet splash with nomodeset and you will see each line processed as it boots.

---

### Post by Mystake on 2011-01-31
hello, I was using nomodeset already and the flashing cursor stayed.

it never loaded into Linux.

---

### Post by oldfred on 2011-01-31
Did you replace quiet spash so you can see where it stops? Have you tried the recovery mode?

---

### Post by Mystake on 2011-02-10
hello,

when I go with nomodeset and quiet splash removed, it goes straight to the flashing cursor. nothing else shows.

recovery mode does the same.

---

### Post by oldfred on 2011-02-10
If you get the grub menu, it says that is loading just fine. But if you have correctly edited out quiet splash, & then control x, then you should see many lines of the boot process, not a flashing cursor.

---

### Post by Mystake on 2011-02-12
Then I don't know whats wrong?

If I could, I would take a video of it but I don't own a camera.

But, ctrl+x after editing out quiet splash and typing in nomodeset gives me the flashing cursor and nothing more.


i can get into the live CD. funnily enough, the mouse freezes every few seconds for a short second then works again <that cycles over and over.

---

### Post by Mystake on 2011-02-21
bump

---

### Post by oldfred on 2011-02-21
Rerun boot script just to see where you are.

What are your hardware specifications. Memory, video card, cpu etc.?

---

### Post by Mystake on 2011-02-22
The desktop is one I built myself back in april 2007.

mobo; evga nvidia 680i sli
graphics card; evga nvidia 8600GTS
ram; ocz 4gb platinum
processor; intel e6300 1.87ghz
hdd; 250gb seagate, 500gb wd, i think the 750 is seagate


i'll re run bootscript in a moment;

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    39,440,383    39,438,336  83 Linux
/dev/sda3          39,442,430   488,392,064   448,949,635   f W95 Ext d (LBA)
/dev/sda5         283,578,431   488,392,064   204,813,634   7 HPFS/NTFS
/dev/sda6          49,205,248   283,578,367   234,373,120  83 Linux
/dev/sda7          39,442,432    49,203,199     9,760,768  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,145,135 1,465,145,073   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a7c62212-5fa5-4a6a-92d0-eaf377a3e64e   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        E09CA7609CA72FC8                       ntfs       Windows 7                     
/dev/sda6        676fa088-9dc4-49f0-a24f-74d599acea13   ext4                                     
/dev/sda7        43e54fb7-ddd5-4d54-a108-cc5b676dec98   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CA427D7B427D6CD7                       ntfs       HD VOLUME                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6CF6DE72F6DE3C50                       ntfs       Media Drive                   
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/HD VOLUME         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Media Drive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/676fa088-9dc4-49f0-a24f-74d599acea13 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a7c62212-5fa5-4a6a-92d0-eaf377a3e64e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a7c62212-5fa5-4a6a-92d0-eaf377a3e64e
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a7c62212-5fa5-4a6a-92d0-eaf377a3e64e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a7c62212-5fa5-4a6a-92d0-eaf377a3e64e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a7c62212-5fa5-4a6a-92d0-eaf377a3e64e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a7c62212-5fa5-4a6a-92d0-eaf377a3e64e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a7c62212-5fa5-4a6a-92d0-eaf377a3e64e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a7c62212-5fa5-4a6a-92d0-eaf377a3e64e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a7c62212-5fa5-4a6a-92d0-eaf377a3e64e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=676fa088-9dc4-49f0-a24f-74d599acea13 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=43e54fb7-ddd5-4d54-a108-cc5b676dec98 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  11.0GB: boot/grub/core.img
   2.2GB: boot/grub/grub.cfg
  18.0GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
  18.0GB: initrd.img
    .3GB: vmlinuz

=================== sda6: Location of files loaded by Grub: ===================


  31.7GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  5e f8 ca a3 ec f6 73 e8  78 f9 7c 1e 5c fb 70 92  |^.....s.x.|.\.p.|
00000010  55 dc 79 30 b2 65 46 9f  d0 e0 68 e8 f1 f8 67 73  |U.y0.eF...h...gs|
00000020  99 99 c0 e7 f4 b4 77 72  77 64 a8 1c 01 1b e1 64  |......wrwd.....d|
00000030  ee 76 1f 4c a7 23 a5 40  97 63 cc c1 7f ae 2d 9c  |.v.L.#.@.c....-.|
00000040  a9 59 1e 2e db 90 6c af  5d 5b 12 cd f8 c4 3f 92  |.Y....l.][....?.|
00000050  17 ff 7d 22 43 e1 57 b6  19 91 4b bc 3f f7 f5 24  |..}"C.W...K.?..$|
00000060  34 76 b9 a5 d3 46 82 2b  60 5b 55 ac 2e 2d 7c 59  |4v...F.+`[U..-|Y|
00000070  fc bc c9 f9 85 77 8e 58  bf bf 87 76 6f 31 70 f8  |.....w.X...vo1p.|
00000080  19 9e ae 65 03 48 d9 d9  e9 11 24 4d 2e 36 06 67  |...e.H....$M.6.g|
00000090  07 43 47 9b a3 bc d0 cf  d1 e5 74 b9 79 f4 39 fc  |.CG.......t.y.9.|
000000a0  fb 46 a7 16 d2 43 7d ab  bd a4 8c 79 4f e3 38 d8  |.F...C}....yO.8.|
000000b0  ee 3a 7b 1d 8b ab d6 d6  cd f0 ef 6e 2e 26 51 95  |.:{........n.&Q.|
000000c0  c5 10 c9 21 ac 28 5b fb  eb ce ff c0 c9 bc 28 52  |...!.([.......(R|
000000d0  de 92 ed df 1f fd bd 22  80 8e ca 75 8b 01 f9 54  |......."...u...T|
000000e0  8a 14 24 40 b5 43 0b 7a  2e 99 97 3a 40 7b ac 43  |..$@.C.z...:@{.C|
000000f0  d6 f3 2d 35 f8 78 19 7b  ae 67 0f 79 b6 ec 1b 25  |..-5.x.{.g.y...%|
00000100  b6 b1 64 cd 8f 77 1b 2e  85 0c df 2b cb e3 7a bc  |..d..w.....+..z.|
00000110  fe 76 87 2c cf 3f 5f ed  de 28 20 e5 b1 fb f8 3e  |.v.,.?_..( ....>|
00000120  6c 1f c1 e0 ed 21 15 89  79 ea fb 1e 47 91 8c 68  |l....!..y...G..h|
00000130  9c 89 81 9f eb dd c6 87  8b bc de 4f ce f2 b9 bc  |...........O....|
00000140  4c 9e 7f 37 d2 fc de 97  a9 d1 e4 ee f2 a6 60 ed  |L..7..........`.|
00000150  3c 3f cd fa 78 85 01 d3  01 0f 62 93 57 8c 90 1b  |<?..x.....b.W...|
00000160  c7 34 30 15 5f 8f e3 f3  3a 61 a9 76 91 a3 79 9e  |.40._...:a.v..y.|
00000170  9e 5e cf c4 fc 3d 1f 77  d5 f6 fd 7f 6f d1 f1 0d  |.^...=.w....o...|
00000180  27 91 87 e5 68 e8 f1 4e  c7 8b d7 7a 1f 9f df f6  |'...h..N...z....|
00000190  bd bd 2b de f5 ff 5f c3  fb 7a 4a d6 da 49 2a fb  |..+..._..zJ..I*.|
000001a0  61 1b eb c1 d9 3e 82 07  c2 f3 75 f7 be f7 47 7b  |a....>....u...G{|
000001b0  8d c0 e2 e1 ef 39 77 34  33 b3 b7 9a 3a 1a 00 ef  |.....9w43...:...|
000001c0  fc ff 07 fe ff ff 41 38  8d 0e 42 35 35 0c 00 fe  |......A8..B55...|
000001d0  ff ff 05 fe ff ff 02 f0  94 00 00 48 f8 0d 00 00  |...........H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2011-02-22
Bootscript looks normal. I would bet there are some special settings required with that motherboard.
One other user gave up with the nvida 680i.
[http://ubuntuforums.org/showthread.php?p=10479016](http://ubuntuforums.org/showthread.php?p=10479016)

this user has it booting:
[http://ubuntuforums.org/showthread.php?t=1428932](http://ubuntuforums.org/showthread.php?t=1428932)

Some info on special settings:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Mystake on 2011-02-22
Um, where do you recommend I go from here?

as said, I can get into the LiveCD just fine now that I use nomodeset, just can't get into the actual installation of it.

I don't know what to do next? I've tried acpi=off and nomodeset=0 but still no luck.

---

### Post by oldfred on 2011-02-23
I am about out of ideas.

You can try the alternate installer. It is more the old style DOS based, and not a liveCD. It installs different drivers since it is more for servers & others with RAID or special issues. It may work for you.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Mystake on 2011-02-23
Hmmm. I'm not completely done with this yet... I don't understand why it works from the LiveCD but not from the installation of Linux itself.


I'll keep searching but I guess for now I'm going back to windows

---

### Post by Mystake on 2011-02-23
On that note,

Thank you very much for your time. If at some point you come across some information that may be of value to me, please pass it on :)


Thanks again for your time, it was much appreciated.

---

### Post by oldfred on 2011-02-23
At the grub menu have you tried the recovery mode, but also add a nomodeset?

---

### Post by Mystake on 2011-02-25
Recovery mode does the same.


I turned on my TV today (I've left my desktop running in the background for a while) and came across the PXE-EC8 and PXE-M0F errors.


No clue how it got there. None at all, lol. but just mentioning it anyway. As far as I know myself, I would've left the blinking cursor on without bothering to turn the computer off.

Yaaaaay! Lol
Just throwing those out there in case they ring any sort of bell.

edit: did some quick googling and I have no clue how that happened. None whatsoever. Can't reproduce it. Nothing out of the ordinary in the bios so... yeah, no hints to what caused that. Again, maybe it'll mean something to you?

---

### Post by oldfred on 2011-02-26
Is BIOS showing hard drives?

As near as I can tell that is the network boot and an error that it cannot boot from the network. Usually network boot is last on the list, so your system did not find a CD, USB, or hard drive. Or did boot order get changed in BIOS?

---

### Post by Mystake on 2011-02-26
Thats why I got confused, same conclusion I came to. 

BIOS is unchanged. Boot order is CDROM, HDD, Removable then Network. For the harddrive order its the 250, the 750 then the 500. 

I can't figure out an explanation as to why it went to the network boot up.

Also the reason I have the CDrom as first boot option is because generally the keyboard doesn't turn on... I thought I fixed that by pulling out the cmos battery and going from a fresh slate but clearly that didn't work. this is also one of the reasons i leave the computer on; so I don't have to struggle randomly trying to get the keyboard turned on. But yeah, easier to take the cd out of the drive than it is to wait for a keyboard to turn on to then hit reset and pick the boot options.

I'll try starting it up on the network option and see if it'll give me those same errors just to rule it out.

Should I maybe be trying to use x86 instead of x64?


edit: so what I'm saying is no, the bios order is unchanged and yes, the hdd's are found.

---

### Post by Mystake on 2011-02-26
im going off top of my head here,

what HDD should grub be going for?
when I hit E, im trying to think.. it does boot=(hd0,msdos1)

could that play any part in it? I switched it to hd0,1 and came back with the same blinking cursor... so this makes me believe it is a Grub issue?

im gunna also turn off autodetect in the bios if it's enabled. I can disable APIC from in there too, just throwing that out there.

---

### Post by oldfred on 2011-02-27
Grub2 is in sda, or in BIOS you should see it as the 250GB drive. So that  should be first in BIOS or or if you have f12 as a one time boot choice you can use that to test.

---

