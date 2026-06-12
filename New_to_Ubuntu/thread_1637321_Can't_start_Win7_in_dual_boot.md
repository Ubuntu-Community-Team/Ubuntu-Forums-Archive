---
title: "Can't start Win7 in dual boot"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Telos3K on 2010-12-04
I installed Ubuntu via Wubi a month ago and got almost everything up and running fine. I still am using Windows for a few legacy apps for which wine doesn't work. (I'm sure I'll eventually migrate entirely off of Windows, but give me time.)  About two days ago, windows stopped running from the dual boot.  I get:

The instruction at 0xfc0lca53 referenced memory at 0x0016flac
The memory could not be read.

I ran the various Windows system repair options and they did not work.

I've also had instances in which, when restarting in Ubuntu, the system hangs and I have to do a hard reboot, although this may be unconnected to the problem with Windows.

How do I repair this?

Thanks!

---

### Post by anand_30 on 2010-12-04
Just asking:

Is your Hard disk healthy?

I have had experiences of hang at start and crashing of both ubuntu as well as windows on my old desktop.At that time my HD was failing.
 
So as ubuntu is also hanging at restart it seems to me that may be its a hardware problem.

Other than this I am out of ideas.

---

### Post by Telos3K on 2010-12-04
Brand new machine, actually (an Asus UL30a, and yes, I addressed the [hard disk parking issue]("https://wiki.ubuntu.com/AsusUL/HddCycles")).....

---

### Post by Rubi1200 on 2010-12-04
Hi and welcome to the forums :)

Use a LiveCD to boot the computer, choosing to try not install Ubuntu.

Run the boot info script (link at the bottom of my post with instructions).

Post the results back here please.

Thanks.

---

### Post by Telos3K on 2010-12-04
Here you go.  What's next?  Many thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,716,280   274,904,279   244,188,000   7 HPFS/NTFS
/dev/sda3         274,904,280   976,768,064   701,863,785   f W95 Ext d (LBA)
/dev/sda5         274,904,343   976,768,064   701,863,722   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       6ffd5af6-1f3d-4232-95a1-734e45f685aa   ext4                                     
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        CC624CD7624CC842                       ntfs       OS                            
/dev/sda5        B19401CA6A583703                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set cc624cd7624cc842
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set cc624cd7624cc842
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro acpi_backlight=vendor  quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single acpi_backlight=vendor
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/dev/sda5    /media/DATA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0



================= sda2/Wubi: Location of files loaded by Grub: =================


  15.6GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.32-24-generic
   6.3GB: boot/initrd.img-2.6.32-25-generic
   7.5GB: boot/initrd.img-2.6.32-26-generic
    .8GB: boot/vmlinuz-2.6.32-24-generic
  11.5GB: boot/vmlinuz-2.6.32-25-generic
  12.2GB: boot/vmlinuz-2.6.32-26-generic
   7.5GB: initrd.img
   6.3GB: initrd.img.old
  12.2GB: vmlinuz
  11.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 d8 b4 62 10  |........?.....b.|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 2a 97 d5 29 00 00  |......?...*..)..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

---

### Post by Rubi1200 on 2010-12-05
As far as I can tell, the results of the script look normal. 

I suspect this is a hardware issue, possibly faulty memory, and suggest you look into that more.

Other than that, you may want to wait and see if others have some more ideas.

I suspect the problems with Ubuntu are related to the general hardware issue, if indeed that is the cause.

---

### Post by sikander3786 on 2010-12-05
Me too suspect like it is a Hardware issue probably faulty RAM. I would suggest to rule that out first. The test might run over-night so be prepared ;-)

You can boot an Ubuntu Live CD/USB and "Test Memory".

Press any key as soon as the computer starts booting from the disc. You'll see the menu.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by Telos3K on 2010-12-05
Something I perhaps should have mentioned before:  the problems began after two sets of updates via Update Manager.  Does it make sense to try and undo those updates and see what happens? Not that I yet know how to do this, but I'll search the forum....

