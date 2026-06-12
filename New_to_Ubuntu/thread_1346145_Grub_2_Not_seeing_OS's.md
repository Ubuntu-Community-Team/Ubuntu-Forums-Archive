---
title: "Grub 2 Not seeing OS's"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Musick Man on 2009-12-04
Hi,

I am in the process of Super Booting my computer. I have installed Ubuntu 9.10, Windows 7, and Slackware, and I am planning on installing Elive also. But I have a problem.

I installed Ubuntu 9.10 first. It loaded fine. Then I installed Windows 7 and the GRUB bootloader (the new beta one that comes with Ubuntu 9.10) did not pick up Windows 7. And after a lot of browsing around, I couldnt find a answer on how to add it to grub, so I just re-installed Ubuntu 9.10 and after I re-installed it, GRUB picked up my Windows 7 Install. 

So last night I installed a distro that is based off of slackware called SLAX. And again, SLAX did not show up on my GRUB, so I figured that if re-installing ubuntu 9.10 made windows 7 show up on grub, then it should work for SLAX also. Well it didnt seem to work. So now I am stuck. 

So what my question is, How do you add Operating Systems to the Grub 2 Bootloader so that you can boot them?

Thanks,

Musick Man

---

### Post by bluesscream on 2009-12-04
what says ```
sudo update-grub
```
more info:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

### Post by QIII on 2009-12-04
You may need to install and run os-prober before updating GRUB2.

But have a look at ranch hand's fine work here:

[http://ubuntuforums.org/showthread.php?p=8191211](http://ubuntuforums.org/showthread.php?p=8191211)

---

### Post by Musick Man on 2009-12-04
When I do the grub-update it shows this

[sudo] password for patrick: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
Found Windows Vista (loader) on /dev/sdb1
done

---

### Post by Musick Man on 2009-12-04
ok. So I have tried ```
sudo update-grub
``` and ```
sudo grub-mkconfig
``` and neither of them pick up my Slackware install.

My slackware is on my partationed hard drive at /dev/sda4. Its a Ext3 file system also. Is there a way that I can manually add it to my grub boot list?

---

### Post by QIII on 2009-12-04
OK.

os-prober did not pick up my OpenSolaris either.

Go back to ranch hand's tutorial.  You will probably need to add an entry to 40_custom.  If he does not talk about how to do it, one of the many links at the bottom of his post surely will.

Here, by way of example, are the custom entries in my /etc/grub.d/40_custom

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Vista" {
        set root=(hd1,1)
        chainloader +1
}

menuentry "OpenSolaris" {
        set root=(hd2,1)
        chainloader +1
}

```

Here's a really good tutorial, which I think ranch hand has included:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Musick Man on 2009-12-04
So I added slackware to my 40_custom file but I got a error message that said "invalid Signature" when I tried to load the OS. 

My 40_custom file looks like this:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Slackware" {
        set root=(hd0,3)
        chainloader +1
}
```

I also thought that I got the partition wrong. So I tried my configuration like this 

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Slackware" {
        set root=(hd0,4)
        chainloader +1
}
```

and that still didnt seem to work. Could it be that I get a Invalid Signature because I have the hd(0,3) set up wrong?

According to Disk Utlitiy it is a Linux Ext3 (Verson 1.0) File System on Partition 4 (Linux (0x83)) on /dev/sda4. The drive is checked as bootable. If any of that information can help

---

### Post by QIII on 2009-12-04
If you can see it in the GRUB2 menu, you may try this.  I found it, but I have NOT confirmed that it will work.  It might be worth your while to wait a while and see if anyone else chimes in to tell you I'm an idiot.

First, remove the entry from your 40_custom.

You probably have done this:
```
sudo apt-get install os-prober
```And this:
```
sudo os-prober
```The recommendation I read said the following.  Remember that if you can't get back in, you can reverse this at the root prompt in recovery mode:

```
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
``````
sudo update-grub
```See if that comes back "clean".   (Maybe we'll get lucky and Slackware will show up without any more ado).

If you get a "clean" update, reboot.

Again, if you can't get in at all, drop to the recovery shell and restore your device.map.

Then let's try making the addition to 40_custom again.

---

### Post by Musick Man on 2009-12-05
I did what you said, and Slackware didnt show up on the bootloader after I did that. But I also got back into my system fine.

So I added the 
```
menuentry "Slackware" {
        set root=(hd0,3)
        chainloader +1
}
```
back into my 40_custom. And its strange, when I do a ```
sudo update-grub
```

It does not show that Slackware was added to the new grub.cfg. Same thing if I run ```
sudo update-grub2
```

But if I run a ```
sudo grub-mkconfig
```

it adds the Slackware boot item. 

Here is the output of ```
sudo update-grub
``` and ```
code sudo update-grub2
``` (its the same output for both)

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
Found Windows Vista (loader) on /dev/sdb1
done

```

