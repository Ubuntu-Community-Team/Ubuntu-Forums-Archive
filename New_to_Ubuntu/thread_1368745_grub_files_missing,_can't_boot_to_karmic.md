---
title: "grub files missing, can't boot to karmic"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by charlier653 on 2009-12-31
Installed winXP pro, then did an install of karmic.

I have no grub os choice screen, and windows boots normal.

Have live cd in computer, terminal open, typed:

```
sudo grub
```

got error message:
```

sudo: grub: command not found
```

Then I tried:

```
find /boot/grub/stage1
```

even though I wasn't in the grub prompt, just to see what would come up. This is the result:

```
find '/boot/grub/stage1' no such file of directory.
```

BIOS is set to boot from hd0,0 where windows resides.
Karmic / is on hd1,0, with /home on a different drive.

So I tried:

```
find /boot/grub/menu.lst
```

and no surprise, got this:

```
find '/boot/grub/menu.lst' no such file or directory.
```

Since this is a new install from the .iso I downloaded today for Karmic, It should be grub2, right?

How do I fix this? I like my Ubuntu!
What other surprises are in store for me, an not quite absolute beginner at this. Have tried various distros starting with 6.06 over the last several years. Love the concept behind Ubuntu, and am really liking what I see in 9.10.

The only reason I want a dual boot is for certain games that won't run under wine or from a vbox.

Any ideas on how to get this working?

---

### Post by lindsay7 on 2009-12-31
Type sudo fdisk -l  in the terminal and post the results here.  That is a small letter L by the way.

---

### Post by charlier653 on 2009-12-31
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5e3afe2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20945   168240681    7  HPFS/NTFS
/dev/sda2           20946       30515    76871025    5  Extended
/dev/sda5           20946       30515    76870993+  83  Linux

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17241723

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2481    19928601    7  HPFS/NTFS

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d720d72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        5596    44949838+   7  HPFS/NTFS
/dev/sdc2            5597       12161    52733362+   5  Extended
/dev/sdc5            5597       12161    52733331   83  Linux

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1994    16016773+  83  Linux
/dev/sdd2            1995        2482     3919860    5  Extended
/dev/sdd5            1995        2482     3919828+  82  Linux swap / Solaris

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d823598

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            4438        7297    22972950    5  Extended
/dev/sde2   *           1        4437    35640171    7  HPFS/NTFS
/dev/sde5            4438        7297    22972918+  83  Linux



Hmmm.....bios POST reports the IDE drives first, then the SATA drive. Here it looks like the sata drive tops the list.

This is the order that the bios POST shows:

ch0 M 20gb  (windows disk)
ch0 s 100gb
ch1 m 20gb  (linux root)
ch1 s 60gb 
ch2 m 251gb sata
ch3 m atapi dvd-rom

---

### Post by charlier653 on 2009-12-31
Ok, found grub.

It's on the sata drive. Takes about 15-20 seconds to load the OS menu.

Will boot to windows from there, but I get a range of error messages when I try to boot to Ubuntu.

This is what I get with [press e to edit]

```
recordfail=1
if  [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd3,1)
search --no-floppy --fs-uuid --set 6540546e-daa5-4ba9-9a7d-35a4c2b92fd9
linux /boot/vmlinuz-2.6.31-14-generic root=uuid=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
```

It appears that I have sh:grub> available to me. Now what to use that for?  I have to admit, using the grub command line scares me a lot!