Sikander, I'll try a memory check --although I did a memory check in windows recovery mode and it detected nothing.  Ruby, when you say a "hardware problem," I assume you mean a problem with how Ubuntu interacts with the hardware, rather than mechanically faulty hardware (a possible RAM issue aside).  In the same way, for example, that there is [random screen flickering]("https://wiki.ubuntu.com/AsusUL#Random screen flickering with Intel 4500MHD Graphics Card") with the video card on my Asus.

---

### Post by sikander3786 on 2010-12-06
Rather than RAM issue, because Live CD/USB just works well (doesn't it?), I have started thinking of trying to repair Windows startup from a Windows install/repair disc. Your Wubi install might get borked that way but still, you'll be able to mount that root.disk folder in Windows and can extract any important data from there.

So, boot a Windows disc and perform startup repair 3 times. Yes 3 times at least. Then try to boot Windows.

Lets hope something un-usual doesn't happen here :-)

---

### Post by zipteye on 2010-12-06
> **Telos3K said:**
> I installed Ubuntu via Wubi a month ago and got almost everything up and running fine. I still am using Windows for a few legacy apps for which wine doesn't work. (I'm sure I'll eventually migrate entirely off of Windows, but give me time.)  About two days ago, windows stopped running from the dual boot.  I get:

The instruction at 0xfc0lca53 referenced memory at 0x0016flac
The memory could not be read.

I ran the various Windows system repair options and they did not work.

I've also had instances in which, when restarting in Ubuntu, the system hangs and I have to do a hard reboot, although this may be unconnected to the problem with Windows.

How do I repair this?

Thanks!

After "The memory could not be read", do you get a OK button?
Does it boot to windows after that?

If so, did you try:   sfc /scannow
Run windows update.

90% percent sure that it is not a hardware problem.
Possibly (probably) a Driver problem.


Last ditch? Update BIOS

---

### Post by beew on 2010-12-06
Wubi is not a dual boot. Just saying. I can't solve your problem as I don't know anything about Wubi, but I would suggest that you uninstall Wubi the minute you  get windows running and install Ubuntu in a real partition if you desire a genuine dual boot.

---

### Post by Telos3K on 2010-12-06
In windows, after OK I get  > system recovery option > select keyboard input method > Next > startup repair

which returns a message saying that Windows cannot repair the problem.  I click OK and the machine shuts down.

If reinstalling everything is what I have to do, Im willing do to that (and as a real dual boot with a partition), but having spent a couple of weeks in a rough march up the learning curve, what can I do to make it easier the second time around?  One problem is that while almost all of my data is backed up, my OS (including root.disk) is not.  But can I even use root.disk if I'm not using wubi?

Suppose I just figure out a way to migrate over the last legacy apps from windows, and never go into windows?  Or is wubi inherently more unstable than a dual boot, so I might as well get it over with?

---

### Post by bcbc on 2010-12-06
Why did you add the /host mount for /dev/sda2 in /etc/fstab? This happens automatically with wubi and it's set to sync writes immediately - to limit damage in the event of hard crashes. I'm not even sure you can override /host in this manner, but I'm curious what the reason was for adding it.

by the way, you can always access the root.disk from a live CD and copy data off it if you need to. The [wubi guide]("https://wiki.ubuntu.com/WubiGuide") shows how to loop mount it.

---

### Post by Telos3K on 2010-12-07
If I somehow managed to add a host/ mount I shouldn't have, it was in the beginning, when I was even more lost and under the impression that the way to access my Windows files from Ubuntu was via NTFS config.  (Now of course, I just go in through DATA.)

I'm basically now seeing this as a straight wubi to partition migration, will review the docs and yell if (when) I need help....

---

### Post by bcbc on 2010-12-07
Here's a howto on migrating wubi: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Telos3K on 2010-12-11
This is very helpful -- but given that my windows is corrupted,  will I be able to do the whole thing (including partitioning) from the LiveCD (it appears so...) and then reinstall Windows without damaging the Ubuntu side of the partition (given some discussion of how Windows installs can wipe out hard disks.....)

---