Here is the output for ```
sudo grub-mkconfig
```

```
Generating grub.cfg ...
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 1a514a1e-24ca-453b-80ba-1428cf7d31cb
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
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1a514a1e-24ca-453b-80ba-1428cf7d31cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1a514a1e-24ca-453b-80ba-1428cf7d31cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1a514a1e-24ca-453b-80ba-1428cf7d31cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1a514a1e-24ca-453b-80ba-1428cf7d31cb ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows 7 (loader) on /dev/sda3
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 35c0bf6750c1df64
	chainloader +1
}
Found Windows Vista (loader) on /dev/sdb1
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c4609cb3609cae24
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Slackware" {
        set root=(hd0,3)
        chainloader +1
}
### END /etc/grub.d/40_custom ###
done

```

Thanks again for all your help:D

I really appericate it.

---

### Post by QIII on 2009-12-05
I will add that to my arsenal.

Thank YOU!

---

### Post by Musick Man on 2009-12-05
Im sorry, but that last post made it sound like it worked, but it didnt...

I did a little bit of expermenting on my own, and now after adding slack back into the 40_custom, when I load it from GRUB it loads into Windows 7. And I am not sure why either. 

I tried adding insmod ext3 and that was what made it start to boot into Windows 7. And after removing it, it still booted into windows 7. Any more ideas on what could make it work? 

Is installing the old GRUB a option?

---

### Post by oldfred on 2009-12-05
For grub2 the partition numbering is different than grub legacy. if slax is in sda4 you entry should be the one you had first:

menuentry "Slackware" {
        set root=(hd0,4)
        chainloader +1
}

Also to chainboot you have to have a boot loader in the PBR. Windows actually has a boot loader in its PBR and thats why you can chain boot windows.


 How to install Grub from a live Ubuntu cd. 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
see note
If someone wants GRUB on a partition, the 'setup (hd0)' step can be modified to 'setup (hdX,Y)'. Where X is the hard disk, and Y the partition using GRUB's nomenclature of starting from 0 (first partition=0, second=1,...).

If slax uses old grub just follow the instructions for installing grub but put it into (hd0,3) using old grubs numbering.

---

### Post by ranch hand on 2009-12-05
I think that you will have better luck if your 40_custom entry looks like this;
```

echo "Adding OpenSolaris" >&2 
cat << EOF
menuentry "OpenSolaris" {
        set root=(hd2,1)
        chainloader +1
}
EOF

```
Make sure that the drive count starts with 0 and the partition count starts with 1 (grub-legacy starts both with 0).

---

### Post by Musick Man on 2009-12-05
At oldfred:

I tried ```
menuentry "Slackware" {
set root=(hd0,4)
chainloader +1
}
```

and 

```
menuentry "Slackware" {
set root=(hd0,4)
}
```

and both times it went straight into my Windows 7. 

At ranch hand

I tried 

```
echo "Adding Slackware" >&2 
cat << EOF
menuentry "OpenSolaris" {
        set root=(hd0,4)
        chainloader +1
}
EOF
```

and

```
echo "Adding Slackware" >&2 
cat << EOF
menuentry "OpenSolaris" {
        set root=(hd0,3)
        chainloader +1
}
EOF
```

and again both times it went straight into my Windows 7. 

Do you think that if I add 

```
(hd3)	/dev/sda4
```

to my device.map and then add 

```
echo "Adding Slackware" >&2 
cat << EOF
menuentry "OpenSolaris" {
        set root=(hd3,0)
        chainloader +1
}
EOF
```