typed find /boot/grub/menu.lst at that prompt, and got error: unknown command `find'

---

### Post by kansasnoob on 2009-12-31
It looks like you have grub2, if so the old "sudo grub" etc doesn't work anymore. To get a better look at exactly what you have here please post the results of the Boot Info Script using the Live CD as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by charlier653 on 2009-12-31
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe5e3afe2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   336,481,424   336,481,362   7 HPFS/NTFS
/dev/sda2         336,481,425   490,223,474   153,742,050   5 Extended
/dev/sda5         336,481,488   490,223,474   153,741,987  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17241723

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,857,264    39,857,202   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d720d72

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    89,899,739    89,899,677   7 HPFS/NTFS
/dev/sdc2          89,899,740   195,366,464   105,466,725   5 Extended
/dev/sdc5          89,899,803   195,366,464   105,466,662  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    32,033,609    32,033,547  83 Linux
/dev/sdd2          32,033,610    39,873,329     7,839,720   5 Extended
/dev/sdd5          32,033,673    39,873,329     7,839,657  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d823598

Partition  Boot         Start           End          Size  Id System

/dev/sde1          71,280,405   117,226,304    45,945,900   5 Extended
/dev/sde5          71,280,468   117,226,304    45,945,837  83 Linux
/dev/sde2    *             63    71,280,404    71,280,342   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="CF3FD30D6F47D660" LABEL="SATA" TYPE="ntfs" 
sda5: UUID="d28e35f5-2ffa-43f7-aa81-545c1067682d" SEC_TYPE="ext2" TYPE="ext3" 
sdb1: UUID="3AA8D626A8D5E105" TYPE="ntfs" 
sdc1: UUID="52A8CD63A8CD45E7" LABEL="apps" TYPE="ntfs" 
sdc5: UUID="8668c694-5412-4c6a-b59c-d8fe68c2bb24" SEC_TYPE="ext2" TYPE="ext3" 
sdd1: UUID="6540546e-daa5-4ba9-9a7d-35a4c2b92fd9" SEC_TYPE="ext2" TYPE="ext3" 
sdd5: UUID="174fbcb5-0af9-4f88-bb9d-cf8d10d9cdab" TYPE="swap" 
sde5: UUID="42a3cf5e-5c35-4b78-9b1b-83a86dc2f4e1" SEC_TYPE="ext2" TYPE="ext3" 
sde2: UUID="66EB87CD4ACA3821" LABEL="save" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root=(hd3,1)
search --no-floppy --fs-uuid --set 6540546e-daa5-4ba9-9a7d-35a4c2b92fd9
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
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 6540546e-daa5-4ba9-9a7d-35a4c2b92fd9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 6540546e-daa5-4ba9-9a7d-35a4c2b92fd9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3aa8d626a8d5e105
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d28e35f5-2ffa-43f7-aa81-545c1067682d /home           ext3    defaults        0       2
# /home2 was on /dev/sdc5 during installation
UUID=8668c694-5412-4c6a-b59c-d8fe68c2bb24 /home2          ext3    defaults        0       2
# /home3 was on /dev/sde5 during installation
UUID=42a3cf5e-5c35-4b78-9b1b-83a86dc2f4e1 /home3          ext3    defaults        0       2
# swap was on /dev/sdd5 during installation
UUID=174fbcb5-0af9-4f88-bb9d-cf8d10d9cdab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

```


the reason it is showing all those windows in all drives is these are used drives I have collected over the years. I don't know how to remove the mbr notations on those drives without an active windows install.

---

### Post by kansasnoob on 2009-12-31
**[COLOR="Red"]This is complicated so read this all, and also be aware that I'll be out most of the day and unavailable to help if you run into trouble, so proceed at your own risk![/COLOR]**

Well, this is going to require a bit of guess work on my part. What I can see from that is we have 5 hard drives & four of them have a Win MBR:

> => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

Win XP is actually installed on sdb1:

> sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


And Karmic is on sdd1:

> sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


And we know that grub2 is installed to sda.

Now this is where the guess work comes in! I can't be certain which of those four drives with a win mbr the system BIOS is relying on to boot, well actually since grub is installed on sda we can rule that out, and since windows still boots straight away we can probably rule out sdd.

Basically you need to do one of two things, either change the BIOS so it's looking to the proper drive to boot Karmic and make sure grub is also installed to that drives mbr, or leave the BIOS alone and try just installing grub to the proper drives mbr.

**I want you to fully understand though that once we replace the win mbr with grub you will not be able to boot Windows again until we get grub working or you'd have to recover the win mbr (there are several ways to do that).**

The method for installing grub to the proper drive is explained here:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

In your case, since karmic is on sdd1 you'd:

```
sudo mount /dev/sdd1 /mnt && sudo mount –bind /dev /mnt/dev && sudo mount –bind /proc /mnt/proc
```

I just can't be sure where to install grub:confused:

Could be any of these:

grub-install /dev/sdb (most likely guess IMO)
grub-install /dev/sdc
grub-install /dev/sdd (I doubt this)
grub-install /dev/sde 

**But I've also found that sometimes grub2 doesn't play well with multiple drives, other times it's just fine, but you could find yourself in a situation where you'd need to mount and chroot Karmic and revert to legacy grub!**

I wrote a bit here about how to mount and chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And here about how to revert grub (or vice versa):

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

