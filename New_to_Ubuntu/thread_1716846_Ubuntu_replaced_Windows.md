---
title: "Ubuntu replaced Windows"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by JamesBartlett on 2011-03-29
Hi guys I recently got hold of a Linux CD, but as an avid gamer and computer enthusiast familiar with Windows, I did not want to replace Windows. During the installation, I opted to install alongside Windows (presuming, as I have seen before that there would be an option to choose the OS to run during the boot sequence). However, when I boot up my system now, it runs straight into Ubuntu. The strange thing however, is that despite having a 320gb hard drive, Ubuntu says that only 280gb of free space, and I know my Windows 7 OS plus all my files/programs took up roughly 40gb. Is it there somewhere? How do I get to it? Even just the data, if need be I can buy Windows again.

Not a happy camper to start with.

---

### Post by ~Plue on 2011-03-29
could you post the results of the boot info script >> [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

the instructions would be provided at the page linked above

---

### Post by d3v1150m471c on 2011-03-29
my guess is it's showing the size of it's partition, not the entire hdd size. which would be normal. Also, hold shift while booting after you clear bios,...you should see windows 7 on the grub screen.

---

### Post by kansasnoob on 2011-03-29
> **~Plue said:**
> could you post the results of the boot info script >> [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

the instructions would be provided at the page linked above

+1! That'll show us what you actually have for partitions, etc.

If Windows was overwritten and you need to recover any files you should run only the live CD/USB until we see what's actually going on.

---

### Post by Grenage on 2011-03-29
> **d3v1150m471c said:**
> my guess is it's showing the size of it's partition, not the entire hdd size. which would be normal. Also, hold shift while booting after you clear bios,...you should see windows 7 on the grub screen.

Grub will show by default if there is more than one OS.

It's probably worth running this from a command line:

```
sudo update-grub
```

It might pick it up, it might not; assuming it doesn't, ~Plue's advice will give people here the info they need to help you.

---

### Post by JamesBartlett on 2011-03-29
x

---

### Post by JamesBartlett on 2011-03-29
> **Grenage said:**
> Grub will show by default if there is more than one OS.

It's probably worth running this from a command line:

```
sudo update-grub
```

It might pick it up, it might not; assuming it doesn't, ~Plue's advice will give people here the info they need to help you.
Cheers mate, it looks like I'm only getting Ubuntu...

---

### Post by JamesBartlett on 2011-03-29
> **d3v1150m471c said:**
> my guess is it's showing the size of it's partition, not the entire hdd size. which would be normal. Also, hold shift while booting after you clear bios,...you should see windows 7 on the grub screen.
Thanks for your help mate, but no luck...

---

### Post by kansasnoob on 2011-03-29
That's the actual content of the script itself. You need to "run" the script in a terminal. Maybe the instructions here are easier to follow:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by JamesBartlett on 2011-03-29
Ah, my mistake. Thanks Kansasnoob.
Is this what you're after?

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39fbd63b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        96,389        96,327  83 Linux
/dev/sda2              96,390   625,137,344   625,040,955   5 Extended
/dev/sda5           2,088,513    15,888,284    13,799,772  83 Linux
/dev/sda6          32,081,868    36,081,989     4,000,122  83 Linux
/dev/sda7              96,516     2,088,449     1,991,934  83 Linux
/dev/sda8          36,082,053   613,827,584   577,745,532  83 Linux
/dev/sda9         613,827,648   625,137,344    11,309,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c2c00715-6c0f-4883-9a8a-be291c417e20   ext4                                     
/dev/sda5        1d02eaac-ef76-4352-8a4b-c1fea055d428   ext4                                     
/dev/sda6        e51a857b-c8cd-4936-9545-28e258529fea   ext4                                     
/dev/sda7        f872158f-cecc-4723-9d83-2a68c99c5947   ext4                                     
/dev/sda8        9c1e0aee-0df1-45e9-aa77-84a3078845f9   ext4                                     
/dev/sda9        eef08a91-b726-4938-9b25-23a8a73d3019   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


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
UUID=e51a857b-c8cd-4936-9545-28e258529fea /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c2c00715-6c0f-4883-9a8a-be291c417e20 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=1d02eaac-ef76-4352-8a4b-c1fea055d428 /home           ext4    defaults        0       2
# /swap was on /dev/sda7 during installation
UUID=f872158f-cecc-4723-9d83-2a68c99c5947 /swap           ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 9c1e0aee-0df1-45e9-aa77-84a3078845f9
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
menuentry "Ubuntu, Linux 2.6.31-23-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 9c1e0aee-0df1-45e9-aa77-84a3078845f9
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=9c1e0aee-0df1-45e9-aa77-84a3078845f9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 9c1e0aee-0df1-45e9-aa77-84a3078845f9
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=9c1e0aee-0df1-45e9-aa77-84a3078845f9 ro single 
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 9c1e0aee-0df1-45e9-aa77-84a3078845f9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9c1e0aee-0df1-45e9-aa77-84a3078845f9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 9c1e0aee-0df1-45e9-aa77-84a3078845f9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9c1e0aee-0df1-45e9-aa77-84a3078845f9 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=9c1e0aee-0df1-45e9-aa77-84a3078845f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=eef08a91-b726-4938-9b25-23a8a73d3019 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  20.0GB: boot/grub/core.img
  19.2GB: boot/grub/grub.cfg
  19.1GB: boot/initrd.img-2.6.31-14-generic
  20.0GB: boot/initrd.img-2.6.31-23-generic
  19.0GB: boot/vmlinuz-2.6.31-14-generic
  19.7GB: boot/vmlinuz-2.6.31-23-generic
  20.0GB: initrd.img
  19.1GB: initrd.img.old
  19.7GB: vmlinuz
  19.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by Grenage on 2011-03-29
It looks like you overwrote the disk, so your Windows install is gone.  Do you have data you need to recover?

---

### Post by JamesBartlett on 2011-03-29
You're kidding me!!! I specifically chose to install alongside Windows. I have tons of data I want to get at, I also have an external hard drive with media I want to access, but isn't recognised by Ubuntu, mostly for music/video files. (mp3/wav/avi/wma)

---

### Post by Grenage on 2011-03-29
I can't see anything listed on sda (your only disc) other than Linux partitions.

First things first, don't boot from or make any changes to the drive; boot from a live CD, such as the Ubuntu disc.  You may have some success getting data back using photorec/testdisk, but I don't believe it will restore the file names.

---

### Post by nothingspecial on 2011-03-29
> **JamesBartlett said:**
>  I also have an external hard drive with media I want to access, but isn't recognised by Ubuntu, mostly for music/video files. (mp3/wav/avi/wma)

Install the ubuntu-restricted-extras package.

---

### Post by JamesBartlett on 2011-03-29
Cheers guys, I hate to be a pain but you're really gonna have to talk me through it...

---

### Post by Grenage on 2011-03-29
> **JamesBartlett said:**
> Cheers guys, I hate to be a pain but you're really gonna have to talk me through it...

I'll step back from this; I have no real experience with testdisk, and it's not my data.  While there are some good guides out there, I am sure more experienced users will be able to provide more assistance.

---

### Post by nothingspecial on 2011-03-29
As it stands windows is gone. Probably most of your data.

The most important thing is to stop using your computer, as in the install now. The more you use it the less chance you have of any data recovery.

You need to boot the live cd and use that while you attempt recovery.

Then you need to read this

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

and this

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Then you need to cross your fingers or pray or whatever.

The chances of getting your stuff back are slim. If you do recover anything the chances are the files will be in no sort of order and a complete mess.

I'm impressed you are being so calm about this.

---

### Post by JamesBartlett on 2011-03-29
> **Grenage said:**
> I'll step back from this; I have no real experience with testdisk, and it's not my data.  While there are some good guides out there, I am sure more experienced users will be able to provide more assistance.
No problem, thanks for your help so far.

---

### Post by Mark Phelps on 2011-03-29
If you're willing to experiment and have access to a Windows PC, I recommend the following:
1) Remove your drive from the PC
2) On the Windows PC, go to the Runtime Software website, download and install the free version of Recover My Files and/or GetDataBack for NTFS.
3) Plug your drive into the Windows PC
4) Run the data recovery software (most probably overnight) to see what it can find.

