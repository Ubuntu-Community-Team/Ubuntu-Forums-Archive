---
title: "Wiping Windows &amp; problems with 10.10 netbook edition - downgrade?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by dieschr on 2011-04-23
Hi everybody, 

I really am as green as those coffee beans when it comes to ubuntu. Always used Windows but want to learn something new and potentially better. 

Here are the specs: 

Asus Eee 1015PE
Intel Atom N450
1GB DDR2
250GB SATA
Intel Graphics Media Accelerator 3150, 256MB shared

First off, I'd like to say that I wouldn't even have gotten as far as installing Ubuntu if it weren't for this forum, so thanks guys - the posts and help was really useful and made me not give up after all the "initramfs" error messages!

I installed Ubuntu 10.10 netbook edition  and used UNet Bootin to boot from my SD card. 

It's been about 10 years since I last partitioned a hard drive so really I wasn't all that confident so chose to let UNetbootin handle that. I chose to install Ubuntu alongside Windows 7 Starter and selected a slightly larger size for the Ubuntu install than windows (I really cant remember the size, something around 10GB for Ubuntu and a little less for Windows, as I don't intend to use it anymore).  

At the time I thought there were only 2 partitions on the laptop, 1 for Windows and 1 hidden one for the Windows recovery. But have now found out that's not quite the case, according to this website: [https://wiki.archlinux.org/index.php/Asus_Eee_PC#Eee_1015_PE.2FPEM](https://wiki.archlinux.org/index.php/Asus_Eee_PC#Eee_1015_PE.2FPEM) 
I presume that Asus wouldn't really have a reason to change this set up for my version of the netbook. 

Also, Ubuntu has been crashing and freezing on me several times since the install (about 24 hours ago). There are no obvious reasons for me (as a newbie) to see. I have been installing a few "apps", but I really couldn't pinpoint which one would cause that. Twice it's happened during shutdown, screen freezes, and nothing happens, so have to just hold down the power button. 
I also find Ubuntu running quite slow, compared to Windows 7 starter. I've had the music app open and firefox and it's all just really slow, switching between the two, etc.

So, I'm having a major brainfreeze and just not sure what to do: 

1. I'm not necessarily looking for a fix with the version I have but wondered whether I should just install the LTR 10.04 desktop version? I also don't like not being able to move the left hand bar on the desktop on the netbook edition as I now have to scroll horizontally to see a full firefox page. Doesn't all fit on the screen with the bar there. 

2. Is it possible that the crashes and slow running are due to Windows being installed alongside Ubuntu?

3. How do I find out which way my hard drive is partitioned up?

4. Is it possible to wipe all of Windows 7 and just leave the hidden recovery partition and have the other partitions for Ubuntu and my data? If so, how do I do that?
  
5. How would I (in case I do want Windows back) start the recovery process for it? 

Sorry for the rambling, just wanted to include all I thought relevant. Give me a shout if you need anything else...
Thanks for any help, advice you can give.

---

### Post by pi3.1415926535... on 2011-04-23
1. You could install 10.04 LTS, or you could wait for the release of 11.04, though [Fuduntu]("http://www.fuduntu.org") is designed specifically for netbooks.

2. It is unlikely that the crashes are being caused by the fact that you are dual-booting.

3. GParted is the default partition editor for Ubuntu it can be found in System>Administration. It will list all of the partitions you have.

4. I would recommend keeping Windows 7 for now, because you may choose to go back to it, or find it useful for running certain applications.

5. To start the recovery process, assuming you are using the [GRUB]("https://help.ubuntu.com/community/Grub2") bootloader, you would select the entry corresponding to the recovery partition.

Also it is helpful to separate different questions into separate posts.

---

### Post by Hedgehog1 on 2011-04-23
If you would like us to have a look at the drive & partition layout  please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

p.s. the 'all four primary partitions already taken' issue you have is also a problem for newer HP laptops.  We have several solutions.

---

### Post by madjr on 2011-04-23
ubuntu 10.10 netbook edition has a known issue of being slow thx to the old "mutter"...

this has been fixed in 11.04 with compiz.

so you should either use 10.10 desktop edition or wait 4 days for 11.04 final version.

if you need further help we'll be glad to help :D

---

### Post by dieschr on 2011-04-25
Thanks for all your input. The crashes of 10.10 netbook edition continue. 90% of the time when I try and shut down the computer it just gets stuck. I tried the whole ctrl + alt + backspace or ctrl + alt + F1, and even another solution found from the forum - hold alt sysrq and press REISUB. None of them had any effect. 

Anyways, here is the info on the partitions through bootinfoscript (also took 10 attempts at figuring out, i've just never worked with code :-k): 

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *          2,048   456,896,511   456,894,464   7 HPFS/NTFS
/dev/sda2         456,896,512   474,600,865    17,704,354  1b Hidden W95 FAT32
/dev/sda3         488,353,792   488,397,167        43,376  ef EFI (FAT-12/16/32)
/dev/sda4         474,601,470   488,353,791    13,752,322   5 Extended
/dev/sda5         474,601,472   487,655,423    13,053,952  83 Linux
/dev/sda6         487,657,472   488,353,791       696,320  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,744,511     7,736,320   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56ED56396477F240                       ntfs                                     
/dev/sda2        86F4-D40A                              vfat       ˆˆˆˆˆˆˆ»íÝÝ                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        16b101e4-85c1-4fd8-a531-194497b710a2   ext4                                     
/dev/sda6        b6e8edaf-7901-4a77-9fd0-33e00c29fc51   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DCE0-D531                              vfat       SD CARD 4GB                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/SD CARD 4GB       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=16b101e4-85c1-4fd8-a531-194497b710a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=16b101e4-85c1-4fd8-a531-194497b710a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=16b101e4-85c1-4fd8-a531-194497b710a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=16b101e4-85c1-4fd8-a531-194497b710a2 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 16b101e4-85c1-4fd8-a531-194497b710a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58bce434bce40df6
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 86f4-d40a
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=16b101e4-85c1-4fd8-a531-194497b710a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b6e8edaf-7901-4a77-9fd0-33e00c29fc51 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 245.6GB: boot/grub/core.img
 243.3GB: boot/grub/grub.cfg
 249.1GB: boot/initrd.img-2.6.35-22-generic
 249.1GB: boot/initrd.img-2.6.35-28-generic
 245.6GB: boot/vmlinuz-2.6.35-22-generic
 245.6GB: boot/vmlinuz-2.6.35-28-generic
 249.1GB: initrd.img
 249.1GB: initrd.img.old
 245.6GB: vmlinuz
 245.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 72 0a  |.X.SYSLINUX...r.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 0c 76 00 c7 3a 00 00  00 00 00 00 02 00 00 00  |..v..:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 31 d5 e0 dc 4e  4f 20 4e 41 4d 45 20 20  |..)1...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 5c  f7 2c 00 66 ba 00 00 00  |..E}.f.\.,.f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```Basically, what I'd like to do is to have Ubuntu on the sda1 (smaller size than it is now), Windows recovery on the sda2 and a third partition, which should just be for my personal data. 

Is this even possible? I've tried to do it, but really can't figure out how to do that with gparted or during installation. 

I don't want to wait 3 days for the next version as I'll be leaving country by then and like to have an up and running OS by then...

Thanks for your help!

---

### Post by madjr on 2011-04-25
> **dieschr said:**
> 

Is this even possible? I've tried to do it, but really can't figure out how to do that with gparted or during installation. 



yes, something similar is possible, so if you dont mind attaching a pic of your gparted showing the partitions (press the PrtSc key), we can further guide you.

> **dieschr said:**
> 

I don't want to wait 3 days for the next version as I'll be leaving country by then and like to have an up and running OS by then...

Thanks for your help!

you dont have to wait 3 days, you can download 11.04 beta2 right now, is pretty stable and will update to the final version by itself.

---

### Post by dieschr on 2011-04-26
ok, here we go with gparted screenshot. i have managed to format sda1, but that's about it. hopefully this helps:

---

### Post by madjr on 2011-04-26
ok, thx for the screen, things are much clear now.

i think the crashes you are having could be due not only to the sluggishness of the old netbook edition, but also because the swap partition is a bit small. I recommend like 800mb+ (you can also find more recommendations online).

now, for what you want to do with the partitions, i recommend you do it from ubuntu on an usb stick (or sd card if that worked for you).

basically you will want to backup your stuff and then format, resize and/or delete some of the partitions.

remember that the ubuntu partition needs to be formated in ext4 and needs a swap of like 800mb as i mentioned.

you can resize them till they become what you want.

experimenting with sda1 and sda4 should be ok, just leave sda2 and 3 as is.

you cant have more than 4 primary partitions (1,2,3 and 4), so one of them became extended (sda4) to allocate more sub partitions.

if you need more help with partitioning, this should help you:

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

---

### Post by dieschr on 2011-04-27
Aaaaallllright, well, some good news and some bad news. 

Thanks for the link re partitioning madjr, that explained things and helped! 

So, I have now partitioned as per attached screenshot. For some reason unbeknown to me it I now have 2 x 1MB of unused space - is this a major problem? I mean it looks untidy, but if it doesn't affect the performance I'll just leave it. Took me long enough to get to this place, haha.  

Also, is it correct to have my /home partition in ext4 file format? It didn't give me an ntfs option for that one, so wasn't sure what to do with that? 

So i have installed 11.04 beta 2, which at first glance seemed to work, 

BUT: every time I try to shut down, suspend, hibernate or restart the screen freezes. All bars dissappear and just the background image & (sometimes) mousepointer remain. None of the short cuts to get back to anything work and I have to hold down the power button. When I click suspend or hibernate the screen goes black (not off, just black colour) and nothing else happens. I can't get back from that state either, so have to do the same as above. 

I have tried to see anything relating to this in the logfile viewer, but not sure where to look and what to look for. I have checked the "dmesg" but don't think there is anything, but really - what do I know? 

Is there anything I can check (something like chkdsk in windows?) to see if there is a hardware problem or where the problem lies or how to find some sort of error message? 

Tearing my hair out. haha. But thanks for the continued help :)

---

### Post by madjr on 2011-04-28
> **dieschr said:**
> Aaaaallllright, well, some good news and some bad news. 

Thanks for the link re partitioning madjr, that explained things and helped! 

So, I have now partitioned as per attached screenshot. For some reason unbeknown to me it I now have 2 x 1MB of unused space - is this a major problem? I mean it looks untidy, but if it doesn't affect the performance I'll just leave it. Took me long enough to get to this place, haha.  

Also, is it correct to have my /home partition in ext4 file format? It didn't give me an ntfs option for that one, so wasn't sure what to do with that? 

So i have installed 11.04 beta 2, which at first glance seemed to work, 

BUT: every time I try to shut down, suspend, hibernate or restart the screen freezes. All bars dissappear and just the background image & (sometimes) mousepointer remain. None of the short cuts to get back to anything work and I have to hold down the power button. When I click suspend or hibernate the screen goes black (not off, just black colour) and nothing else happens. I can't get back from that state either, so have to do the same as above. 

I have tried to see anything relating to this in the logfile viewer, but not sure where to look and what to look for. I have checked the "dmesg" but don't think there is anything, but really - what do I know? 

Is there anything I can check (something like chkdsk in windows?) to see if there is a hardware problem or where the problem lies or how to find some sort of error message? 

Tearing my hair out. haha. But thanks for the continued help :)

congrats!! you are getting the hang of partitioning. You'll be a pro soon once you do it once or twice more :)

question: how is the speed compared to 10.10 ? same or better ?

anyway the partitions look pretty ok, you can allocate those 1mbs back into the main partitions if you want. Is pretty easy so i think you'll figure it out :p

the only future potential problem i see is that sda5 ( / or root) is a bit small. Some programs and updates might fill up quickly in a few months.

people usually give it at least 10gb or fuse "/" and "home" in one, by changing home to / (linux can only have "swap and /", which also acts as home or "swap, / and a separate home"). / and/or home can only be of a linux file system like ext4. Linux can access ntfs, so you can always later create one of those for sharing some files between linux and windows.

about the shutdown problem, that is pretty strange.

have you applied all natty updates? ubuntu 11.04 final will be due in a few hours, so you might get a good number of updates during the week.

did this also happen in 10.10 ?

you might want to report it or see if someone else has the same problem with your model

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[http://ubuntuforums.org/showthread.php?t=734460](http://ubuntuforums.org/showthread.php?t=734460)

you want to give as much info as possible so follow the guide please.

after reporting you can post here the bug report link.

if you need further help let us know ):P

---

### Post by dieschr on 2011-07-06
Thanks madjr, 
I know this is very delayed but this is the first time I have some sort of decent internet connection (by which I mean it doesn't take 30 minutes to load google.com. Only about 10 mins or so. haha. Admittedly, I should probably have planned all this a little better to fix problems before travelling but anyways: 

I have installed all updates that keep coming up but the problem persists. It also happened in version 10.10. 

I have not been able to follow the directions in terms of reporting the bug officially. However, the computer still does not shut down properly. There seems to be no pattern as to what happens when I press shut down. 
Sometimes it freezes before I can even press OK to shut down. Sometimes it goes to the blank desktop and then freezes and on a few occasions I got the attached screens. I couldnt take a screen shot so had to take a bad photograph of the screen. Each image is from a different occasion. 

Maybe this helps in some form or gives you any indication as to where the problem might lie? I just haven't got the internet access to go through all the reporting of bugs as it takes so long to load sites, etc. 

I hope this uploads here too, and maybe someone can shed some light? 
THanks for any help you can give! Sunny and humid greetings from Belize!

---

### Post by dieschr on 2011-08-01
Well, a few days after I posted this, I installed one of the regular  updates and now ubuntu shuts down! So maybe someone saw my post or maybe  there are ubuntu gods looking out for me... In any case - thanks for  the help!

---

### Post by madjr on 2011-08-02
> **dieschr said:**
> Well, a few days after I posted this, I installed one of the regular  updates and now ubuntu shuts down! So maybe someone saw my post or maybe  there are ubuntu gods looking out for me... In any case - thanks for  the help!

good to hear this!

---