**And, as I said, you should have a plan in place to recover the win mbr if needed!**

I personally prefer this method using the Ubuntu Live CD:

[http://ubuntuforums.org/showpost.php?p=8538352&postcount=173](http://ubuntuforums.org/showpost.php?p=8538352&postcount=173)

Best of luck, I think you'll need it :)

---

### Post by charlier653 on 2009-12-31
Thank you. I appreciate the help!

Bios is set to sda. that is how I found where grub was hiding, by changing the bios until it popped up.

I will proceed with extreme caution experimenting around with grub2, and if i can't get it to work before frustration sets in, I'll then go ahead and revert to grub. Either way, I'll have my Ubuntu!

Am curious about something, I had a look in the grub.d folder. Are those files written in c or some derivative of it (c+, c#, etc.)??

Again, thanks for your help!

---

### Post by lindsay7 on 2009-12-31
You can try this and see if it resets the grub.


 Type in the terminal

"sudo update-grub" without the quotation marks

---

### Post by charlier653 on 2009-12-31
Tried that, got error "cannot find /"

am reinstalling, and using advanced for setting where the boot files go.

have set a /boot partition on the same drive as /, will see if that makes a difference.


result: no joy.  now gives me "grub rescue" prompt.

will try again later, putting grub on winXP partition.

---

### Post by charlier653 on 2009-12-31
I found [this]("https://help.ubuntu.com/community/Grub2")and am finding that only two or three commands in the list under rescue are working. Did I do something to cause this or is there a problem with my grub2?

Have tried to follow the steps in that help file, but am continually getting "unknown command" on things that are supposed to work.

I did a reinstall of Ubuntu, and set grub to the same disk as my Ubuntu. All I get now is a broken grub rescue.

Will keep playing with it, maybe my experience will help the next person?

---

### Post by drs305 on 2009-12-31
> **charlier653 said:**
> I found [this]("https://help.ubuntu.com/community/Grub2")and am finding that only two or three commands in the list under rescue are working. Did I do something to cause this or is there a problem with my grub2?

Have tried to follow the steps in that help file, but am continually getting "unknown command" on things that are supposed to work.

I did a reinstall of Ubuntu, and set grub to the same disk as my Ubuntu. All I get now is a broken grub rescue.

Will keep playing with it, maybe my experience will help the next person?

From the rescue prompt (following the guide), if you run "ls" it should return the known partitions.

For this example, I'll assume your boot files are on sda5 **but use whichever partition you think your grub files are on**. Remember G2 considers sda5 as (hd0,5).

 If you run "ls (hd0,5)/boot" do you see a *vmlinu[COLOR="DarkRed"]z[/COLOR]...* and *initrd.img...* file?

If you run "ls (hd0,5)/boot/grub" do you see a *grub.cfg* file?

If you still get errors, have you run the "set prefix=(hd0,5)/boot/grub"

You might also try to load the modules manually, with "insmod (hd0,5)/boot/grub/xxxxx.mod"
Try loading "linux.mod", "normal.mod" and "help.mod"

---

### Post by charlier653 on 2009-12-31
The grub.cfg file is in (hd3,1), got that from ```
ls (hd3,1)/boot/grub
```

The initrd and linuz  (note the z instead of x) are in the /boot where they belong.


Am currently working that help file.....and I finally realised that the writer of it took WAAAAY too many shortcuts, not spelling out the fact  that you have to type in all the info. As in he says initrd /initrd.img.....leaving out the fact that you still have to tell grub every little nuance of what you are looking for.

---

### Post by Ubu2010 on 2009-12-31
Just a little FYI, I personally have used EasyBCD to handle dual-booting Ubuntu and Windows (7, specifically). EasyBCD works really well for handling Grub and NTLDR, making them play nicely as it were. Oh, and it's free :D

---

### Post by charlier653 on 2009-12-31
Ok, it's finally doing something. what next? Will I have to go through that every time I boot?


BTW, I'm trying to do this using the kvm switch between my server and my personal box.

nerve wracking, at best.

as to my siggy, i'll have to change that......the games I like don't like vbox or wine

---

### Post by Ubu2010 on 2009-12-31
charlier653, see my above post if you want to try that, that is.

---

### Post by charlier653 on 2009-12-31
I think i will look into it, thanks!

---

### Post by Ubu2010 on 2009-12-31
You are welcome. It is so easy to use.

---

### Post by charlier653 on 2009-12-31
i think i might have it.

posting this from karmic now,

charlie@charlie-desktop:~$ sudo update-grub
[sudo] password for charlie: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done
charlie@charlie-desktop:~$


am going to try a reboot......




no go....back where I started from....grub rescue.

---

### Post by Ubu2010 on 2009-12-31
Save yourself all the added effort and try EasyBCD, I'm not kidding, it makes dual-booting easy. ;)

---

### Post by garyed on 2009-12-31
My guess is Grub is having a hard time finding the order of your drives.
This is a simple fix if it works.

Boot from the 9.10 live CD, open a terminal & do:

```

sudo mount /dev/sdd1 /mnt

```
then:```

sudo grub-install --root-directory=/mnt/ /dev/sda 
```

then reboot, take out the CD & hopefully you'll get a grub menu to get you back into Ubuntu. Once there get to a terminal & do:
[code]sudo update-grub[code]

I'm assuming sda is the drive your bios is set to boot from.
If that doesn't work you could try to substitute sdb for sda

---

### Post by charlier653 on 2009-12-31
Somebody slap me!!!!


Good catch on the bios boot order.

Now have the grub OS list.

Boots into windows just fine from grub. However, when I try to boot into linux, I get "invalid environment block  press any key to continue"

---

### Post by charlier653 on 2009-12-31
How about this?


```
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
setroot=(hd3,1)
search --no-floppy fs-uuid --set 6540546e-daa5-4ba9a7d-35a4c2b92fd9
linux /boot/vmlinuz-2.6.31-14-generic root=uuid=6540546e-daa5-4ba9a7d-35a4c2b92fd9_ro  quietsplash
initrd /boot/initrd.img-2.6.31-14-generic
```





Have edited to the proper uuid, was (i assume) set for the sata disk.but have a question about the insmod ext2.

I had all my linux partitions formatted in ext3, would that make an environment issue?




edit:

googled the environment problem, found [this]("http://ubuntuforums.org/showthread.php?t=1285098"). might do the trick.
will keep you posted

---

### Post by drs305 on 2009-12-31
"insmod ext2" is the correct verbiage. It applies equally to ext2, ext3,ext4.

Sorry the shortcuts weren't clearer. You referred in the preceeding post to the Grub 2 document. I was merely recapping how the guide spelled it out in detail.

---

### Post by charlier653 on 2009-12-31
Thank you. I now have the ability to boot into Karmic, with one small problem remaining. I have to edit out the env line and then crtl+x, then the system boots. I'll see if I can find the file where that comes from and edit it out more permanently.

Thanks for all the help!

@ubu2010: Am looking into EasyBCD. will probably use it.
Thanks!

---

### Post by drs305 on 2010-01-01
> **charlier653 said:**
> Thank you. I now have the ability to boot into Karmic, with one small problem remaining. I have to edit out the env line and then crtl+x, then the system boots. 

Regarding the "env line": Are you referring to entries such as "apci=off", "vga=792", etc?

If so, take a look at /etc/default/grub on the "GRUB_CMDLINE_LINUX_DEFAULT=" or "GRUB_CMDLINE_LINUX_DEFAULT=" to see if they contain the entries you need to modify.

If they aren't contained in /etc/default/grub, tell us specifically what you are editing out and we can probably give you the script from which the entry originates.

---

### Post by charlier653 on 2010-01-02
I was referring to: <if [ -n ${have_grubenv} ]; then save_env recordfail; fi> in the edit window on boot failure.

Haven't gone looking for the offending culprit yet, and am kinda afraid to do much at this point. My Ubuntu works now, with only that one small problem on boot-up. 

this is what my /boot/grub/grubenv looks like right now:

```
# GR#  Environmeon Block
rck
rdfail=0
l=########################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
```

I don't know what it is supposed to look like, all I know is that I get an error message about "invalid environment block" right after grub starts loading and just before the OS choice screen loads. If i try to boot to ubuntu, it will refuse to boot unless I delete that line in the edit window.

Any idea what is supposed to be in that /boot/grub/grubenv file?

A stab in the dark: Would it be the "loadenv.mod" file causing the problems?

---

### Post by drs305 on 2010-01-02
> **charlier653 said:**
> 
Any idea what is supposed to be in that /boot/grub/grubenv file?

You can generate a new /boot/grub/grubenv file, which will effectively "reset" it to the default with the following command. It shouldn't cause any problem and if an error still exists might revert to what you currently have.

Note: Do not try to edit this file. **The file is filled with [COLOR="DarkRed"]#[/COLOR] to make the file exactly 1024 bits. Do not edit the file.**

The command to create a new file is:
```

sudo grub-editenv /boot/grub/grubenv create # create

```

and will look like:
> 
# GRUB Environment Block
####.....


If you have a saved default, the file would look something like:
> 
# GRUB Environment Block
saved_entry=1
#####.....


If you want to see what it would look like with a saved default, run this (then create a new one to reset):
```

sudo grub-set-default 0

```

---

### Post by charlier653 on 2010-01-02
Ok, did the create grubenv, no change.

Since the error is <error: invalid environment block> what sets the environment? I get the idea that [COLOR="DeepSkyBlue"]/boot/grub/grub[/COLOR] or [COLOR="DeepSkyBlue"]/grubenv[/COLOR] are just checks to ensure that there is an environment to boot into. Both files look similar, with the exception of "[COLOR="DarkOrange"]environmeon[/COLOR]" and "[COLOR="DarkOrange"]environment[/COLOR]". Don't understand why the difference, or if there should be any.

I am not skilled in reading files written in c (or it's variants), as these appear to be, referring to the code needed to create the grub.cfg.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by [COLOR="Red"]/usr/sbin/grub-mkconfig[/COLOR] using templates
# from [COLOR="Red"]/etc/grub.d[/COLOR] and settings from [COLOR="Red"]/etc/default/grub[/COLOR]
#

```

Does anyone have a hint as to where the environment generation starts?

---

### Post by charlier653 on 2010-01-03
How do I remove the extra grub from sda1?

```
============================= Boot Info Summary: ==============================

 => [COLOR="Red"]Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6540546e-daa5-4ba9-9a7d-35a4c2b92fd9)/boot/grub.[/COLOR][COLOR="Blue"](I think I need to remove this 
one, as it points to the wrong drive.)[/COLOR]
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 1.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe5e3afe2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   336,481,424   336,481,362   7 HPFS/NTFS
/dev/sda2         336,481,425   490,223,474   153,742,050   5 Extended
/dev/sda5         336,481,488   490,223,474   153,741,987  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17241723

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,857,264    39,857,202   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d720d72

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    89,899,739    89,899,677   7 HPFS/NTFS
/dev/sdc2          89,899,740   195,366,464   105,466,725   5 Extended
/dev/sdc5          89,899,803   195,366,464   105,466,662  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    33,206,354    33,206,292  83 Linux
/dev/sdd2          33,206,355    39,873,329     6,666,975   5 Extended
/dev/sdd5          33,206,418    39,873,329     6,666,912  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d823598

Partition  Boot         Start           End          Size  Id System

/dev/sde1          71,280,405   117,226,304    45,945,900   5 Extended
/dev/sde5          71,280,468   117,226,304    45,945,837  83 Linux
/dev/sde2    *             63    71,280,404    71,280,342   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="CF3FD30D6F47D660" LABEL="SATA" TYPE="ntfs" 
sda5: UUID="d28e35f5-2ffa-43f7-aa81-545c1067682d" TYPE="ext3" 
sdb1: UUID="3AA8D626A8D5E105" TYPE="ntfs" 
sdc1: UUID="52A8CD63A8CD45E7" LABEL="apps" TYPE="ntfs" 
sdc5: UUID="8668c694-5412-4c6a-b59c-d8fe68c2bb24" TYPE="ext3" 
sdd1: LABEL="Ubuntu root" UUID="9944bb87-b0d4-41bc-a6c7-fb865f701661" TYPE="ext3" 
sdd5: UUID="36b55fff-e60c-490d-a404-73cac062b705" TYPE="swap" 
sde5: UUID="42a3cf5e-5c35-4b78-9b1b-83a86dc2f4e1" TYPE="ext3" 
sde2: UUID="66EB87CD4ACA3821" LABEL="save" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,errors=remount-ro)
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
/dev/sdc5 on /home2 type ext3 (rw)
/dev/sde5 on /home3 type ext3 (rw)
/dev/sda5 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/charlie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=charlie)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root=(hd3,1)
search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
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
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 9944bb87-b0d4-41bc-a6c7-fb865f701661
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3aa8d626a8d5e105
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=9944bb87-b0d4-41bc-a6c7-fb865f701661 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d28e35f5-2ffa-43f7-aa81-545c1067682d /home           ext3    defaults        0       2
# /home2 was on /dev/sdc5 during installation
UUID=8668c694-5412-4c6a-b59c-d8fe68c2bb24 /home2          ext3    defaults        0       2
# /home3 was on /dev/sde5 during installation
UUID=42a3cf5e-5c35-4b78-9b1b-83a86dc2f4e1 /home3          ext3    defaults        0       2
# swap was on /dev/sdd5 during installation
UUID=36b55fff-e60c-490d-a404-73cac062b705 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

