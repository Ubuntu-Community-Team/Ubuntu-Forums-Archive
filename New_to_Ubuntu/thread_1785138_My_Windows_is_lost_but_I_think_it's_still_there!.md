---
title: "My Windows is lost but I think it's still there!"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by citronex on 2011-06-17
Hi,
it is needless to say that I'm a complete beginner.  
I was running a dual boot with windows vista and ubuntu 10.10.  after updating to 11.04 (another mistake) I used the computer janitor and without knowing what I was doing I deleted the windows grub. Now my windows is lost somewhere, and I can't even mount the partition where it was in.  

I tried following other threads but I always got stuck somewhere.  For instance, I could not find my menu.lst file under boot/grub. 
I ran some commands, here are my results.


```
citronex@citro-toshiba:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6ae43fb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       31344   250231788    7  HPFS/NTFS
/dev/sda3           31344       38914    60801025    5  Extended
/dev/sda5           37941       38914     7812096   82  Linux swap / Solaris
/dev/sda6           31344       37941    52988928   83  Linux

Partition table entries are not in disk order
```
```
citronex@citro-toshiba:~$ cat /boot/grub/menu.lst > ~/Desktop/menu.txt
cat: /boot/grub/menu.lst: No such file or directory

```
```
citronex@citro-toshiba:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              50G   41G  6.7G  86% /
none                  1.9G  696K  1.9G   1% /dev
none                  1.9G  2.2M  1.9G   1% /dev/shm
none                  1.9G  464K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda2             239G   95M  239G   1% /media/Main_HD

```
```
citronex@citro-toshiba:~$ ls -la /boot
total 21024
drwxr-xr-x  3 root root     4096 2011-05-22 11:47 .
drwxr-xr-x 23 root root     4096 2011-05-22 11:47 ..
-rw-r--r--  1 root root   730039 2011-04-11 00:24 abi-2.6.38-8-generic
-rw-r--r--  1 root root   130313 2011-04-11 00:24 config-2.6.38-8-generic
drwxr-xr-x  3 root root    12288 2011-05-22 11:47 grub
-rw-r--r--  1 root root 13125062 2011-05-10 00:01 initrd.img-2.6.38-8-generic
-rw-r--r--  1 root root   160988 2010-10-22 08:08 memtest86+.bin
-rw-r--r--  1 root root   163168 2010-10-22 08:08 memtest86+_multiboot.bin
-rw-------  1 root root  2654256 2011-04-11 00:24 System.map-2.6.38-8-generic
-rw-------  1 root root     1368 2011-04-11 00:26 vmcoreinfo-2.6.38-8-generic
-rw-------  1 root root  4523936 2011-04-11 00:24 vmlinuz-2.6.38-8-generic

```
```
citronex@citro-toshiba:~$ sudo updatedb && locate menu.lst
[sudo] password for citronex: 
/usr/share/doc/memtest86+/examples/grub-menu.lst

```

Any help would be highly appreciated, for I need this information to work!

Thank you in advance.

Citro. :(

---

### Post by Quackers on 2011-06-17
In the terminal please run ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader is picked up. 
If it is you can reboot hopefully to a grub menu with 2 choices again.
If the Windows Loader is not found by grub.cfg please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by citronex on 2011-06-17
Quackers, thanks so much for your help.
here is the resulting data from the results.txt file:
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   503,537,623   500,463,576   7 NTFS / exFAT / HPFS
/dev/sda3         503,539,710   625,141,759   121,602,050   5 Extended
/dev/sda5         609,517,568   625,141,759    15,624,192  82 Linux swap / Solaris
/dev/sda6         503,539,712   609,517,567   105,977,856  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1874FC1574FBF2FC                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        C6B82B5EB82B4BED                       ntfs       Main_HD
/dev/sda5        ec9c43f9-3aef-4227-9eff-f330cde99890   swap       
/dev/sda6        05af2ba9-32e5-422e-8984-e00ad3bd2055   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/Main_HD           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 05af2ba9-32e5-422e-8984-e00ad3bd2055
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 05af2ba9-32e5-422e-8984-e00ad3bd2055
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05af2ba9-32e5-422e-8984-e00ad3bd2055
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=05af2ba9-32e5-422e-8984-e00ad3bd2055 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05af2ba9-32e5-422e-8984-e00ad3bd2055
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=05af2ba9-32e5-422e-8984-e00ad3bd2055 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05af2ba9-32e5-422e-8984-e00ad3bd2055
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05af2ba9-32e5-422e-8984-e00ad3bd2055
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=05af2ba9-32e5-422e-8984-e00ad3bd2055 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ec9c43f9-3aef-4227-9eff-f330cde99890 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 268.240646362 = 288.021200896  boot/grub/core.img                             1
 250.854766846 = 269.353254912  boot/grub/grub.cfg                             1
 281.399921417 = 302.150864896  boot/initrd.img-2.6.38-8-generic               2
 244.700504303 = 262.745165824  boot/vmlinuz-2.6.38-8-generic                  1
 281.399921417 = 302.150864896  initrd.img                                     2
 244.700504303 = 262.745165824  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  01 00 42 31 7d 5c 50 72  6f 78 79 53 74 75 62 43  |..B1}\ProxyStubC|
