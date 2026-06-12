---
title: "Grub error"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Gluebuntu on 2010-12-19
Hi,

I am having a problem with booting up my computer: I had windows 7 and Ubuntu 10.04 in a dual boot. Unfortunately I recently wrecked Ubuntu so it wouldn't boot.

To fix this I booted into an Ubuntu 10.10 USB I had and backed up all my important files to another USB. After that was finished, I installed Ubuntu 10.10 to the /dev/sda3 ext4 partition without formatting it first. The install completed fine but when I tried to boot, grub came up with an error:

```
error: the symbol 'grub_xputs' not found
grub rescue>
```So I thought "Maybe I just need to format the partition when I install Ubuntu." I did the install again this time formatting /dev/sda3. When I tried to boot, grub came up with the same error message! :?

Are there any commands I can perform (from USB or grub rescue) to give you more information?

Please help me to get this working. :(

---

### Post by theasprint on 2010-12-19
Is your Ubuntu a Wubi installation?

Grub Rescue mode only have a few commands.

Here is a link for a list of commands: [https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

So far I have only encountered grub-rescue once. But i did not face the problem. Instead i got pissed and reformatted my whole  PC.

But don't worry. The link i gave you looks promising

Good luck:D

---

### Post by sikander3786 on 2010-12-19
See this page for instructions on how to boot from Grub Rescue Prompt.

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
courtesy of forum member *drs305*

Or if unsure, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by Rubi1200 on 2010-12-19
The results of the boot info script recommended by sikander3786 would really help us.

In general, a > grub_xputserror indicates that GRUB is missing some files.

The best method to deal with this is to purge and reinstall GRUB, but let's see the results first please.

---

### Post by Gluebuntu on 2010-12-19
Thank you for the replies.

My Ubuntu 10.10 installation was not from Wubi but I used a Live USB (with persistence.)

Thanks, sikander3786, for the link.

I tried the boot_info_script and here is the output that was in RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 258515279 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   144,945,941   144,943,894   7 HPFS/NTFS
/dev/sda2         285,616,126   312,545,279    26,929,154   5 Extended
/dev/sda5         285,616,128   291,573,759     5,957,632  82 Linux swap / Solaris
/dev/sda6         291,575,808   312,545,279    20,969,472  82 Linux swap / Solaris
/dev/sda3         144,954,495   285,603,569   140,649,075  83 Linux
/dev/sda4         312,545,280   312,576,704        31,425  1b Hidden W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       56fd1625-21e8-6c46-978e-954017f72fdf   ext2                                     
/dev/sda1        EE20E44420E4157D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        90d2bf6f-10bc-41f7-803c-c367c2ae0aea   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f612c358-e216-4e5a-9358-4dfae471ec20   swap                                     
/dev/sda6        017c9f63-162f-49d2-9da0-d8ab2bc3779c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E87C-9995                              vfat       UBUNTU2G                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=90d2bf6f-10bc-41f7-803c-c367c2ae0aea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=90d2bf6f-10bc-41f7-803c-c367c2ae0aea ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ee20e44420e4157d
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=90d2bf6f-10bc-41f7-803c-c367c2ae0aea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f612c358-e216-4e5a-9358-4dfae471ec20 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=017c9f63-162f-49d2-9da0-d8ab2bc3779c none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/core.img
 121.6GB: boot/grub/grub.cfg
  75.2GB: boot/initrd.img-2.6.35-22-generic
 132.3GB: boot/vmlinuz-2.6.35-22-generic
  75.2GB: initrd.img
 132.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 34 02  |.X.SYSLINUX...4.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  aa b5 3b 00 e6 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 95 99 7c e8 4e  4f 20 4e 41 4d 45 20 20  |..)..|.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 f8 27 38 00  66 ba 00 00 00 00 bb 00  |}.f..'8.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Thank you again for helping me.

---

### Post by tipsword on 2010-12-19
I too just downloaded and installed 10.10 on my new laptop - I got the o/s updated to try and get the broadcom wifi drivers to work. On reboot mine went to grub rescue with error: no such device: 90b2dd01-9ba7-4bd0-9749-ed73bc03545
 
I have LS ... shows (hd0) when I try and look at the boot properties ls (hd0)/boot I get error: unknown filesystem
 
As I mentioned I just got the laptop is (was) win 7 home premium (Samsung R580) 
 
Thoughts or am I hosed
 
I am working on making a usb stick to boot to and will look at those mount instructions again.  I am totally/completely a Linux know nothing... I support Win XP / 7 for work and thats all I know.
 
Thanks,
Brian   :confused:

---

### Post by Gluebuntu on 2010-12-19
Although I can't help you with your actual problem, here is a link to a really easy and useful Linux USB creator. It only works on windows I think.