I think this is where I'm getting the "invalid environment block" error, so it might cure my boot problems to delete the extra grub.

---

### Post by drs305 on 2010-01-03
run the following:
```

sudo dpkg-reconfigure grub-pc

```

The first line you are asked to enter something in is normally blank. The second is where you would put "quiet splash ". TAB to the "OK" in each case.

The third entry is what you really want. It will ask where to put grub and it will probably have at least two devices with asterisks. *Use the space bar to select/delselect the devices you want, and then make sure to TAB to the OK before pressing enter*.

When finished, run
```

sudo grub-install /dev/sdX

```
where you want to keep grub 2.

---

### Post by charlier653 on 2010-01-03
Unfortunately, that didn't work. still have the env block error.

Should I have done ```
sudo update-grub
``` after the first step or after the second?

Ran the boot info script again, still has that extra grub on sda.

Thanks for trying, though.

---

### Post by charlier653 on 2010-01-03
Earlier in this thread you said that the /boot/grub/grubenv file is supposed to be exactly 1024 bytes. After searching google for this problem, I checked the file size for both /grubenv & gruvenv. grubenv shows as 1025 bytes, and gruvenv shows as 1024 bytes.

Do I edit and remove 1 of the #?

---

### Post by drs305 on 2010-01-03
No, you didn't need to update-grub. You will notice, if you had changed any settings in /etc/default/grub, that the changes were overwritten during the execution of the commands above. 