00000010  6c 73 69 64 33 32 22 2f  3e 0a 20 20 20 20 20 20  |lsid32"/>.      |
00000020  20 20 3c 44 65 6c 65 74  65 4b 65 79 20 66 6c 61  |  <DeleteKey fla|
00000030  67 73 3d 22 30 78 30 30  30 30 30 30 30 31 22 20  |gs="0x00000001" |
00000040  70 61 74 68 3d 22 5c 52  65 67 69 73 74 72 79 5c  |path="\Registry\|
00000050  4d 41 43 48 49 4e 45 5c  53 4f 46 54 57 41 52 45  |MACHINE\SOFTWARE|
00000060  5c 43 6c 61 73 73 65 73  5c 49 6e 74 65 72 66 61  |\Classes\Interfa|
00000070  63 65 5c 7b 39 33 33 41  43 41 41 42 2d 32 32 37  |ce\{933ACAAB-227|
00000080  41 2d 34 44 41 45 2d 38  31 46 42 2d 45 36 41 32  |A-4DAE-81FB-E6A2|
00000090  44 34 41 30 43 44 42 31  7d 5c 4e 75 6d 4d 65 74  |D4A0CDB1}\NumMet|
000000a0  68 6f 64 73 22 2f 3e 0a  20 20 20 20 20 20 20 20  |hods"/>.        |
000000b0  3c 44 65 6c 65 74 65 4b  65 79 20 66 6c 61 67 73  |<DeleteKey flags|
000000c0  3d 22 30 78 30 30 30 30  30 30 30 31 22 20 70 61  |="0x00000001" pa|
000000d0  74 68 3d 22 5c 52 65 67  69 73 74 72 79 5c 4d 41  |th="\Registry\MA|
000000e0  43 48 49 4e 45 5c 53 4f  46 54 57 41 52 45 5c 43  |CHINE\SOFTWARE\C|
000000f0  6c 61 73 73 65 73 5c 49  6e 74 65 72 66 61 63 65  |lasses\Interface|
00000100  5c 7b 35 35 44 46 35 45  38 37 2d 30 37 38 41 2d  |\{55DF5E87-078A-|
00000110  34 34 32 46 2d 41 32 44  44 2d 43 31 41 37 45 34  |442F-A2DD-C1A7E4|
00000120  30 44 30 33 31 36 7d 5c  50 72 6f 78 79 53 74 75  |0D0316}\ProxyStu|
00000130  62 43 6c 73 69 64 33 32  22 2f 3e 0a 20 20 20 20  |bClsid32"/>.    |
00000140  20 20 20 20 3c 44 65 6c  65 74 65 4b 65 79 20 66  |    <DeleteKey f|
00000150  6c 61 67 73 3d 22 30 78  30 30 30 30 30 30 30 31  |lags="0x00000001|
00000160  22 20 70 61 74 68 3d 22  5c 52 65 67 69 73 74 72  |" path="\Registr|
00000170  79 5c 4d 41 43 48 49 4e  45 5c 53 4f 46 54 57 41  |y\MACHINE\SOFTWA|
00000180  52 45 5c 43 6c 61 73 73  65 73 5c 49 6e 74 65 72  |RE\Classes\Inter|
00000190  66 61 63 65 5c 7b 35 35  44 46 35 45 38 37 2d 30  |face\{55DF5E87-0|
000001a0  37 38 41 2d 34 34 32 46  2d 41 32 44 44 2d 43 31  |78A-442F-A2DD-C1|
000001b0  41 37 45 34 30 44 30 33  31 36 7d 5c 54 79 00 fe  |A7E40D0316}\Ty..|
000001c0  ff ff 82 fe ff ff 02 18  51 06 00 68 ee 00 00 fe  |........Q..h....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 18 51 06 00 00  |............Q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```
Let me know if need anything else.

---

### Post by Quackers on 2011-06-17
Strange!
It seems that both your recovery partition and your main Windows partitions are still there, but the boot script is not picking up anything in them.

I also don't like this bit of the boot script below
```
Unknown BootLoader on sda3