It would work? Because I am setting /dev/sda4 to my device.map and it is calling partition 1 on /dev/sda4?

(if its a only partition on a drive, its partition 0 right?)

---

### Post by ranch hand on 2009-12-05
(hd3,0) would be calling for your 4th HDD and using a number for the partition, 0, that is not used in grub2.

I think it may have have trouble with this.

How about using this script and posting the results;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Musick Man on 2009-12-05
Here is the contents of RESULTS.txt. 

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000d8eb

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   231,994,664   231,994,602  83 Linux
/dev/sda2         231,994,665   239,995,034     8,000,370   5 Extended
/dev/sda5         231,994,728   239,995,034     8,000,307  82 Linux swap / Solaris
/dev/sda3    *    239,995,035   483,267,329   243,272,295   7 HPFS/NTFS
/dev/sda4    *    483,267,330   726,539,624   243,272,295  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05e705e7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0bac539

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065    78,156,224    78,140,160   f W95 Ext d (LBA)
/dev/sdc5              16,128    78,156,224    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1a514a1e-24ca-453b-80ba-1428cf7d31cb" TYPE="ext4" 
/dev/sda3: UUID="35C0BF6750C1DF64" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda4: LABEL="Slackware" UUID="738f54a8-b515-4551-9c06-68cb311910af" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="3ee98da1-5b89-4331-83f6-2d156500c592" TYPE="swap" 
/dev/sdb1: UUID="C4609CB3609CAE24" TYPE="ntfs" 
/dev/sdc5: UUID="F650454C504514B1" LABEL="New Volume" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/patrick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=patrick)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 1a514a1e-24ca-453b-80ba-1428cf7d31cb
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1a514a1e-24ca-453b-80ba-1428cf7d31cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1a514a1e-24ca-453b-80ba-1428cf7d31cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1a514a1e-24ca-453b-80ba-1428cf7d31cb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1a514a1e-24ca-453b-80ba-1428cf7d31cb ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 35c0bf6750c1df64
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c4609cb3609cae24
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Slackware" {
        set root=(hd0,3)
        chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1a514a1e-24ca-453b-80ba-1428cf7d31cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3ee98da1-5b89-4331-83f6-2d156500c592 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=================== sda4: Location of files loaded by Grub: ===================


 247.4GB: boot/initrd.gz
 247.4GB: boot/vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  02 01 02 01 02 01 02 01  02 01 02 01 02 01 02 01  |................|
*
00000040  0c ff 0c 0c 0b 0b 0b 0b  0a 0a 0a 0a 0a 0a 0a 0a  |................|
00000050  09 09 09 09 09 09 09 09  09 09 09 09 09 09 09 09  |................|
00000060  08 08 08 08 08 08 08 08  08 08 08 08 08 08 08 08  |................|
*
00000080  07 07 07 07 07 07 07 07  07 07 07 07 07 07 07 07  |................|
*
000000c0  06 06 06 06 06 06 06 06  06 06 06 06 06 06 06 06  |................|
*
00000140  05 05 05 05 05 05 05 05  05 05 05 05 05 05 05 05  |................|
*
000001b0  05 05 05 05 05 05 05 05  05 05 05 05 05 05 00 01  |................|
000001c0  01 01 07 fe ff ff 3f 00  00 00 c1 52 a8 04 00 00  |......?....R....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

And Here is what I the terminal output was if it is any help. 

```
[sudo] password for patrick: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sdb1 for information... 
Searching sdc1 for information... 
Searching sdc5 for information... 
Finished. The results are in the file RESULTS.txt located in /home/patrick/Downloads

```

I just added a attachment of the drive information from the Disk Utility.

---

### Post by ranch hand on 2009-12-05
Well the first thing that struck me is that you have grub 0.97 on the MBR of sda.  On the other hand we are working with grub 1.97beta4 (I think) in your Ubuntu.

How about posting the results of;
```

grub-install -v

```
run from in your Ubuntu installation.

If, as it appears, it is grub1.97beta4, follow these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the file editing instructions as that is not needed.  We need grub2 recognized as being in your MBR.