I would have expected you to find two devices listed initially, and that deselecting one and leaving only the one you wanted selected/asterisked to remove grub from the second partition.

Just curious: did you ever look to see what was written in /boot/grub/grubenv? And is it's size 1024 bytes?

I spent some time reading this bug report. It may give you some ideas but unfortunately the majority of the posts are from two months ago and a fix was committed in October. Nevertheless, it may provide you with some interesting reading and give you some avenues to explore.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784")

---

### Post by charlier653 on 2010-01-03
Here is the grubenv text (truncated):

```
# GR#  Environmeon Block
rck
rdfail=0
l=####....
```

Was 1025 byte, I edited it, removing 1 # from the end. No change, other than the file size being 1024 bytes now.

---

### Post by kansasnoob on 2010-01-04
Odd, my grubenv just looks like this:

```
# GRUB Environment Block
#######################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
```

I see sdd ended up being the right location for grub, eh? Darn it, that was my last choice :(

The rest of this grub2 stuff is still confusing to me, I'm just learning as I go.

---

### Post by charlier653 on 2010-01-04
Mine looks like that too, I just truncated it for the post.

Tried several other options, but nothing seems to work.

Guess I'll just have to live with it till next April when the new LTS comes out. Maybe it will be fixed by then.

There is one other thing I could try, but not sure I really want to. Might open up a whole new can of worms:
     Use the windows disk to fixmbr then reinstall grub2 from a live cd. not sure that would get rid of the extra grub or not though.

---

### Post by charlier653 on 2010-01-04
drs305,

Thanks for that link, it does give me some more ideas as to where to look and what/how to mod.

Will leave this open for now, maybe someone can come up with something.

---

### Post by kansasnoob on 2010-01-05
Thought I'd give this a bump because I'm beyond curious :P

---

### Post by charlier653 on 2010-01-09
Submitted a new post on the bug report.

It seems that grub2 has been randomly choosing what partition it looks to for boot files, and giving the environment error as a report that it can't find the boot script.

Found this by rebooting many times and checking where grub was looking. Came back with a different partition every time. No consistency to where grub2 looked, even after using "set root=uuid x". Don't know if any dev will look into this issue. I am hoping that they do, and incorporate any fix for this in the new LTS due out in April.

Have given up on grub2 for my mulitdisk box, and installed legacy. Works every time now, no problems booting into either OS now.

---

