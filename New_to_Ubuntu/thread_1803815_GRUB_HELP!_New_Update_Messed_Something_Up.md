---
title: "GRUB HELP! New Update Messed Something Up"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by UserDemos on 2011-07-13
Hey all,

I've dealt with this before, but can't get my previous solutions to work. I'll let the screenshot speak for me. 

Can anyone help a relative newbie before who is now stuck? Thanks in advance!

---

### Post by wildmanne39 on 2011-07-13
> **UserDemos said:**
> Hey all,

I've dealt with this before, but can't get my previous solutions to work. I'll let the screenshot speak for me. 

Can anyone help a relative newbie before who is now stuck? Thanks in advance!
Hi, I do not know if I can figure it out but you will need to post this information to be able to get help with it. 

Post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by UserDemos on 2011-07-14
Hey there,

Here are the results.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.........$....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1418570 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   484,204,543   484,202,496  83 Linux
/dev/sda2         484,206,590   488,396,799     4,190,210   5 Extended
/dev/sda5         484,206,592   488,396,799     4,190,208  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697152 bytes
4 heads, 32 sectors/track, 61823 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,913,470     7,913,439   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       b7fac5d3-81d6-405e-9773-ccc804b77cd7   ext3       
/dev/sda1        d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c   ext4       
/dev/sda5        8e096629-6ca7-4571-bcf6-83debb963fe6   swap       
/dev/sdb1        78BE-0340                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d13ff7e2-aa8f-45c2-8b49-1e4b4701ca7c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8e096629-6ca7-4571-bcf6-83debb963fe6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  80.135009766 = 86.044311552   boot/grub/core.img                             1
 220.251548767 = 236.493299712  boot/grub/grub.cfg                             1
 181.637474060 = 195.031752704  boot/initrd.img-2.6.38-10-generic              2
   1.907226562 = 2.047868928    boot/initrd.img-2.6.38-8-generic               2
 181.149723053 = 194.508034048  boot/vmlinuz-2.6.38-10-generic                 2
  80.133281708 = 86.042456064   boot/vmlinuz-2.6.38-8-generic                  1
 181.637474060 = 195.031752704  initrd.img                                     2
   1.907226562 = 2.047868928    initrd.img.old                                 2
 181.149723053 = 194.508034048  vmlinuz                                        2
  80.133281708 = 86.042456064   vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

I hope this can help someone solve my dilemma. Thanks for everyone's help in advance again!

---

### Post by wildmanne39 on 2011-07-14
Hi, did this problem start after you installed updates yesterday? Hold down the **** key while booting and you should get the grub menu select the this kernel 2.6.38-8-generic and see if you can boot.

---

### Post by UserDemos on 2011-07-14
Yes, it started yesterday after I did the reboot for the updates.

Holding the shift key sends me to the same screen. Am I doing something wrong?

Again, thanks for the help!

---

### Post by wildmanne39 on 2011-07-14
Hi, It looks like your mount point for your drive is missing, I am going to research this and see if I can find an answer.

---

### Post by wildmanne39 on 2011-07-14
Here are some links on mounting partitions, you need to make your mount auto at startup.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by drs305 on 2011-07-14
The screenshot you posted indicates that Grub may be having problems with your menu.

From the Grub menu, try this:
```
configfile (hd0,1)/boot/grub/grub.cfg
```

If that doesn't work, confirm Grub 2 can see the kernel and menu:
```
ls (hd0,1)/boot/grub/grub.cfg  # Should see grub.cfg
ls (hd0,1)/boot  # Should see the kernels and initrd images
ls (hd0,1)/ # Should see 'vmlinuz' and 'initrd.img'

```

If the 'ls' commands work:
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod normal
normal
```

If that fails:
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

If any of these work and your system boots, run:
```
sudo grub-install /dev/sda
sudo update-grub

