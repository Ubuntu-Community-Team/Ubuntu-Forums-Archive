---
title: "Another Kernel Panic"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by warch on 2011-01-05
Maybe "absolute beginner" isn't the best section, but I might as well be one because I know so little compared to others. 

On my Dell Dimension 8110 I was updating 10.10 and on restart I got the dreaded :Kernel Panic - not syncing: VFS: Unable to mount root FS on unknown-block(0,0).

The first thing I did think of was poorly seated or dead memory module. I took them all out and reseated, did a memory test. All appears OK. 

I found quite a few other posts around the net with this same issue, but nothing that related to mine. 

Having two hard drives (the slave was empty) I disconnected the orig master and connected the slave as the master. I loaded 10.10 on it. It is operating normally, so I assume we can rule out memory.

When the original HD is connected as the slave, I can access it. 


Here is a screen shot of the original panic:

[IMG]http://billarchibald.com/misc/kernel_panic.jpg[/IMG]


Is there a simple solution by copying any file from the new and good install into the old?

Please any help written as if to a complete idiot would help.

---

### Post by ulfj on 2011-01-05
I got that one a while back also and never could figure it out so I got annoyed and did a fresh install. I'll be keeping track of this thread because I'd rather not do that again when I know there is a fix out there somewhere! Sorry I couldn't help any on this one.

---

### Post by warch on 2011-01-05
ulfj,

I've searched far and wide and many have had this problem, there are many "suggestions" as to what to do, but I have not read yet a definitive answer.

I'm beginning to wonder if this is a serious bug when updating that no one has a solution for. 

I too could do a fresh install, but there are many things I would REALLY like to not to start fresh, besides my preferences. And I have found no solution as to doing a "repair" install.

---

### Post by TechWiz2100 on 2011-01-05
The error is based on the file systems and MBR of the hard drive. Either the HDD that has Ubuntu was moved to a different controller which would cause a change to the first coordinate in the hdd(0,0) or Ubuntu is not installed to partition 1.

Your best bet for getting around this would be to F8 and enter root=/dev/sda1 or root=/dev/sda and then change it in grub later on.

Also, there could be an issue that caused your Ubuntu partition to become un-flagged as bootable which can be fixed with fdisk in terminal or System > Administration > Disk Utility

---

### Post by warch on 2011-01-06
Thanks TechWiz,

But this HD will not boot at all. The only option I have as it tries to boot is to enter setup (F2). Otherwise, no key strokes work. How can I "F8 and enter" anything?

Remember, treat me like an idiot, because obviously I am missing something basic.

---

### Post by TechWiz2100 on 2011-01-06
My apologies

By F8 I mean spam the F8 key after your computer makes the post beep if grub does not pop up to give you options.

If it does however pop up giving you a list of Ubuntu's with kernels and what not to choose from, select recovery mode if available or simply move to another selection, then back to the first selection (to stop the timer) and then type in the above root variable.

I assume you are using grub and the 2nd option will work for you but I'm not positive and F8 is usually the generic boot interrupt.

---

### Post by warch on 2011-01-06
OK, please bear with me. 


Grub does come up:
[ATTACH]180291[/ATTACH]


The top & middle recovery options go to this screen with no keystroke possible 
[ATTACH]180292[/ATTACH]

The bottom recovery option brought this up

[ATTACH]180293[/ATTACH]

when I entered either root=/dev/sda or root=/dev/sada1.....  this was the result: 
[ATTACH]180294[/ATTACH]


So I  restarted into GRUB and selected "e".
This was the screen that came up:
[ATTACH]180295[/ATTACH]

I added root=/dev/sda1 or root=/dev/sda  and see this:

[IMG]http://billarchibald.com/misc/Ubuntu307.jpg[/IMG]


I have tried all sorts of combinations and nothing happens.

I swapped disks again and had this problematic disk as sdb and looked at it with the disk utility, and it IS flagged as bootable.

Again, are there any boot files or something I can copy from the good disk onto the bad one? Or is there a command I can enter from the command line that I can get to through grub. 

Or perhaps the boot sector is just plain bad on that drive and nothing will write to it? I do find it curious that this happened on restart after an update.

---

### Post by TechWiz2100 on 2011-01-06
Don't worry this is actually a pretty odd error so its not just because you're new lol

Do any of the other non recovery kernels boot at all? From the looks of it you had your Ubuntu set up running for a while now, at least a few months.

The thing that baffles me is that it seems like sda in recovery 3 is actually pointing to your optical drive instead of your hard drive which isn't right...

The problem was probably caused by a bad kernel update most likely your 2.6.35-24

If you still have a Live CD for Ubuntu 10.10 lying around I recommend you take a look at this link: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

It will guide you through the re-installation of grub from Live CD and that will hopefully fix your issue. If not then it may be the drive but I'm doubtful that it is or grub have issues showing up at all.

---

### Post by sandyd on 2011-01-06
> **warch said:**
> OK, please bear with me. 


