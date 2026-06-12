---
title: "Need Dual Booting Help - Win7/Ubuntu 9.10"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by thefoolisme on 2010-02-10
Let me start by saying if your response is going to be dump Windows, please stop reading.  I keep finding this response to others' questions, and it really doesn't help.

I've used ubuntu in the past, but had been away from it for a while.  I decided to dual-boot my laptop with the latest Ubuntu, since it was last dual-booted with hardy heron.  Everything loaded great, and the dual boot was working...and then it wasn't.  

When the PC boots up, it gets stuck in this loading Stage1.5 loop then reboots.  I managed to get both partitions loaded using an old supergrub disk, but I couldn't get it fixed.  I thought I would use EasyBCD to put Ubuntu in the Win7 boot loader, but that's not working either.  

It seems that Grub2 is to blame from the research I've done.  Seems to me that it's a POS, but that doesn't solve my problem.  How can I fix my dual-boot system to be a working dual-boot system again without having to use an old supergrub disk to get an OS loading?

Thank you in advance for your help.

---

### Post by lidex on 2010-02-10
Stolen from this page:[https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29]("https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29")

> This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy. This can happen if you don't select your drive when running sudo update-from-grub-legacy. Shortly after starting this command the user will be asked to select the device (sda, sdb, etc). Highlight the drive and press the space bar to select it when presented with this screen. Failure to select a drive will result in an Error 15.
To recover from this error, GRUB 2 must be reinstalled. Go to [Reinstalling from the LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for instructions.

---

### Post by lotharmat on 2010-02-10
Or you could just drop Windows.... ;)

*runs away quickly


**Also uses Win7 on a regular basis and actually likes it.

---

### Post by thefoolisme on 2010-02-10
Lidex - that's probably exactly what it is - Grub legacy files, since this laptop had the older Ubuntu on it before.  I'll have to try that.  Thanks!

---

### Post by Mike Green9 on 2010-02-10
[SIZE=1]I have also had problems dual booting W7 and Ubuntu 9.10. I finally got it working using, yes, GRUB2.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]When I installed Ubuntu I made sure that it put GRUB in it's own partition (I also used a mount point of '/').[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I then booted W7 and ran EasyBCD Beta  2.0.0.76. I added GRUB2 to my list, and it did the trick. When I boot, I can load XP, W7, or Ubuntu. [/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I tried NeoGrub and GRUB - to no avail. [/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]For a variety of reasons, I would like to dump Windows. But I hate to admit it, I kinda like W7.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Hope this helps,[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]M...[/SIZE]

---

### Post by thefoolisme on 2010-02-14
OK, I reinstalled Grub2 using the Live CD, and it worked...temporarily.  How can I fix it so it doesn't keep breaking?

---

### Post by lidex on 2010-02-14
I'm not sure of what needs fixing...what is it doing now?

---

### Post by thefoolisme on 2010-02-14
I fixed it using the instructions given.  It worked for a couple of log ons, and then the next time I went to log on, it was broken again.  Just went into a "Starting Grub" then restarting the computer loop.  I had to use a Supergrub disk in order to boot the system up.  I fixed Grub again, but I don't want to have to do that every 3 log ons.  And I don't want to always have to use a supergrub disk when turning the PC on.  I never used to have this problem with the old Grub.  Very frustrating.

---

### Post by lidex on 2010-02-14
Never an easy answer ;)
OK, download the Boot Info Script [here]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.54/boot_info_script054.sh/download")
and follow [these instructions]("http://bootinfoscript.sourceforge.net/"). You'll need to boot from your LiveCD. Post results here.

---

### Post by oldfred on 2010-02-14
If you are running HP or Dell you may have windows software that writes into the MBR which corrupts grub2.

HP ProtectTools and Dell Recovery Tool write into MBR meierfra.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

---

### Post by thefoolisme on 2010-02-15
I'm running an Asus laptop, so the HP and Dell issues aren't a factor.  Below is the boot info script info that was requested.  The first partition is obviously the restore partition.  Sda5 is a separate storage partition that has been on there since my old Ubuntu system.  I look forward to any insight.

Thanks!

_____________________

Results from Boot Info Script:

```
  Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

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

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
4 heads, 44 sectors/track, 3551945 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,523,129    22,523,067  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     22,523,904   335,093,759   312,569,856   7 HPFS/NTFS
/dev/sda3         335,095,728   625,140,911   290,045,184   f W95 Ext d (LBA)
/dev/sda5         335,095,808   530,408,307   195,312,500   7 HPFS/NTFS
/dev/sda6         530,408,340   579,236,591    48,828,252  83 Linux
/dev/sda7         579,236,636   622,205,407    42,968,772  83 Linux
/dev/sda8         622,205,452   625,140,911     2,935,460  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D476-EF15                              vfat       RECOVERY                      
/dev/sda2        32A86085A8604A05                       ntfs       Vista64                       
/dev/sda5        7640675C406721DB                       ntfs       DATA                          
/dev/sda6        3df8a002-bf64-4c69-9fa8-e1b564f866a6   ext4                                     
/dev/sda7        57be0a60-2cbf-4b8a-a61b-17e8dea36e12   ext4                                     
/dev/sda8        bf818a7d-5403-4c99-9aae-139c970c1da2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 3df8a002-bf64-4c69-9fa8-e1b564f866a6
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3df8a002-bf64-4c69-9fa8-e1b564f866a6
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=3df8a002-bf64-4c69-9fa8-e1b564f866a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3df8a002-bf64-4c69-9fa8-e1b564f866a6
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=3df8a002-bf64-4c69-9fa8-e1b564f866a6 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3df8a002-bf64-4c69-9fa8-e1b564f866a6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3df8a002-bf64-4c69-9fa8-e1b564f866a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 3df8a002-bf64-4c69-9fa8-e1b564f866a6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3df8a002-bf64-4c69-9fa8-e1b564f866a6 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d476-ef15
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 32a86085a8604a05
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=3df8a002-bf64-4c69-9fa8-e1b564f866a6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=57be0a60-2cbf-4b8a-a61b-17e8dea36e12 /home           ext4    defaults        0       2
# /storage-disk was on /dev/sda5 during installation
UUID=7640675C406721DB /storage-disk   ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows was on /dev/sda2 during installation
UUID=32A86085A8604A05 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda8 during installation
UUID=bf818a7d-5403-4c99-9aae-139c970c1da2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 273.2GB: boot/grub/core.img
 274.8GB: boot/grub/grub.cfg
 273.1GB: boot/initrd.img-2.6.31-14-generic
 274.6GB: boot/initrd.img-2.6.31-19-generic
 273.1GB: boot/vmlinuz-2.6.31-14-generic
 273.5GB: boot/vmlinuz-2.6.31-19-generic
 274.6GB: initrd.img
 273.1GB: initrd.img.old
 273.5GB: vmlinuz
 273.1GB: vmlinuz.old
```

---

### Post by oldfred on 2010-02-15
I do not see anything wrong with your boot configuration.

The link also has McAfee Security Center ? and I have also see someone who had Norton Ghost running on windows that caused the same problem. meierfra.'s sourceforge page has several solutions. Link in previous post.

---

### Post by thefoolisme on 2010-02-15
If the MacAfee is the problem, then it's still a Grub 2 issue.  The macafee has been on there for ages.  

Looking at the solutions, it seems that I can disable the offending program, and see what happens.  Not really excited about turning off my security software in Windows.  The other alternative is to revert to legacy Grub, which I would gladly do, except I installed Ubuntu with ext4 format.  If everything I've read is correct, legacy Grub won't work with ext4, correct?

There has to be another permanent solution, other than reinstalling Ubuntu with an ext3 file format, I would think.

---

### Post by lidex on 2010-02-15
Does this happen after booting into one of your windows configurations? I see BCD in there.

Can you do me a favor and go back into that post and enclose those script results in code tags please. Just click "edit" then "advanced" highlight the text and click the "#". Thankyou.

---

### Post by thefoolisme on 2010-02-15
Done.  
I tried using BCD early on as an idea from another posting to try and fix this.  There shouldn't be anything listed in the BCD startup anymore.  

Thanks.

---

### Post by oldfred on 2010-02-15
Ubuntu modified its version of grub 0.97 to boot ext4 partitions. Other distributions may not as grub legacy has not been maintained for about 10 years and every distribution made minor patches.
You should be able to revert to old grub as 9.04 used old grub and would boot ext4.

I do not consider software that writes into the MBR to hide hidden serial numbers valid software. Also some of the virus checkers are not smart enough to know grub is valid in the MBR not just a  windows MBR boot loader.

---

### Post by mikechant on 2010-02-16
Oldfred said:
> Ubuntu modified its version of grub 0.97 to boot ext4 partitions. Other distributions may not as grub legacy has not been maintained for about 10 years and every distribution made minor patches.
You should be able to revert to old grub as 9.04 used old grub and would boot ext4.

Just to agree - I stuck to old grub (9.04 version) when I installed 9.10 and it's working just fine with ext4.
At present I intend to stay with grub legacy (as it's officially known) for the foreseeable future. Too many problems reported with grub2 at present.

---

### Post by Mark Phelps on 2010-02-16
Since you're using Legacy GRUB, I've posted a link to the SuperGrubDisk page dealing with Stage 1.1 boot problems and Windows.

While this may NOT be your problem, it's probably worth looking at anyway:

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

---

### Post by thefoolisme on 2010-02-16
Thanks for the info about legacy Grub.  I think I'll try reverting to the old Grub since it will work with ext4 when I have a chance in the next few days.  Seems like it would probably be the simplest solution.  I appreciate the help and comments folks!

---

### Post by thefoolisme on 2010-02-20
OK, I'm about ready to give up.  I can't get legacy grub to install correctly and run.  I can't get Grub 2 to stop breaking. I can't believe they released Ubuntu 9.10 with grub 2 like this.  So much for "It just works." I've been playing with Ubuntu on and off for the last 5 years or so, and I have never had an issue like this.  

Can someone please help me get this right?  Reinstalling Grub 2 only works until I boot into Windows again.  Installing legacy grub per the link below doesn't work at all.  

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR) 

I just want my dual-boot system to work like it should.  Help!!!

---

### Post by thefoolisme on 2010-02-20
After walking away from this for a while, then coming back, I think I have managed to successfully uninstall Grub2, install legacy Grub using this: 

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

Then figuring out how to add Windows to the list using this post:
[http://ubuntuforums.org/showthread.php?t=1379429&highlight=adding+windows+legacy+grub](http://ubuntuforums.org/showthread.php?t=1379429&highlight=adding+windows+legacy+grub)

It doesn't seem to be perfect (i.e. I probably put something extra into the Grub menu lst, but it IS working, and that's all i wanted.  :-)

---