It won't recovery anything (the free version) but you will be able to see what it can find. Based on those results, you will then need to decide whether or not to purchase it in order to do the actual data recovery.

---

### Post by Grenage on 2011-03-29
> **Mark Phelps said:**
> If you're willing to experiment and have access to a Windows PC, I recommend the following:
1) Remove your drive from the PC
2) On the Windows PC, go to the Runtime Software website, download and install the free version of Recover My Files and/or GetDataBack for NTFS.
3) Plug your drive into the Windows PC
4) Run the data recovery software (most probably overnight) to see what it can find.

It won't recovery anything (the free version) but you will be able to see what it can find. Based on those results, you will then need to decide whether or not to purchase it in order to do the actual data recovery.

Good thinking, it slipped my mind that it was a Windows install, and likely NTFS.  Get Data Back for NTFS is an _excellent_ program.

---

### Post by JamesBartlett on 2011-03-31
Thanks a million guys, I'm going to mark this solved, I bit the bullet and did a clean sweep of the HD, installing Ubuntu as the solitary OS. I do like it, but I'm not going to lie, I miss win7, I know Windows inside out. But, I'm with Ubuntu now and am definitely liking it, Thanks for your help guys.

---

### Post by nothingspecial on 2011-03-31
Once again, I applaud your calm. I've seen so many people flip in this situation.

Did you install the restricted-extras package to play all your mp3/wma whatever they are files?

---

### Post by JamesBartlett on 2011-03-31
I did mate. all good, mp3 files playing A-OK. And I may seem calm but I'm gutted tbh, I'd made a lot of Music on FL Studios - All gone. No point losing the head though! Thanks for everything!

---