Grub does come up:
[ATTACH]180291[/ATTACH]


The top & middle recovery options go to this screen with no keystroke possible 
[ATTACH]180292[/ATTACH]

The bottom recovery option brought this up

[ATTACH]180293[/ATTACH]

when I entered either root=/dev/sda or root=/dev/sada1.....  this was the result: 
[ATTACH]180294[/ATTACH]


So I  restarted into GRUB and selected "e".
This was the screen that came up:
[ATTACH]180295[/ATTACH]

I added root=/dev/sda1 or root=/dev/sda  and see this:

[IMG]http://billarchibald.com/misc/Ubuntu307.jpg[/IMG]


I have tried all sorts of combinations and nothing happens.

I swapped disks again and had this problematic disk as sdb and looked at it with the disk utility, and it IS flagged as bootable.

Again, are there any boot files or something I can copy from the good disk onto the bad one? Or is there a command I can enter from the command line that I can get to through grub. 

Or perhaps the boot sector is just plain bad on that drive and nothing will write to it? I do find it curious that this happened on restart after an update.
This has NOTHING to do with the boot sector. Since GRUB shows up fine, the boot sector is intact. 

Boot using a livecd, and post output of the boot info script -> [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by warch on 2011-01-06
Thanks guys.

Yes, I have had Ubuntu running on that box for some time - I can't even remember exactly which version I loaded and when, but I know 10.10 went on it on 10-11 - I was eagerly waiting.

[QUOTE=TechWiz2100]The problem was probably caused by a bad kernel update most likely your 2.6.35-24[/QUOTE]
I can't argue with that assumption, as that was the update before the restart that initiated this issue . And no, the other recovery kernels do not boot. 



I am backing-up important files now,it'll be a few hours - I only have 51 more gigs to copy.  I will swap the unbootable drive back to  primary and see what I can do or find out with a livecd - yes I still have a 10.10 cd (and a 9.04 and 8.10 [IMG]http://billarchibald.com/smilies/pc_smash.gif[/IMG])

again, thanks

---

### Post by warch on 2011-01-06
sandyd,

EDIT: ignore this, see below

---

### Post by warch on 2011-01-06
TechWiz,

I did as you suggested. At the grub prompt, I entered:

find /boot/grub/stage1

(which was directed on the link you supplied), I received this response

Error15: File not found

---

### Post by warch on 2011-01-07
Sorry Sandyd, I am an idiot - but I am learning.

I just went back to the sourceforge page and read more carefully how to generate the results of the boot info script;

Here they are:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   315,531,263   315,529,216  83 Linux
/dev/sda2         315,533,310   321,671,167     6,137,858   5 Extended
/dev/sda5         315,533,312   321,671,167     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        62edfa57-3459-4f98-81ef-c94f3b5f9b2f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8cf82531-157e-4a24-ac97-1977704f0122   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=62edfa57-3459-4f98-81ef-c94f3b5f9b2f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=62edfa57-3459-4f98-81ef-c94f3b5f9b2f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=62edfa57-3459-4f98-81ef-c94f3b5f9b2f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=62edfa57-3459-4f98-81ef-c94f3b5f9b2f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=62edfa57-3459-4f98-81ef-c94f3b5f9b2f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=62edfa57-3459-4f98-81ef-c94f3b5f9b2f ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 62edfa57-3459-4f98-81ef-c94f3b5f9b2f
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/core.img
  99.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 147.3GB: boot/initrd.img-2.6.35-23-generic
 151.1GB: boot/initrd.img-2.6.35-24-generic
  98.9GB: boot/vmlinuz-2.6.35-22-generic
 127.3GB: boot/vmlinuz-2.6.35-23-generic
   8.6GB: boot/vmlinuz-2.6.35-24-generic
 151.1GB: initrd.img
 147.3GB: initrd.img.old
   8.6GB: vmlinuz
 127.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by TechWiz2100 on 2011-01-07
> **warch said:**
> TechWiz,

I did as you suggested. At the grub prompt, I entered:

find /boot/grub/stage1

(which was directed on the link you supplied), I received this response

Error15: File not found

Did you mount the drive in LiveCD before running the find command? There is info on mounting drives and partitions further down in the post that I linked. As for your report from the script... All seems fine and well to me... Maybe Sandy can further decrypt it and get something useful out of it.

---

### Post by warch on 2011-01-07
TechWiz,

I have spent way too many hours researching this today (my eyes are crossed, fuzzy, and pained).

One page that greatly interested me was this:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and one line that caught my eye was this:

"There is no "/find boot/grub/stage1" at the grub prompt. Stage 1.5 has been eliminated."

and yes, I do have Grub2, as you can see from this image

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180291&d=1294334910[/IMG]

I have reloaded Grub as per instructions found today, so I sincerely doubt it is a Grub problem. 

What I would like to do is reload the kernel from a livecd, but have not found those instructions. 

I have tried to boot with rescatux, but for some reasons when it asks for my username and password, it will not accept what I enter.

I am about to throw in the towel and reload, but that stubborn streak in me wants to find the fix. I will await what Sandy says about the report

---

### Post by TechWiz2100 on 2011-01-08
I'm starting to think that its the drive acting up and I apologize for linking you to the wrong thread, I hadn't realized such a change in Grub2 and I assumed Ubuntu was still using Grub v1 because at the top it still says Grub version 1.x instead of 2.x (who the hell is responsible for that one).

I can probably guide you through the process to manually install the kernel again but thats probably not going to fix a thing because Grub is reporting issues loading/locating the partition for Ubuntu.

Your report shows everything is A-OK so I don't quite understand why its not working and the last things I can think of is a broken hard disk or corrupt filesystem. Grub is seeking via UUID which I believe never changes so regardless of which controller the device is in, Ubuntu should be able to find it.

I wish the devs would stop tinkering so much with Grub... it was already a pain to deal with when it didn't work before and the tinkering and changes only make it that much worse lol

---

### Post by tsh on 2011-01-08
Same problem here.I just installed 10.10 on a drive which had 6.10 before, only formatting sda1. Tried a few grub command line options, but not sure any more what the right syntax is for boot drive and root partition. Going to try live boot and chroot.

---

### Post by warch on 2011-01-08
Yes TechWiz,

Although I am an idiot;) I am learning a lot on the fly, and I (even though being an idiot)see weird stuff that indicates a disk malfunction. HOWEVER when I have it as sdb and a new install on sda, everything is there. This makes me think the MBR has been corrupted (is that sound logic?).