[http://old.linuxliveusb.com/](http://old.linuxliveusb.com/)

I've used this loads of times and it's really helpful. (And it looks nice too!) :D

---

### Post by tipsword on 2010-12-19
Thank you Glue ~ once I get that going (down loading iso now) how to I get back to my old stomping grounds.  It's going really suck if I have whack this hard disk and reinstall win 7 altogether.
 
feeling really sheepish as I read a bunch before I did this and didn't follow the first rule of making a back out for yourself *sigh* who knew :-D
 
Brian

---

### Post by oldfred on 2010-12-19
tipsword, so we do not get confused, please start your own thread and post a copy of the boot script in that.

The install of wubi nor the installs of grub2 to partitions should be a problem, but you should not normally install grub to a partition.

Can you manually boot?
grub rescue:
ls # Do you see (hd0), (hd0,3) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,3) in the next command.
configfile (hd0,3)/boot/grub/grub.cfg


Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by tipsword on 2010-12-19
> **oldfred said:**
> tipsword, so we do not get confused, please start your own thread and post a copy of the boot script in that.
 
The install of wubi nor the installs of grub2 to partitions should be a problem, but you should not normally install grub to a partition.
 
Can you manually boot?
grub rescue:
ls # Do you see (hd0), (hd0,3) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,3) in the next command.
configfile (hd0,3)/boot/grub/grub.cfg
 
 
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
 
~~~
 
Done, new thread created ~ now how to I fix this thng?  I am really tired and very frustrated and need my laptop back.
 
Thank you in advance for any help you might have to offer, it's truly appreciated.
 
Brian

---

### Post by Gluebuntu on 2010-12-20
Your welcome, tipsword.

From the boot info script up there, can you see any errors or problems? This stuff is beyond me. You can make it "for the human being" but Linux is still Linux. :) (Not to say that I don't want to deal with it.)

Is there a way I can reinstall grub to the /dev/sda3 partition from my Live USB?

Thank you all again. (The Ubuntu community is very helpful isn't it?)

---

### Post by oldfred on 2010-12-20
Gluebuntu
See my post #9, only the first sentence was for tipsword to try to avoid this type of confusion. 

Can you manually boot. The minor problems I see in boot script should not prevent booting.

If you cannot manually boot, so you can reinstall grub from inside your system, you need to use the liveCd to reinstall grub.

---

### Post by Gluebuntu on 2010-12-20
I tried putting this into grub recue:

```
grub rescue>configfile (hd0,3)/boot/grub/grub.cfg
```But it says:

```
Unknown command 'configfile'
```0,3 should be the correct one because it was one of the numbers returned when I did the ls command.
sda3 is the one that has Ubuntu 10.10 in it.

My computer is a net-book so sadly I cannot use a CD on it but is it possible for me to reinstall grub some how from a Live Ubuntu USB? I just don't know how to get it to install grub to the sda3 partition instead of the USB drive.

---

### Post by oldfred on 2010-12-20
A liveUSB is the same as a liveCD for these instructions:

Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

If you have Ubuntu in sda3 and no separate /boot:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda3 and want grub2 in drive sda's MBR:
#Find linux partition, change sda3 if not correct:
sudo fdisk -l
#confirm that linux is sda3
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

If the above 'short' version does not work, then we have to do the full chroot version.

If the quick version does not work, post this so we can see if something else is missing:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Gluebuntu on 2010-12-21
O.K. I booted up my computer with my Ubuntu USB, opened a terminal and put in this command:

:popcorn:

[LEFT]```
$ sudo fdisk -l
```The output:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x998abf18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9023    72471947    7  HPFS/NTFS
/dev/sda2           17779       19456    13464577    5  Extended
/dev/sda3            9024       17778    70324537+  83  Linux
/dev/sda4           19456       19457       15712+  1b  Hidden W95 FAT32
/dev/sda5           17779       18150     2978816   82  Linux swap / Solaris
/dev/sda6           18150       19456    10484736   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     1956565    b  W95 FAT32
```Then I put in this:

```
$ sudo mount /dev/sda3 /mnt
```There was no output to the screen.

After that I put in the grub install command:

```
$ sudo grub-install --root-directory=/mnt/ /dev/sda
```The output for that was:

```
Probing devices to guess BIOS drives. This may take a long time.
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
```What do you suggest I do now that it seems to have been installed? Do I need to configure grub or something? :)
[/LEFT]

---

### Post by sikander3786 on 2010-12-21
That seems successful. Reboot and see.

Don't need to configure anything else.

---

### Post by Gluebuntu on 2010-12-22
Horray! Grub is working! When I boot my computer up I the 

```
grub>
```prompt. There is one more problem though: now that I have grub, how to I boot into Ubuntu? Before, when grub was working, I could just choose wich operating system I wanted to boot into from a list.

Now what should I do? :?

---

### Post by psusi on 2010-12-22
You don't want two swap partitions so you probably should fix that.  As for your grub problem, run the bootinfo script again.

---

### Post by oldfred on 2010-12-22
Grub still is not correct as it did not load the menu.

You could try manual boot:

ls # Do you see (hd0), (hd0,3) ? 
configfile (hd0,3)/boot/grub/grub.cfg

Boot script as suggested by psusi may tell us what else is wrong. Or we just may have to run the full chroot total install of grub.

---

### Post by Gluebuntu on 2010-12-23
I tried manuall boot but grub said "ls" was not a command and although I can't remember the exact error message, something was wrong (I think) with the arguments passed to "configfile (hd0,3)/boot/grub/grub.cfg"

I ran boot info script again and this is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 258515279 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   144,945,941   144,943,894   7 HPFS/NTFS
/dev/sda2         285,616,126   312,545,279    26,929,154   5 Extended
/dev/sda5         285,616,128   291,573,759     5,957,632  82 Linux swap / Solaris
/dev/sda6         291,575,808   312,545,279    20,969,472  82 Linux swap / Solaris
/dev/sda3         144,954,495   285,603,569   140,649,075  83 Linux
/dev/sda4         312,545,280   312,576,704        31,425  1b Hidden W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    31,266,815    31,266,784   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       56fd1625-21e8-6c46-978e-954017f72fdf   ext2                                     
/dev/sda1        EE20E44420E4157D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        90d2bf6f-10bc-41f7-803c-c367c2ae0aea   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f612c358-e216-4e5a-9358-4dfae471ec20   swap                                     
/dev/sda6        017c9f63-162f-49d2-9da0-d8ab2bc3779c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E87C-9995                              vfat       UBUNTU2G                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        285E-DDC7                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/56fd1625-21e8-6c46-978e-954017f72fdf ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/90d2bf6f-10bc-41f7-803c-c367c2ae0aea ext4       (rw,nosuid,nodev,uhelper=udisks,commit=0,commit=0)
/dev/sdc1        /media/285E-DDC7         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=90d2bf6f-10bc-41f7-803c-c367c2ae0aea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=90d2bf6f-10bc-41f7-803c-c367c2ae0aea ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 90d2bf6f-10bc-41f7-803c-c367c2ae0aea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ee20e44420e4157d
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=90d2bf6f-10bc-41f7-803c-c367c2ae0aea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f612c358-e216-4e5a-9358-4dfae471ec20 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=017c9f63-162f-49d2-9da0-d8ab2bc3779c none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/core.img
 121.6GB: boot/grub/grub.cfg
 132.3GB: boot/grub/stage2
  75.2GB: boot/initrd.img-2.6.35-22-generic
 132.3GB: boot/vmlinuz-2.6.35-22-generic
  75.2GB: initrd.img
 132.3GB: vmlinuz

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f612c358-e216-4e5a-9358-4dfae471ec20 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 34 02  |.X.SYSLINUX...4.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  aa b5 3b 00 e6 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 95 99 7c e8 4e  4f 20 4e 41 4d 45 20 20  |..)..|.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 f8 27 38 00  66 ba 00 00 00 00 bb 00  |}.f..'8.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

@psusi

Why is it bad to have two swap partitions? (I don't disagree, I just would like to learn why.)

---

### Post by psusi on 2010-12-23
> **Gluebuntu said:**
> Why is it bad to have two swap partitions? (I don't disagree, I just would like to learn why.)

It's a waste of space.  Also it appears that you have managed to install both grub2 and grub legacy.  You need to reinstall grub2.

---

### Post by oldfred on 2010-12-23
You did not install grub2 as per post #14. Somehow you have grub legacy.

You need to totally uninstall both grub2 & grub legacy and reinstall grub2.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by sikander3786 on 2010-12-23
> **oldfred said:**
> You did not install grub2 as per post #14. Somehow you have grub legacy.

You need to totally uninstall both grub2 & grub legacy and reinstall grub2.


Just to add to that a bit, you need to boot an Ubuntu Karmic/Lucid or Maverick Live CD/USB. Older Ubuntu releases used to come with Grub Legacy and you might be installing Grub Legacy again ;-)

---

### Post by Gluebuntu on 2010-12-23
Thank you very much guys!!!! I followed the tutorial you suggested, oldfred, and it works! I can restart my computer and be presented by grub a menu allowing me to choose what OS I boot into. :D I am posting this from Ubuntu 10.10 on my computer now. Thanks to everyone who helped I am very very glad to use my computer again! (The Live USB was very slow...)

I'm very grateful for all the help you gave me.

I can now mark this thread as [SOLVED]

The reason I get so over excited is because I'm a younger user :smile:

---

### Post by oldfred on 2010-12-23
Hey, we not so young users get excited when something works too.:)

Glad it is now working. If you have other issues please feel free to start a new thread with that issue.

---