Rerun the boot info script.  No need to post the whole thing but the very first entry would be nice.

---

### Post by oldfred on 2009-12-05
The script shows grub1.97. It can be somewhat confusing as it will show either grub0.97 or grub1.97. Both versions are currently at .97 so it easy to miss read.

I see two boot flags which I thought was impossible? Windows needs it to boot but grub can use makeactive to set it. Does slax need it also? The boot script also does not show slax? It is usually pretty good at seeing other boot loaders, so is slax missing something, it does not look complete?

---

### Post by Musick Man on 2009-12-05
Results.txt (only first part)

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
```

I only did the part that said To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda and not off a live CD (The code was sudo grub-install /dev/sda and it returned with no errors reported.). Is that a problem? or should I go back and do everything like it says off a Live CD?

---

### Post by Musick Man on 2009-12-05
Oldfred: To Install SLAX I followed these instructions on the internet: 

[http://gr8idea.info/os/tutorials/slax/install.html](http://gr8idea.info/os/tutorials/slax/install.html)

Could it be bad instructions? 

Also, when I open up the partition that it is installed on, I see 3 folders. A Boot folder, a Lost+Found folder and a slax folder.

I attached the contents of the Boot folder and the Slax Folder. The Lost+found folder didnt let me access the contents.

---

### Post by ranch hand on 2009-12-05
I think that I would WITHOUT REBOOTING until sure things were right, remove everything related to grub in synaptic.

You must have an upgrade to 9.10 and there is some residue from grub-legacy that is screwing things up.  If you have a custom file just copy it to some place safe like your desktop so you can just put it back.

Then just install grub-common and grub-pc.  When done, even though this was run when you installed, run both update-grub and grub-install /dev/sda.

---

### Post by Musick Man on 2009-12-05
I removed everything GRUB releated. Then installed grub-common and grub-pc. 

when I ran sudo update-grub I got a something new. 

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
**ls: cannot access /media/New: No such file or directory**
Found Windows 7 (loader) on /dev/sda3
Found Windows Vista (loader) on /dev/sdb1
done
```

It did not show that SLAX was added when I ran sudo update-grub, but when I run grub-mkconfig it shows that SLAX was added.

EDIT:

I just ran sudo bash /home/patrick/Downloads/boot_info_script038.sh and got some different starting results.

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
```

---

### Post by ranch hand on 2009-12-05
Well, I just don't know.  What is the deal with this grub .97 business?

Does everything on your menu work?

As far as Slax goes I have only run it as a live CD and really have no idea what the right entry would be.

I assume, though, that it is on sda4.  That means that the drive/partition definition should be "(hd0,4)".

I am sure that you need to chainload it.

---

### Post by Musick Man on 2009-12-05
Yes, Everything else on my menu works. 

I have the hard drive setup as hd(0,4)

```
echo "Adding SLAX" >&2 
cat << EOF
menuentry "SLAX" {
        set root=(hd0,4)
        chainloader +1
}
EOF
```

I will try booting it again and see what happens.

---

### Post by ranch hand on 2009-12-05
That does not work I take it?

---

### Post by Musick Man on 2009-12-05
```
echo "Adding SLAX" >&2 
cat << EOF
menuentry "SLAX" {
        set root=(hd0,4)
        chainloader +1
}
EOF
```

does not work. When I select it and press enter it says error: Invalid Signature Press any key to continue.

---

### Post by ranch hand on 2009-12-05
You need to check the 2nd and 3rd links in the link in my sig.  drs305 has done a great job and a lot of folks have posted how to boot to all sorts of OS'.  Search the threads for Slax.

---

### Post by oldfred on 2009-12-05
To chainboot you have to have grub or some boot loader in the PBR of the slax partition. The script will set it if it is there although it sometimes does not correctly identify all PBR data.

The script only shows slax as the label of that partition. What is really in that partition?

---

### Post by Musick Man on 2009-12-05
Well after looking at your posts, and doing some re-search, I have come to the conclusion that SLAX was made to only be a Live CD and was never intended to be used on the desktop. 

Thanks for all your help everyone that had some input. I am glad to know that there is a very smart group of people that is always eager to help. 

-Musick Man

---