When I look at that disk with the disk utility, it does indicate a "few" bad sectors. 

It is an old disk, it is an old machine. I basically loaded Ubuntu as a test and as the first step to get the windoze monkey off my back. 

If you could give me the steps on reloading the kernel (any kernel) from a livecd boot, I'd appreciate it. I'm not quite ready to give up. 

and thank you for your time.

---

### Post by tsh on 2011-01-08
A couple of things to try, turn off all the features in the BIOS (this worked for me, can work out which one later) or if you can boot with the live cd you can ```
install-grub
``` after mounting your boot drive, give the root-directory as /mount/bootdrive.

---

### Post by warch on 2011-01-08
> **tsh said:**
> A couple of things to try, turn off all the features in the BIOS (this worked for me, can work out which one later) or if you can boot with the live cd you can ```
install-grub
``` after mounting your boot drive, give the root-directory as /mount/bootdrive.

I have a feeling this was accomplished when I loaded Rescatux (in safe mode) and had it restore grub2.

But I could be wrong.

---

### Post by TechWiz2100 on 2011-01-09
Oh wait a sec, does your BIOS have settings for your SATA controller such as AHCI and what not? While I was messing around with my Hackintosh system, I found that certain SATA drives do not work properly under certain SATA settings (which lead to OS X bonking up a storm for a few more hours of frustration lol)

You said the device works fine as SDB when its not booting. Try messing around with those for a bit and report back your findings or screenshot your BIOS for us.

---

### Post by warch on 2011-01-09
Now, you bring up something that confused me, but did not delve into because I just accounted it to my lack of knowledge (aka idiocy). 

Correct me if I am wrong. Linux drive nomenclature of sda, sdb, etc refer to SATA drives, while hda, hdb, etc refer to IDE/ATA drives. Well my Ubuntu system is old and uses IDE drives NOT SATA. HOWEVER, whenever I use *fdisk -l*, the drive(s) are refered to as sdX.


Therefore, being IDE there is no SATA controller, correct?  And I just looked at the BIOS and see no evidence of SATA settings

---

### Post by TechWiz2100 on 2011-01-09
SDA usually represents Serial Device A as in USB/SATA/SCSI what have you but there are some cases where IDE gets put in for SDA and vise versa due to BIOS config but I'm no expert on that. I think it has to do with the PATA driver also using SDA to eliminate HDA and confusions of multiple sorts.
[http://en.wikipedia.org/wiki/Device_file_system#Naming_conventions]("http://en.wikipedia.org/wiki/Device_file_system#Naming_conventions")

IDE also has a few AHCI controller settings as well if im not mistaken but I never had issues with them other than one setting that talked about which controller was to be used (e.g. Primary, Secondary or Both) but that never killed anything unless the drive was on a deactivated controller.

I'm going to take a look and see if I can find any information about fixing broken filesystems from LiveCD to possibly salvage your setup but to be honest I'm stumped with this one.

---

### Post by warch on 2011-01-09
thanks for the honesty TechWiz.

Is there anyone else that can be directed to this thread who may be able to suggest a solution?

I do see that there are a number of experts on this forum - although they seem to be attending to threads in different sections.

---

### Post by warch on 2011-01-14
bump.....

no reply about what my choices are now to find someone else who may be able to help?

---

### Post by warch on 2011-01-14
bump.....

no reply about what my choices are now to find someone else who may be able to help?

---

### Post by warch on 2011-01-14
sorry, computer glitch, double post

---