```

---

### Post by UserDemos on 2011-07-15
drs305: here's what happened.

the first code you posted: I didn't seem to get anywhere with.

the second code I posted a screenshot for: it tells me that there's no drive to mount (or something similar) after I exit.

I tried the third one just to make sure I covered all of my options: and there's a screenshot for that one too. 

I could not get into my GUI to or get anything to boot. 

Once again, all of this help is greatly appreciated. I can't believe I've gotten so stuck. Thanks and thanks and thanks!

---

### Post by drs305 on 2011-07-15
There is a relatively new app which repairs some boot problems. I think it would be good to try to use it. Here is a link that displays the commands to run:
[http://ubuntuforums.org/showpost.php?p=11045408&postcount=426]("http://ubuntuforums.org/showpost.php?p=11045408&postcount=426")
There is a link at the bottom of the post if you need more information.

If that doesn't work, you can try to purge and reinstall Grub 2 via the following guide. If you have questions about it, you can post here.
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by UserDemos on 2011-07-15
None of those worked. They all send me to square 1 EXCEPT the boot-program which enabled this screen and then sent me to choose a kernel. I had to revert to an old one, but at least my computer works. I have to manually revert to the old kernel, but at least I can get in and use it. 

I'm starting to think the problem isn't with GRUB, but the kernel update. Something must be corrupt and I'm not sure what to do. Check out the screen. 

Thoughts? And again, thanks for the help everyone.

---

### Post by drs305 on 2011-07-15
Do you now get the normal Grub 2 menu and boot off that, or do you still have to boot via the repair app?

If you can boot off the Grub menu to the older kernel, I'd try to repair the newer initrd image file. If that doesn't work, I'd remove the latest kernel with Ubuntu Tweak and then reinstall it.

To repair the bad kernel:
```
sudo update-initramfs -u -k <kernel version>
sudo update-grub # If it doesn't run automatically after the first command finishes
```
Example: sudo update-initramfs -u -k 2.6.38-8-generic

If that doesn't work, you can learn about removing kernels from this link. I'd recommend using the Ubuntu Tweak option.
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by ybmatters on 2011-07-17
I've just performed the latest updates on a Dell Inspiron 2200 and ended up in the same situation as the OP. I've followed the instructions in here and cannot get anything to work. Invariably I end up at the "cannot read the Linux header" error. I don't think this problem is with grub, I think the kernel is borfed.

I'm downloading an 11.04 ISO now and will reinstall from there <sigh>.

---

### Post by ybmatters on 2011-07-17
Gawd what a bleeding mess! Attempts to install from the ISO just hang. Needed a Windows disk to remove all partitions. Then 11.04 boots to a known error with Ubiquity and only then does the the install seem to be working.

While ever this sort of problem with installs and updates continue (and no this is not my first problem with updates causing hangs and grub errors and the like), Ubuntu has no hope of challenging MS :(

I want to trust Ubuntu to be more than my FTP and WAMP server, but I can't. Last version I felt really safe with was my first 9.04 :frown:

And now I get the "error: out of disk." and "grub rescue>" aarrrgghh!

---

### Post by drs305 on 2011-07-17
> **ybmatters said:**
> And now I get the "error: out of disk." and "grub rescue>" aarrrgghh!

There was a problem with Lucid's Grub which produced an 'out of disk' error but that has long since been fixed. 

Now the 'out of disk' error combined with the 'rescue' prompt sometimes indicates that the BIOS can't see far enough into the disk to find the boot files referenced by the MBR. You can check in the BIOS to confirm it reports the proper disk size, or from the grub prompt try "ls (hdX,Y)/boot/grub/" to see if BIOS/Grub can see the Grub files (X,Y being the drive/partition).

---

### Post by ybmatters on 2011-07-23
Sorry drs305 for not responding. The email notification of a response did not come through.

I did try your suggested command and yes I could see the disk. In fact I'd followed all of the checks/suggestions/recommendations in this thread. In the end I gave up. I'd had 11.04 running well, allowed the the latest update which left me with the "linux headers" message and it failed even when I tried to boot from the previous revision in Grub. 

I tried to reinstall a freshly downloaded copy of 11.04 to end up at the "out of disk" error as per the edit to my last message.

I simply gave up, used Windows to re-delete the partitions and installed from my CD copy of 10.04.

So thanks for the attempt to help but I'll just stick at 10.04 where I know I'm safe :???:

---

### Post by httpstatus418 on 2011-08-25
Hi!

According to the descriptions it's most likely that this is related to the problem I have/had. Updating 10.04 to new kernels or newer versions left me with several annoying problems that resulted in many hours of fiddling around. But long story short:

the source of my problem is an old laptop, a 320GB hard-disk, and a bios that does lack the 48bit LBA algorithm. That means, the bios recognizes only the first 137GB of a hard-disk, and so does grub. You can check the entry in your bios. As long as the contents of ' /boot' are within the limit, everythings fine. And that's the only solution I found - keep the boot folder within the 137GB limit by creating a separate partition.

At least it solved my problems :)

---

