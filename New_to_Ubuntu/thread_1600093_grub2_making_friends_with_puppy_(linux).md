---
title: "grub2 making friends with puppy (linux)"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by duruttye on 2010-10-18
Hey there!

I have xubuntu 10.10, and just installed puppy linux on /dev/sda7.

I'm having trouble updating grub, because it seems that grub doesn't find it at all.

So I'm prepared to put in some serious coding in the grub.cfg file in case somebody can help me.

For now, this is the only code I found floating around the forums, but it just doesn't feel right at all, especially the last 2 lines :) : 

[HTML]# For booting GNU/Linux on dev/sda7 (H.D.D. primary partition)
menuentry "Puppy Linux (on /dev/sda7)" {
        set root=(hd0,7)
        linux /puppy551/vmlinuz
        initrd /puppy551/initrd.gz

}[/HTML]

I mounted that partition in xubuntu:

```
/media/puppy$ ls 
extlinux.conf  initrd.gz  lupu-511.sfs  vmlinuz
```


So could anyone point me to the right direction?
In case you need some more information, just say so :)

thank you!

---

### Post by duruttye on 2010-10-18
I downloaded and ran this script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and I have this result:

[PHP]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,623,859    29,623,797   7 HPFS/NTFS
/dev/sda2          29,623,860    49,158,899    19,535,040  83 Linux
/dev/sda3          49,158,900   234,436,544   185,277,645   5 Extended
/dev/sda5          49,158,963    74,364,884    25,205,922  83 Linux
/dev/sda6          78,461,523   234,436,544   155,975,022  83 Linux
/dev/sda7    *     74,364,948    78,461,459     4,096,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F0248009247FD0D8                       ntfs                                     
/dev/sda2        5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        95d60b33-c0f9-462e-830b-6bcf040bbb28   ext4                                     
/dev/sda6        f11c9e02-6f35-4538-a114-0dc64f8fc561   ext4                                     
/dev/sda7        01205d9e-21e1-4285-a8ce-e79ef2fa6eb5   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sda7        /media/puppy             ext4       (rw,commit=0)
/dev/sda6        /media/cuccok            ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c
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
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c ro single 
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
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set f0248009247fd0d8
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Puppy Linux (on /dev/sda7)" {
	insmod part_msdos
        insmod ext2
        set root='(hd0,msdos7)'
        linux16 /media/puppy/vmlinuz
	initrd /media/puppy/initrd.gz
	

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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=5b8a974d-4d7e-4eeb-af6c-9b28ba54b52c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=95d60b33-c0f9-462e-830b-6bcf040bbb28 /home           ext4    defaults        0       2
# /media/cuccok was on /dev/sda6 during installation
UUID=f11c9e02-6f35-4538-a114-0dc64f8fc561 /media/cuccok   ext4    defaults        0       2
# /media/windows was on /dev/sda1 during installation
UUID=F0248009247FD0D8 /media/windows  ntfs    defaults,umask=007,gid=46 0       0
#innen /media/pupp was on /dev/sda7
UUID=01205d9e-21e1-4285-a8ce-e79ef2fa6eb5 /media/puppy    ext4    defaults        0       2

=================== sda2: Location of files loaded by Grub: ===================


  20.0GB: boot/grub/core.img
  17.7GB: boot/grub/grub.cfg
  16.4GB: boot/initrd.img-2.6.35-22-generic
  20.1GB: boot/vmlinuz-2.6.35-22-generic
  16.4GB: initrd.img
  20.1GB: vmlinuz

=================== sda5: Location of files loaded by Grub: ===================


  25.5GB: initrd.gz
  25.4GB: vmlinuz

=================== sda7: Location of files loaded by Grub: ===================


  38.2GB: initrd.gz
  38.2GB: vmlinuz[/PHP]

---

### Post by oldfred on 2010-10-18
Is this like a grub.cfg? extlinux.conf if so print it also as the script does not look for that file & print it.

I do not understand the stanza you have:

menuentry "Puppy Linux (on /dev/sda7)" {
    insmod part_msdos
        insmod ext2
        set root='(hd0,msdos7)'
        linux16 /media/puppy/vmlinuz
    initrd /media/puppy/initrd.gz


/media/puppy is your mount point. It looks like the kernal & init are in the root of sda7 so the entry should be more like just /vmlinuz, but they almost always require parameters.

The MultiBoot USB has this entry where it has copied the files to /boot/puppy. But the media is usbflash.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)


    menuentry "Puppy" {
        linux /boot/puppy/vmlinuz root=/dev/ram0 pmedia=usbflash loglevel=7 pkeys=us
        initrd /boot/puppy/initrd.gz
    }

---

### Post by duruttye on 2010-10-19
Well, I don't understand that stanza either :) I just deducted it, I'm just another noob, snooping around where I shouldn't

I don't want to Multiboot USB, because I installed puppy linux on sda7, so, if anyone knows what to do to have that puppy linux installation in grub2 menu and to have it boot properly, please help me :)

If you need some additional information, just say so!

And thank you for the reply!

---

### Post by duruttye on 2010-10-25
Hey, 
just checking:)

any ideas out there?

---

### Post by oldfred on 2010-10-25
OK, I have lupu-511.sfs booting from my flash drive sdd1 with grub2.:)

I tried a variety of alternatives of the command line options that others had used and this worked but I may have some setting not quite right. I tried to get psubdir= option to work but the kernel would load and it would not find lupu-511.sfs. So I moved lupu-511.sfs to root of sdd1. I created /boot/lupu511 to hold all the other files. And my grub2 is in /boot/grub. When I boot I select sdd as boot drive and that then becomes hd0 in grub2. My system sees flash drives as usb hard drive.

menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=usbflash loglevel=7 pkeys=us 
initrd /boot/lupu511/initrd.gz
}

---

### Post by duruttye on 2010-10-25
Well, this is bigger then me, it seems.

menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz pkeys=us 
initrd /boot/lupu511/initrd.gz
}

this is what I tried in grub.cfg after I made a folder in /boot/ named lupu511

```
/boot/lupu511$ ls -a
.  ..  extlinux.conf  initrd.gz  lupu-511.sfs  vmlinuz

```

After boot, grub sees that there is a entry in the menu, but after I select it, it says, file not found, or something similar...

My grub2 is also in /boot/grub, so as of from now they are on the same partition, marked as bootable...

I don't know...

Thank you anyway!

Just a reminder: I'm trying to boot from my hard drive, not an usb-drive.

---

### Post by duruttye on 2010-10-25
Hey there!

I found this:
[http://murga-linux.com/puppy/viewtopic.php?t=54210&sid=da579444fef56102d251b11e75374464](http://murga-linux.com/puppy/viewtopic.php?t=54210&sid=da579444fef56102d251b11e75374464)

Could someone help me a translate that last posters guide. I have no idea what I should do with that, but it seems, that that guy did it with ease...

pleeease, pretty please

---

### Post by C.S.Cameron on 2010-10-25
MultiBootUSB will boot Puppy using grub2.
I suggest that reviewing their script could be enlightening:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by oldfred on 2010-10-25
Do you get kernel to load and then it says lupu-511.sfs not found? This was the error I consistently got until I moved the lupu-511.sfs up to the top level and removed the psubdir= entry.

I did have to have the  root=/dev/ram0. I tried both  pmedia=usbflash and pmedia=atahd. 

Try an entry like this and if you still get a not found, put a copy of lupu-511.sfs in the top level of hd0,1. ( Same level as /boot folder)

menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz  root=/dev/ram0 pmedia=atahd pkeys=us 
initrd /boot/lupu511/initrd.gz
}

---

### Post by duruttye on 2010-10-26
Hey oldfred!

I tried what you said, but it didn't work.

Error: file not found
error: you need to load the kernel first (or something similar), so I didn't load the kernel after all :)

this is in the grub.cfg:

```
### BEGIN

menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd pkeys=us 
initrd /boot/lupu511/initrd.gz
}
### END
```

this is on the boot partition from where the ubuntu boots:
```
ls
bin    etc            initrd.img    media  root     sys  vmlinuz
boot   extlinux.conf  lib           mnt    sbin     tmp
cdrom  home           lost+found    opt    selinux  usr
dev    initrd.gz      lupu-511.sfs  proc   srv      var

```
when I copied it to this location, it asked if I want to replace vmlinuz, and I didn't replace it, I guess that belongs to ubuntu...