00000000 01 00 42 31 7d 5c 50 72 6f 78 79 53 74 75 62 43 |..B1}\ProxyStubC|
00000010 6c 73 69 64 33 32 22 2f 3e 0a 20 20 20 20 20 20 |lsid32"/>. |
00000020 20 20 3c 44 65 6c 65 74 65 4b 65 79 20 66 6c 61 | <DeleteKey fla|
00000030 67 73 3d 22 30 78 30 30 30 30 30 30 30 31 22 20 |gs="0x00000001" |
00000040 70 61 74 68 3d 22 5c 52 65 67 69 73 74 72 79 5c |path="\Registry\|
00000050 4d 41 43 48 49 4e 45 5c 53 4f 46 54 57 41 52 45 |MACHINE\SOFTWARE|
00000060 5c 43 6c 61 73 73 65 73 5c 49 6e 74 65 72 66 61 |\Classes\Interfa|
00000070 63 65 5c 7b 39 33 33 41 43 41 41 42 2d 32 32 37 |ce\{933ACAAB-227|
00000080 41 2d 34 44 41 45 2d 38 31 46 42 2d 45 36 41 32 |A-4DAE-81FB-E6A2|
00000090 44 34 41 30 43 44 42 31 7d 5c 4e 75 6d 4d 65 74 |D4A0CDB1}\NumMet|
000000a0 68 6f 64 73 22 2f 3e 0a 20 20 20 20 20 20 20 20 |hods"/>. |
000000b0 3c 44 65 6c 65 74 65 4b 65 79 20 66 6c 61 67 73 |<DeleteKey flags|
000000c0 3d 22 30 78 30 30 30 30 30 30 30 31 22 20 70 61 |="0x00000001" pa|
000000d0 74 68 3d 22 5c 52 65 67 69 73 74 72 79 5c 4d 41 |th="\Registry\MA|
000000e0 43 48 49 4e 45 5c 53 4f 46 54 57 41 52 45 5c 43 |CHINE\SOFTWARE\C|
000000f0 6c 61 73 73 65 73 5c 49 6e 74 65 72 66 61 63 65 |lasses\Interface|
00000100 5c 7b 35 35 44 46 35 45 38 37 2d 30 37 38 41 2d |\{55DF5E87-078A-|
00000110 34 34 32 46 2d 41 32 44 44 2d 43 31 41 37 45 34 |442F-A2DD-C1A7E4|
00000120 30 44 30 33 31 36 7d 5c 50 72 6f 78 79 53 74 75 |0D0316}\ProxyStu|
00000130 62 43 6c 73 69 64 33 32 22 2f 3e 0a 20 20 20 20 |bClsid32"/>. |
00000140 20 20 20 20 3c 44 65 6c 65 74 65 4b 65 79 20 66 | <DeleteKey f|
00000150 6c 61 67 73 3d 22 30 78 30 30 30 30 30 30 30 31 |lags="0x00000001|
00000160 22 20 70 61 74 68 3d 22 5c 52 65 67 69 73 74 72 |" path="\Registr|
00000170 79 5c 4d 41 43 48 49 4e 45 5c 53 4f 46 54 57 41 |y\MACHINE\SOFTWA|
00000180 52 45 5c 43 6c 61 73 73 65 73 5c 49 6e 74 65 72 |RE\Classes\Inter|
00000190 66 61 63 65 5c 7b 35 35 44 46 35 45 38 37 2d 30 |face\{55DF5E87-0|
000001a0 37 38 41 2d 34 34 32 46 2d 41 32 44 44 2d 43 31 |78A-442F-A2DD-C1|
000001b0 41 37 45 34 30 44 30 33 31 36 7d 5c 54 79 00 fe |A7E40D0316}\Ty..|
000001c0 ff ff 82 fe ff ff 02 18 51 06 00 68 ee 00 00 fe |........Q..h....|
000001d0 ff ff 05 fe ff ff 01 00 00 00 01 18 51 06 00 00 |............Q...|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
```
While it is perfectly normal for an extended partition to have this message about an unknown bootloader, it is not usually accompanied by what appears to be Windows Registry key details (down the right hand side).

I'm not sure what to recommend at this time.
I'll pm somebody else (who may not be online at the moment) and ask him to take a look and maybe make a recommendation.

---

### Post by citronex on 2011-06-17
Oh! now that I remember, before I lost my windows grub, I had an issue loading into windows, It returned a black screen but unfortunately I don't remember what it said.  I'm a pretty savvy windows user, and I don't think it's anything that can't be solve with the repair disk.  But in order to solve that, I need to get windows back into my operating systems menu :$

Thanks for the help.

---

### Post by Quackers on 2011-06-17
Unfortunately the forum user I contacted doesn't appear to be online at the moment, but he may be on later.
It may be worth running the Windows repair disc and see if the automatic repair will run. It may report a partiular error, or it may fix something. 
If you want to try that and it does repair things so that Windows boots we can always re-install grub later from the Ubuntu live cd.

---

### Post by idoitprone on 2011-06-17
This is quick and dirty way to diagnosis if either os-prober has failed or you may have to conjure some windows rescue utils. If this workes then reinstall os-prober and undo these changes

#NOTE: Grub 2 use scripts, not menu.lst as in grub legacy

Go to 40-customs at /etc/grub.d
 add the entry to the bottom

```
menuentry "vista" {
set root=(hd0,2)
chainloader +1
}
```

dont forget to add executable permissions
```
sudo chmod u+x 40_custom
```
then
```
sudo update-grub
```

From the look of it this probably will fail, but there may be interesting errors. It may help diagnosis but look at me i am an idoit trying to tell you to boot from a bootfiles that the bootscript cannot find. So it most likely will fail.

Strange, Ubuntu cannot mount the windows partition, please do tell

---

### Post by citronex on 2011-06-17
wow! hahaha my comp is soo messed-up now.  I tried to see if I could fix the windows side of things by using the repair disc, and now it tells me that my bootManager is missing! so is no longer using ubuntu to pull up the OS menu, which means I can't open ubuntu anymore and needless to say windows!

---

### Post by Quackers on 2011-06-17
Did the automatic startup repair run?

---

### Post by wildmanne39 on 2011-06-17
> **citronex said:**
> wow! hahaha my comp is soo messed-up now.  I tried to see if I could fix the windows side of things by using the repair disc, and now it tells me that my bootManager is missing! so is no longer using ubuntu to pull up the OS menu, which means I can't open ubuntu anymore and needless to say windows!Hi, here is a guide to reinstall the boot manager.
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)
I gave you this guide because I thought it might be best to fix your windows MBR before fixing grub.

---

### Post by oldfred on 2011-06-17
The info in the unknown boot loader can literally be any data. When partitions are move it seems the old data is not erased. The script just prints out unknown boot loader if it finds non-zero data. So The registry data looks like it came from a shrink of the windows partition. Was it moved/shrunk too much or something. 

It seems unusual for all the windows boot files to be missing from the NTFS partition and the script not reporting an error. Sometimes you do not see anything because the script cannot mount the partition to check for files. But it usually reports that.

Can you see windows data in the NTFS partition sda2? Boot files would be these files & folders:
/bootmgr /Boot/BCD   /Windows/System32/winload.exe

Grasping at straws, chkdsk from a windows repair disk. Or testdisk to see if data is there.

---

### Post by Quackers on 2011-06-17
Thanks oldfred :-)

citronex,
if you want to get Ubuntu booting again you can boot from the Ubuntu live cd/usb and select "try Ubuntu".
Then open a terminal and run the following commands one at a time, pressing enter after each line.
```
sudo mount /dev/sda6 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot and Ubuntu should boot up directly.

As for Windows I suspect it may need to be re-installed. Check first in the Places menu whether the Windows partitions can be seen, as oldfred says.

---