and this is the /boot/lupu511 folder:

```
/boot/lupu511$ ls
extlinux.conf  initrd.gz  lupu-511.sfs  vmlinuz

```

I can't really believe that there is nobody who wrote down how to boot puppy linux with grub2 from a clean, separate partition besides ubuntu, this is somewhat odd :)

Thank you for your time, I'm very close to giving up.

---

### Post by duruttye on 2010-10-26
I tried it without the ```
root=/dev/ram0
``` thing in grub.cfg, but it didn't do any good :)

---

### Post by oldfred on 2010-10-26
I just created a new partition sdc13 on my drive, but boot from sdb2 which is a gpt drive.

This worked:
```
menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}
```

I did have to move lupu-511.sfs to the top level of the partition ( same as /boot not inside /boot) and created /boot/lupu511 with all the other files including vmlinux & initrd.gz.

---

### Post by angelsguitar on 2011-01-07
Hi.

I was just looking around for some references on how to boot Puppy using grub2 and found this.

Is it working alright? Did you solved your issue?

---

### Post by melenegiorgo on 2011-02-20
I actually made it work following this post 

> ust spent an "interesting" 2 hours wrestling with Grub2 after I downloaded the final release of Ubuntu 9.10 today. 

I prefer to use Ubuntu's grub to boot all my distros and previously used the /boot/grub/menu.lst in Ubuntu. I did the same this time installing Ubuntu's grub into the MBR. 

It picked up Windows xp, Windows 7, Ubuntu 9.10 and Ubuntu 9.04, Fedora 11 and Debian 5. 

It failed to recognise any of my 5 Puppy frugal installs or Tiny Core Linux. But there again grub 0.97 also failed in that way. 

Eventually got it to boot the Puppies so in case others want to do this, here goes (some of this is a repeat of what's above)..... 

1. As mentioned don't do anything to the /boot/grub/grub.cfg file !!! 

2. Copy the file Quote:
/etc/grub.d/40_custom

somewhere. 

3. rename it something like Quote:
41_puppy431



4. after the 5 lines of existing text add whatever you need to boot puppy ...see below. 

5. move the file back to /etc/grub.d/ 

6. Code:
 sudo chmod +x /etc/grub.d/41_puppy

to make the file executable. 

7. Code:
 sudo grub-makeconfig 


then Code:
 sudo update-grub



Without this the /boot/grub/grub.cfg file doesn't get updated. 

8. Now the grub boot code that seemed to work for me was 
Code:

menuentry "Whatever you call puppy" { 
set root=(hd1,5) 
linux  /puppy431/vmlinuz  psubdir=puppy431 
initrd  /puppy431/initrd.gz 
} 
EOF 


Nice and simple. Obviously change depending on your installation. This was for Puppy431 residing as a frugal on sdb5 in a subdirectory called /puppy431. Note the numbering. 

9. The way of describing a partition has changed!!! 
I have my Puppies on sdb5 . This used to be described in grub as (hd1,4). Now it's (hd1,5).  

10. Note that adding Quote:
insmod ext3 

just after the menuentry line seemed to stop it booting. 

Also adding a line Quote:
search --fs-uuid --set ehdn78sh-3738-6dg8-bba3-ehd76sgs6sgs

to identify the UUID of the partition that puppy is on didn't seem to be necessary. 

This worked for puppy 412, 421, 431.1 and 431. 

I am still struggling to get puppy214X working. It does work using the psubdir method above but you're back to having to tell it which pup_save file to use. 

Make similar files for other puppies and note that grub will list them in numerical order so, for example, 42_puppy412 will come before 43_puppy214. 

HTH 
Dave


My puppy was in sda9 and I was keep writing root=(hd0,8) witch obsiously wrong due to changes.

The right thing to write is root=(hd0,9)

---

### Post by mcdohl on 2011-08-03
hi,
after googling here and there,
i actually didn't remember how i get to this and it works:

menuentry "Puppy linux 511 on sda7" {
set root=(hd0,7)
linux /boot/vmlinuz root=/dev/sda7 pmedia=atahd
}
### END

hope that help :)

---

