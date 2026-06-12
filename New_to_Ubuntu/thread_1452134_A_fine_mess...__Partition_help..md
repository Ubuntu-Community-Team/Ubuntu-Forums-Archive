---
title: "A fine mess...  Partition help."
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Nesaskewatch on 2010-04-11
While I am using Lucid, I feel this is a problem with partitioning and not a development issue.  Therefore I am posting here.  :)

I decided to try and clean up the partitions on my drive as I got a low space warning while upgrading.  After monkeying around for a while I have discovered I haven't a clue how to move partitions around!  I have read a number of tutorials, but seem to have hit the wall.  I want to consolidate the unused portions and allocate them to sda7, and perhaps eliminate one of the two swap files.  I have attached a pic of my drive in gparted.  sda1 is XP, sda5 is my development test bed (Lucid Lynx beta 2) and sda7 is my "working" ubuntu partition.  I know how to resize the partitions, but haven't the foggiest how to move them...  As I said, I want to consolidate and allocate the unused portions to sda7, and perhaps end up with one swap file.  So left to right would be sda1 (xp) sda7 (Future Lucid release) and sda5 (development test bed) then the swap file at the end?

I hope I haven't messed things up too bad...

Thanks!

---

### Post by Nesaskewatch on 2010-04-11
I should add that I have already shrunk sda1 and sda5 to the size I want using gparted from a live cd.  I just can't figure out how to move the unallocated spaces to the left and consolidate them, then allocate to sda7.

Thanks again!

---

### Post by Doctor Mike on 2010-04-11
> **Nesaskewatch said:**
> I should add that I have already shrunk sda1 and sda5 to the size I want using gparted from a live cd.  I just can't figure out how to move the unallocated spaces to the left and consolidate them, then allocate to sda7.

Thanks again!You might wan to consider making an image (or more) image backup(s) then restructuring partitions, then merging partition data (if needed) to the newly formed partitions. If you have solid image backups you can wipe everything and build anything you want... Oh verify your images first... Had a lot of extra work because of that once.

---

### Post by Nesaskewatch on 2010-04-11
> **Doctor Mike said:**
> You might wan to consider making an image (or more) image backup(s) then restructuring partitions, then merging partition data (if needed) to the newly formed partitions.

I have just this one drive I'm afraid.  This is the first time I have tried to move partitions.  It sounds so easy in the various howto's I've read, but I can't quite figger it.

---

### Post by s_ø on 2010-04-11
There is always a risk of something going wrong when you edit partitions. A common one is to delete the wrong partition...
You should backup your data,if you cant backup everything, backup the most important stuff (to cd/dvd/usb...)

To get the unallocated space outside your extended partition inside, resize sda2.
The unused swap (the one without the little key icon) can be deleted.
then resize/move the partitions one by one so all the unallocated space ends up next to sda7.

---

### Post by Nesaskewatch on 2010-04-11
Hey!  Thanks for the reply!  A few questions if I may;

> **s_ø said:**
> To get the unallocated space outside your extended partition inside, resize sda2.

So I can just select sda2 from the *list* and enlarge it all the way pretty much? (Save some for swap file size?)  *Then* I will have the option of moving them?  


> **s_ø said:**
> then resize/move the partitions one by one so all the unallocated space ends up next to sda7.

This is where I got stuck.  All I was able to do is resize them.  I am hoping that by resizing sda2 I will have the option of moving them as opposed to resizing only...?

I am asking these questions first before I actually try them with the live cd.  I will try to backup onto a dvd, but that will be a first as well.

Cheers man!

---

### Post by s_ø on 2010-04-11
> So I can just select sda2 from the *list* and enlarge it all the way pretty much? (Save some for swap file size?)
Yes enlarge it all the way, unless you need some for another primary partition (for windows or another os). Swap space can be inside the extended partition.
> *Then* I will have the option of moving them?  
To move partitions you need somewhere to move them, you cant move them into each other. You should be able to move sda5 so the unallocated space is between sda5 and sda8. Then you can move sda8 so unallocated is between sda7 and sda8.
Then resize sda7.

---

### Post by Nesaskewatch on 2010-04-11
> **s_ø said:**
> You should be able to move sda5 so the unallocated space is between sda5 and sda8. Then you can move sda8 so unallocated is between sda7 and sda8.
Then resize sda7.

Sounds like tiddlywinks!  Or maybe chess?

Thanks very much!  Easily understood.

BTW, I just downloaded Clonezilla.  I'll burn an image somewhere somehow.

I'll post the result shortly I hope.

Cheers!

---

### Post by Nesaskewatch on 2010-04-11
Well, lookie here!  (See attachment)

Thanks for the help friend!  Worked great.  I had to get rid of the swap that was "in between", and do the sda2 resize separately, but all went swimmingly well.  Maybe sometime I might be able to help you?  Who knows...  

Thanks again.

---

### Post by Nesaskewatch on 2010-04-11
I spoke too soon?  I just found out XP won't boot now!  lol  Reverts to the grub screen for selecting kernels/OS's when I select it and hit enter.  Won't let me select XP.  Everything else works great.  Perhaps I messed up Grub?  Going to search around a bit.  If anyone has any ideas...?  

Thanks!

---

### Post by Don1500 on 2010-04-11
In Ubuntu, open the terminal (accessories>terminal) 
Enter the following:
```
sudo update-grub
```
It could be that easy.

---

### Post by Nesaskewatch on 2010-04-11
> **Don1500 said:**
> 
It could be that easy.

Man was I hoping that was it?!  Blast.  Still boots me back to the list when I select xp.  The Linux systems boot up well but no xp joy.  I can mount the drive in L2, and it is still shown as boot in gparted, so it must have fubarred as I moved/resized all the rest.  I did shrink it's partition by a couple GiB's...  

It's a good guess that it is grub though right?  (I should say grub2)

---

### Post by 4Orbs on 2010-04-11
If Lucid is the most recent system you installed, then it is the one which now manages the grub2 boot loader. It is also the one you want to run the update-grub command in.

---

### Post by Nesaskewatch on 2010-04-12
> **4Orbs said:**
> If Lucid is the most recent system you installed, then it is the one which now manages the grub2 boot loader. It is also the one you want to run the update-grub command in.

I have tried the grub-update in both instances of Lucid to no effect.  Still can't boot xp.  Would this make much sense?

```
sudo mount /dev/sdax /mnt
```


For each os.  x being sda1, sda5 and sda7  Then;

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

(I found the code in another grub thread.  Thanks to tom.swartz07!)

I want to ask before doing this.

Cheers!

---

### Post by 4Orbs on 2010-04-12
That doesn't look like the thing to do IMHO. Since sda1 is the Windows bootable partition, you don't want grub on that one. The instructions you posted are, I THINK, meant for repairing grub by working from the live cd as a rescue disk.

At this point it would probably be best to just wait for one of the Ubu-gurus to come along and post a proper fix.

You might only need to run install-grub from one of the Lucid systems rather than update-grub. I think the problem arose because you shrank the Windows partition and you were unable to boot into Windows afterwards... thus Windows couldn't run it's necessary file system check which is mandatory after shrinking that partition.

Anyway, I suggest you not do anything until someone with more experience comes along and posts a REAL solution.

---

### Post by Nesaskewatch on 2010-04-12
I guess I should elaborate as to why I am waiting for advice before running the code in my previous post.  (I have also included another gparted shot of my disk for easy reference)

When I am mounting each os I want to be able to boot, should I also include sda2?  xp is sda1 and everything else is on the extended partition (sda2 includes sda5, sda7 and the swap file)  Or, should I only mount the *actual* drives?  eg; sda1, sda5 and sda7.

Thanks again for the help.

---

### Post by Nesaskewatch on 2010-04-12
> **4Orbs said:**
> Anyway, I suggest you not do anything until someone with more experience comes along and posts a REAL solution.

Excellent advice!  I have to go and tend to life for a couple hours, so, here's to doing nothing!  :lol:

Cheers!

BTW, here is my "df" output with all drives mounted;

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             70916716  23081548  44233000  35% /
none                   1281348       296   1281052   1% /dev
none                   1285500       388   1285112   1% /dev/shm
none                   1285500        92   1285408   1% /var/run
none                   1285500         0   1285500   0% /var/lock
none                   1285500         0   1285500   0% /lib/init/rw
/dev/sda5             10159580   7629940   2013560  80% /media/2f45fe74-72b0-416a-9c9e-cb9fd881a420
/dev/sda1             30716244  22780016   7936228  75% /media/00ACFFE0ACFFCDE2

fdisk -l;

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4e984e98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       14593    86501992+   5  Extended
/dev/sda5           12794       14078    10321762+  83  Linux
/dev/sda6           14079       14593     4136706   82  Linux swap / Solaris
/dev/sda7            3825       12793    72043429+  83  Linux

---

### Post by 4Orbs on 2010-04-12
Could you post a new gparted screenshot? I'd like to see the current state of the Windows partition (since you resized it). This isn't necessary if it was resized before the other screenshots were taken.

---

### Post by Nesaskewatch on 2010-04-12
Here is the most recent shot of my disk in gparted.

I just noticed that the linux swap is not mounted.  It was before I started moving and resizing.  Is that relevant here?

Thanks.

---

### Post by Nesaskewatch on 2010-04-12
I am starting to get kind of worried here.  I really need to get xp back up soon.  I am working on a customer's Jaguar and all my tech data was on there.  Not to mention that I can't run *any* of my shop CD's in Linux.  

I am thinking I must have damaged the xp MBR or bootloader when I shrank it down.  I have seen several methods for repairing xp boot, but I am worried of compounding the problem by charging ahead blind!

Your help has been, and continues to be very much appreciated!

Here is the output from the boot info script;

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 172308579 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 168266971 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   234,436,544   173,003,985   5 Extended
/dev/sda5         205,519,545   226,163,069    20,643,525  83 Linux
/dev/sda6         226,163,133   234,436,544     8,273,412  82 Linux swap / Solaris
/dev/sda7          61,432,686   205,519,544   144,086,859  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00ACFFE0ACFFCDE2                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2f45fe74-72b0-416a-9c9e-cb9fd881a420   ext3                                     
/dev/sda6        9d7a781d-0931-4d0d-a701-0906b7b78790   swap                                     
/dev/sda7        7fe67364-cd07-4ad6-a2a6-8546968ffcbd   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2f45fe74-72b0-416a-9c9e-cb9fd881a420

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=794

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-13-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-13-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.31-13-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-13-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-13-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.31-13-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.28-15-generic ...
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.28-11-generic ...
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00acffe0acffcde2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d7a781d-0931-4d0d-a701-0906b7b78790 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 107.9GB: boot/grub/core.img
 114.1GB: boot/grub/grub.cfg
 114.2GB: boot/grub/menu.lst
 114.1GB: boot/initrd.img-2.6.28-11-generic
 114.5GB: boot/initrd.img-2.6.28-15-generic
 114.5GB: boot/initrd.img-2.6.31-20-generic
 114.2GB: boot/initrd.img-2.6.32-19-generic
 114.2GB: boot/vmlinuz-2.6.28-11-generic
 114.1GB: boot/vmlinuz-2.6.28-15-generic
 114.1GB: boot/vmlinuz-2.6.31-20-generic
 114.1GB: boot/vmlinuz-2.6.32-19-generic
 114.2GB: initrd.img
 114.1GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00acffe0acffcde2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=edb7393a-e1aa-4440-9187-7e1c7e5a17c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  31.8GB: boot/grub/core.img
  32.3GB: boot/grub/grub.cfg
  46.6GB: boot/initrd.img-2.6.31-20-generic
  57.3GB: boot/initrd.img-2.6.32-19-generic
  37.9GB: boot/vmlinuz-2.6.31-20-generic
  46.5GB: boot/vmlinuz-2.6.32-19-generic
  57.3GB: initrd.img
  46.6GB: initrd.img.old
  46.5GB: vmlinuz
  37.9GB: vmlinuz.old
```

---

### Post by 4Orbs on 2010-04-12
It is a good thing that you posted the boot info results. Now, if one of the wise Ubuntu masters will just look at this thread, I feel certain that your problem can be fixed. While I think I can see where the problem is, I won't offer any advice for fear of messing things up worse by giving incorrect information. I wish there were a way of drawing more attention to this thread, but I guess that bumping it to the top of the forum every day is all that can be done until a guru comes along. Above all, don't do anything crazy out of frustration. :)

---

### Post by Nesaskewatch on 2010-04-12
> **4Orbs said:**
>  Above all, don't do anything crazy out of frustration. :)

I got myself into this mess by being impulsive!  Live and learn as they say...

Thanks for the bump!

---

### Post by ranch hand on 2010-04-12
OK, this will take some study.  I will copy the boot info to gedit for easier reading.

I would  really like you to do to things.  One is to check your /boot/grub/device-map and make sure it is right.  You may not have one at all as they are clearing it out.

Then I would like you to;
```

gksudo /etc/grub.d/40_custom

```
and copy/paste this into that file;
```

echo "Adding XP on sda1" >&2 
cat << EOF
menuentry "XP on sda1" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF

```
Save that file as  06_custom.  Get into nautilus as root and check the permissions on that file.  There is a box for making the file executable as a program that must be checked or the script will not run.

Run'
```

sudo update-grub

```
and 
```

sudo grub-mkconfig

```
and look at the results of that one carefully and make sure that the MS entry is at the top of the menu.  If not you did not get the permissions right on the 06_custom file.

Assuming it is right, just to make sure that the MBR is cleanly install upon;
```

sudo grub-install /dev/sda

```
reboot and see if it works.

If not you are going to have to recover the MS boot loader.  Do not look to me for help on that.  Haven't a clue and do not want one (yes there is a little hostility toward that fine bunch here).

Then you can re install grub on the MBR  from your live CD.

You might want to check both your /etc/fstab files to make sure they match your new partition table.  I haven't gotten that far yet.

Give the custom entry a whack and see if it helps.

---

### Post by 4Orbs on 2010-04-12
As for the swap not being mounted... In my experience, this always happens when you resize a linux partition. It can be easily fixed by editing the fstab file. However, I don't believe that is what is preventing you from succesfully booting into Windows.

---

### Post by Nesaskewatch on 2010-04-12
Wow.  Thanks guys.  I'm going to start working through Ranch Hands directions and post back asap.  Might take a bit.  

Thanks again.

---

### Post by Nesaskewatch on 2010-04-12
> **ranch hand said:**
> I would  really like you to do two things.  One is to check your /boot/grub/device-map and make sure it is right.  You may not have one at all as they are clearing it out.

This is all that is within device.map on sda7;

(hd0)	/dev/sda

It's the same within sda5.  Both sda5 and sda7 are the linux partitions.  I'm going to edit this entry as I go along.

One question I have is does it matter which partition I am in when I do this?

---

### Post by egalvan on 2010-04-12
> **ranch hand said:**
> 

If not you are going to have to recover the MS boot loader.  Do not look to me for help on that.
  Haven't a clue and do not want one
 (yes there is a little hostility toward that fine bunch here)..

well, I have more than a "little" hostility... :)

Never-the-less, SuperGrub will recover your MS boot loader presto-change'o.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

it's all but automatic...
And if it saves your bacon (or your job), then please consider a donation to the authors of supergrub.


(messing up MS's boot loader is easy, and fun.

so is fixing it...)

---

### Post by 4Orbs on 2010-04-12
> I'm going to edit this entry as I go along.
Just a suggestion... Some of us rely on email notifications to tell us when a thread has new activity on it. We don't get those emails if you only edit an existing post. So a new post will probably get a quicker response for you.

---

### Post by ranch hand on 2010-04-12
That is what we want to see in the device map.

The easiest thing to do is do this from your 10.04 install as that is where you have your grub information.  One of the great improvements in the new grub is the ability to do everything from where it lives instead of having to use a live CD (unless you can't boot at all).

---

### Post by 4Orbs on 2010-04-12
Ranch Hand... both of his Ubuntu installs are ver 10.04.

---

### Post by Nesaskewatch on 2010-04-12
> **ranch hand said:**
> Then I would like you to;
```

gksudo /etc/grub.d/40_custom

```
and copy/paste this into that file;
```

echo "Adding XP on sda1" >&2 
cat << EOF
menuentry "XP on sda1" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF

```

When I put "gksudo /etc/grub.d/40_custom" into terminal, I get this;
  
dave@dave-laptop:~$ gksudo /etc/grub.d/40_custom
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
dave@dave-laptop:~$ 

I am confused...  Where do I add lines?  I was expecting a file to open.  This merely appears in terminal.

Thanks.  And sorry for being so green at this.

---

### Post by 4Orbs on 2010-04-12
Since I'm already here, I'll butt in just to save a little time. The command should be:
```
gksudo gedit /etc/grub.d/40_custom
```
That will open the file in the text editor.

---

### Post by ranch hand on 2010-04-13
> **4Orbs said:**
> Ranch Hand... both of his Ubuntu installs are ver 10.04.

From the boot info script;
```

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

```

---

### Post by 4Orbs on 2010-04-13
oops! How could I have missed that?

---

### Post by ranch hand on 2010-04-13
> **Nesaskewatch said:**
> When I put "gksudo /etc/grub.d/40_custom" into terminal, I get this;
  
dave@dave-laptop:~$ gksudo /etc/grub.d/40_custom
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
dave@dave-laptop:~$ 

I am confused...  Where do I add lines?  I was expecting a file to open.  This merely appears in terminal.

Thanks.  And sorry for being so green at this.
Heck you could just open a new file (as root) in gedit or just replace every thing with this header and your entry;
```

#!/bin/sh
# This file is an example on how to add custom entries

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF

```
from my custom menu.

You may want to edit the partition designations in my entry and try it for one of your installs.  Never needs updating.  Boots to the newest kernel on the partition called for.

I think all you really need is a file with the right kind of entry format and the right permission checked.

You could just put your entry in the 40_custom file below the other stuff.  I skip a line to make reading easier.

---

### Post by Nesaskewatch on 2010-04-13
> **ranch hand said:**
> From the boot info script;
```

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

```

This is interesting...  I *should* have *two* instances of 10.04.  Weird...  It is shown as 9.10 there though.  

Back to work!  I had to take out the trash and set up the barbie for the Mrs.

---

### Post by Nesaskewatch on 2010-04-13
OK.  Here is the output from terminal for most of that;

```
dave@dave-laptop:~$ gksudo gedit /etc/grub.d/40_custom
dave@dave-laptop:~$ sudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

^C      
dave@dave-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda5
done
dave@dave-laptop:~$ sudo grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding XP on sda1" >&2 
cat << EOF
menuentry "XP on sda1" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Microsoft Windows XP Professional on /dev/sda1
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00acffe0acffcde2
	drivemap -s (hd0) ${root}
	chainloader +1
}
Found Ubuntu lucid (development branch) (10.04) on /dev/sda5
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
done
dave@dave-laptop:~$
```

Looking good?  Just want to check before I proceed with this;

> Assuming it is right, just to make sure that the MBR is cleanly install upon;
Code:

sudo grub-install /dev/sda

reboot and see if it works.

If not you are going to have to recover the MS boot loader. Do not look to me for help on that. Haven't a clue and do not want one (yes there is a little hostility toward that fine bunch here).

Then you can re install grub on the MBR from your live CD.

You might want to check both your /etc/fstab files to make sure they match your new partition table. I haven't gotten that far yet.

Give the custom entry a whack and see if it helps.

---

### Post by Nesaskewatch on 2010-04-13
Well, I have a new entry in the menu for "xp on sda1", however, it still won't boot.  There is the old entry that also does not work.  I just get put back to the menu.  All the Linux drives work.  I guess the xp MBR is hooped.  

Darn.  I guess it's late, so I'll take this up again in the am.

Thanks guys.  I really appreciate your help.

Manana!

---

### Post by 4Orbs on 2010-04-13
That's a bummer. There are a couple of items in your boot info that seemed odd to me. First is that sda1 appears to have grub installed in that partition. I don't think that should be there but I'm not knowledgeable enough about grub to speak in absolutes. So this question: When you boot from the old grub entry to XP, and it returns to the menu... is that menu that you return to the "New" grub menu that has two entries for XP?

Second question: Did you perhaps use the Wubi installer (from inside Windows) to install one of your Ubuntu systems?

---

### Post by ranch hand on 2010-04-13
How about a new results from the boot script?

You really ought to get rid of some of those old kernels.

I bet if you look at the system monitor on your 10.04 you will see that there is no swap.

From the sda7 fstab;
> 
# swap was on /dev/sda8 during installation
UUID=edb7393a-e1aa-4440-9187-7e1c7e5a17c7 none            swap    sw              0       0

I would change that to;
> 
# swap was on /dev/sda8 during installation
## UUID=edb7393a-e1aa-4440-9187-7e1c7e5a17c7 none            swap    sw              0       0
/dev/sda6         none            swap    sw              0       0
[

---

### Post by tad1073 on 2010-04-13
At this point, it seems easier to just reinstall 10.04, which should pick up xp and your other ubuntu install.

The time spent trying to fix grub2 you could have reinstalled and set-up 10.04 to the same state.

---

### Post by ranch hand on 2010-04-13
That will not fix the boot loader for the MS install.  Grub chain loads to it and it appears not to work.

Reinstalling to use os-prober is a little over kill.  Just running update-grub should do it.  There have been (I think it is pretty well straightened out now) a number of incidents of grub not picking up MS on installation.  In about 95% of those cases all that was required was to update-grub from the new install.

---

### Post by Nesaskewatch on 2010-04-13
> **ranch hand said:**
> How about a new results from the boot script?

You really ought to get rid of some of those old kernels.

I bet if you look at the system monitor on your 10.04 you will see that there is no swap.

From the sda7 fstab;

I would change that to;

I was wondering about that as well.  Not that I knew anything, but it seemed odd.  Before I messed things up it had 2 swaps.  I wonder if the swap needs to be right next to both linux partitions?  I realized this am that I had not done the fstab mods you mentioned.  I'm going to try and do what you suggested  and see what happens.  I will throw up a new boot script. in a minute.  I'm also going to make sure the permissions were set correctly on that 06_custom script.  I'm thinking it must be alright if it added a new line to the menu...  

Back in a minute.

Oh, and good morning!  :)

Here is the new boot info;  ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 172308579 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 168266971 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   234,436,544   173,003,985   5 Extended
/dev/sda5         205,519,545   226,163,069    20,643,525  83 Linux
/dev/sda6         226,163,133   234,436,544     8,273,412  82 Linux swap / Solaris
/dev/sda7          61,432,686   205,519,544   144,086,859  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00ACFFE0ACFFCDE2                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2f45fe74-72b0-416a-9c9e-cb9fd881a420   ext3                                     
/dev/sda6        9d7a781d-0931-4d0d-a701-0906b7b78790   swap                                     
/dev/sda7        7fe67364-cd07-4ad6-a2a6-8546968ffcbd   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2f45fe74-72b0-416a-9c9e-cb9fd881a420

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=794

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-13-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-13-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.31-13-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-13-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.31-13-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.31-13-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro vga=794
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		2f45fe74-72b0-416a-9c9e-cb9fd881a420
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.28-15-generic ...
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	echo	Loading Linux 2.6.28-11-generic ...
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00acffe0acffcde2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d7a781d-0931-4d0d-a701-0906b7b78790 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 107.9GB: boot/grub/core.img
 114.1GB: boot/grub/grub.cfg
 114.2GB: boot/grub/menu.lst
 114.1GB: boot/initrd.img-2.6.28-11-generic
 114.5GB: boot/initrd.img-2.6.28-15-generic
 114.5GB: boot/initrd.img-2.6.31-20-generic
 114.2GB: boot/initrd.img-2.6.32-19-generic
 114.2GB: boot/vmlinuz-2.6.28-11-generic
 114.1GB: boot/vmlinuz-2.6.28-15-generic
 114.1GB: boot/vmlinuz-2.6.31-20-generic
 114.1GB: boot/vmlinuz-2.6.32-19-generic
 114.2GB: initrd.img
 114.1GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding XP on sda1" >&2 
cat << EOF
menuentry "XP on sda1" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	echo	Loading Linux 2.6.32-19-generic ...
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 7fe67364-cd07-4ad6-a2a6-8546968ffcbd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00acffe0acffcde2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.32-19-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-15-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, with Linux 2.6.28-11-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2f45fe74-72b0-416a-9c9e-cb9fd881a420
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=2f45fe74-72b0-416a-9c9e-cb9fd881a420 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=edb7393a-e1aa-4440-9187-7e1c7e5a17c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  31.6GB: boot/grub/core.img
  33.7GB: boot/grub/grub.cfg
  46.6GB: boot/initrd.img-2.6.31-20-generic
  57.3GB: boot/initrd.img-2.6.32-19-generic
  37.9GB: boot/vmlinuz-2.6.31-20-generic
  46.5GB: boot/vmlinuz-2.6.32-19-generic
  57.3GB: initrd.img
  46.6GB: initrd.img.old
  46.5GB: vmlinuz
  37.9GB: vmlinuz.old
```

---

### Post by Nesaskewatch on 2010-04-13
> **ranch hand said:**
> I bet if you look at the system monitor on your 10.04 you will see that there is no swap.

Do I need to do the fstab mod as root?  Or do I save it with a new name?  (This is another first for me)  I don't seem to be able to save the change unless I "save as"

Cheers!

I just noticed the fstab in gedit is "read only".  I guess I need to change permissions?  I would do that with Nautilus in root correct?

---

### Post by oleink on 2010-04-13
If he is adding memory to a location and not removing any from a partition he should not lose data...

---

### Post by ranch hand on 2010-04-13
You do need to be root to change the fstab file as you are making changes to your system that will effect performance.
```

sudo gedit /etc/fstab

```
The position of swap is not real important as far as the OS is concerned.  The thing here is that this OS is looking for swap where there is no swap partition anymore.

Editing the the fstab file should get it looking where it is supposed to.

I move partitions (copy/paste) from drive to drive with gparted.  As long as they are going into the same numbered partition on the new drive  and their /home partition is on the same numbered partition and swap is on the same numbered partition, every thing is cool.  Any change in that requires editing the fstab file so that the OS will work.

I think this is why folks use things like clonezilla to move from drive to drive.  I think that re writes the fstab.  I don't use it as;
A>I like to know what an app is doing so I need to learn to do it myself first
B>I do not like the idea of someone elses script messing with my files
C>Third party apps to run your box is just too damned much like "running" MS

I switched to Linux so I could actually run my box.  Got a lot to learn but it is FUN.

---

### Post by Nesaskewatch on 2010-04-13
Now sda7 wont boot!  Hangs at the ubu splash screen.  lol  I am now on sda5.  (2 down, 1 to go!)  I guess I should have confirmed the fstab change before leaping in...  I am hoping I can go in from this partition and remove that line I added to sda7's fstab.  Can I use nautilus from sda5 to change the fstab in sda7?  

Cheers!

---

### Post by 4Orbs on 2010-04-13
Nesaskewatch: Would you do one small test that will only take a minute? I'm assuming you still show two XP entries on the grub menu.

Please boot to grub and select the old, original XP entry. Then when it returns you to the grub menu, click the XP entry again. If, by some miracle, it does boot into Windows... allow Windows to complete the file system check before rebooting.

---

### Post by Nesaskewatch on 2010-04-13
> **4Orbs said:**
> Nesaskewatch: Would you do one small test that will only take a minute? I'm assuming you still show two XP entries on the grub menu.

Please boot to grub and select the old, original XP entry. Then when it returns you to the grub menu, click the XP entry again. If, by some miracle, it does boot into Windows... allow Windows to complete the file system check before rebooting.

I actually tried that when you first suggested it.  Sorry I didn't mention it...  I did it again a minute ago to see if it changed but no go.  

I did manage to repair sda7's fstab from sda5 by mounting it while I was root.  I'm back in sda7 now.  I just removed the line I added and restored it to original.

---

### Post by ranch hand on 2010-04-13
> **Nesaskewatch said:**
> Now sda7 wont boot!  Hangs at the ubu splash screen.  lol  I am now on sda5.  (2 down, 1 to go!)  I guess I should have confirmed the fstab change before leaping in...  I am hoping I can go in from this partition and remove that line I added to sda7's fstab.  Can I use nautilus from sda5 to change the fstab in sda7?  

Cheers!
Wow, that should not have happened.  But yes you can do that in nautilus as root.

EDIT
Just saw your last post.  Great.

Gave myself a dope slap.

---

### Post by ranch hand on 2010-04-13
I do not think that you are going to have any luck booting to MS without doing something about its boot loader;
> 
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 172308579 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

I do not think that bit about grub being installed on sda1 is not right, I think.  Don't chain load or boot to MS so I am not sure.

I hope I am wrong.

---

### Post by Nesaskewatch on 2010-04-13
Copy that.  I have to bolt for a bit on important bidness.  I'll be back soon.

Thanks folks!

---

### Post by 4Orbs on 2010-04-13
While you are away, I'll grab the opportunity to voice my admiration for your stamina and ranch hand's expertise. Had it been my fubarred system, I would have given up yesterday and just repaired the MBR using SuperGrub or the XP installation cd... then install the 10.04 Lubuntu beta. Anyhow, troubleshooting is still great fun.

---

### Post by oleink on 2010-04-13
Yeah you are doing a good job sticking in there!:popcorn:

---

### Post by Nesaskewatch on 2010-04-13
Well, I'm back.  I have been reviewing my situ and have come to the conclusion that I am really hooped...  I suppose I am looking at recovering the MBR for xp.  As I said, I have a lot of things that could not be backed up on my xp install and am really hoping to recover it.  

I guess I should start searching for; "recover xp mbr without destroying anything else" and; "Loser".  I recall seeing something in here that explained the steps for recovering the mbr in xp.  

And 4Orbs, it is fun to troubleshoot linux.  It's like learning Japanese from a Russian that only speaks Urdu.  Badly.  

If anyone would care to point me at something even vaguely like a solution, feel free!  I'll just sit here and learn how to play the banjo for money.  

Cheers!

---

### Post by ranch hand on 2010-04-13
You should be able to copy every thing on your XP install even if you can't read it.  Just make sure you have all the ntfs and fat support installed and have a fat or ntfs (which ever XP uses) partition in which to put it.

If you have a XP install disk there should be a function on it to fix your MBR.

 I am not sure who it was but some kind soul here  mentioned restoring the MS bootloader with the super grub disc.  This may be the case, have not looked at it for some time.  You may want to get it and see what it says.  The site may give a clue.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by 4Orbs on 2010-04-13
egalvan's post on page 3 of this thread will point you to SuperGrub website. I've never used SuperGrub, but I've seen that many people absolutely are in love with it. I have used the XP install disk to repair my MBR one time and if I recall correctly, it only took a few minutes.

Be aware that when you repair the MBR, you will lose access to your Ubuntu (because grub gets removed). You can re-install grub afterwards by using the Ubuntu live cd, but that could potentially re-introduce the problems you've attempted to fix here. I would very much like to see a follow up post by you relating what the eventual conclusion might be. You know, closure heals a fried brain. Mine got fried just following this thread. Best of luck.:guitar:

---

### Post by ranch hand on 2010-04-13
I think we can safely get grub back on after fixing the MS boot loader but that has to be fixed first.

The install disk would be my choice too if it is available.

---

### Post by Nesaskewatch on 2010-04-13
I have just spent two hours hunting high and low and cannot find my xp cd...  It has the product key on the case.  

...

I am going to try and find an xp iso for download, but I'm not sure if I can burn one in Linux.  I guess I'll find out.

---

### Post by Nesaskewatch on 2010-04-13
Ya right.  I have been using ubu for so long now that I forgot about that whole software costing money thing.  I guess I'm screwed.

---

### Post by Nesaskewatch on 2010-04-13
I found it!  I was rooting around for some slugs for the shotgun, and found it!  :wink:

I think I have the fixmbr.exe thing figured so I'll go ahead and do it then hopefully check back from inside xp. 

Any issues I should watch for?

---

### Post by ranch hand on 2010-04-13
Well I would give the SG disk a look.  The little looking I did at the site was kind of confusing but there was mention of one for windows.   I think that you can install lillo on MS and have it boot.

I am looking for help on that.  Don't panic yet.

---

### Post by 4Orbs on 2010-04-13
> I guess I'm screwed.
Well, I disagree. You COULD spend a couple more hours creating a storage partition from the unallocated space on your HDD and format it to NTFS, then use pysdm (storage device manager) in Ubuntu to mount the storage partition and easily change permissions, then copy all your most important files from the Windows partition over to the storage partition (of course you'd need to mount the Win partition in Ubuntu too). Then you could use SuperGrub to repair the MBR without fear of losing the important files you've put on the storage partition. Even if you completely destroy the Win and Ubuntu systems... the storage partition is still safe and you'd only need to re-install some OS to access that.

EDIT:
Uh-oh! Disregard that. I see you don't have any unallocated space left on the HDD.

EDIT #2:
But it's still a good idea, even if you get everything fixed.

---

### Post by oleink on 2010-04-13
results yet?  I hope it worked:)

---

### Post by Nesaskewatch on 2010-04-13
Weird.  I ran fixmbr, and it claimed to have written a new mbr, but xp still won't boot, and grub still appears to be working fine.  Linux hasn't changed at all.  I then went back into recovery and ran chkdsk /r just for the hell of it and it again claimed to have fixed errors, but still no go.  I am wondering if when I resized xp I somehow moved some files that "cannot be moved"?  There is another command in recovery that I think was fixboot or something like that.  Maybe I should try that?  Amazing how I have forgotten so much about windows.  I used to be pretty good at wrecking xp.

Ideas?

---

### Post by 4Orbs on 2010-04-13
???... Grub shouldn't even be there anymore. It must be booting into that mysterious grub that is installed inside the Windows partition.

---

### Post by Nesaskewatch on 2010-04-13
Fixboot worked!  I am now in xp!!  (Man.  Is that a weird thing to be happy about!)  I guess it's now just a matter of fixin grub up eh?

Would a simple
 
```
sudo update-grub
``` 

work?

Cheers very much you guys!  I'm thinkin' I'm on the home stretch!

:P

Of course updating grub won't work!  I have to get into it first!  How about booting into the live cd, then update grub?

---

### Post by ranch hand on 2010-04-13
This is great.  Maybe I can sleep tonight.

You need to follow these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring the editing files part as "update-grub" will take care of that and the "grub-install /dev/sda" should put grub back on your MBR.

Do not add a partition number to the "sda".  That, I think, is what happened to you MS boot sector.  Just a plain "sda" is what we want here.

This should do it.

---

### Post by Nesaskewatch on 2010-04-13
Roger that.  I have 2 partitions with 10.04, and the primary is xp.  Where it says;

> $ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt 

$ sudo mount /dev/sda1 /mnt

    * If you have /boot on a separate partition, that need's to be mounted aswell. For reference, /dev/sda2 will be used. 

$ sudo mount /dev/sda2 /mnt/boot Make sure you don't mix these up, pay attention to the output of FDISK

    * Now mount the rest of your devices 

$ sudo mount --bind /dev /mnt/dev

I don't want to list sda1 here right?  I only want sda5 and sda7, correct?  Does the swap need to be included?  Does it matter which is boot?  I'm a bit confused...  To be safe, would you mind taking a boo at the pics of my drives posted previously and confirm what I should enter here?  I don't have those pics on this os.

Cheers!

I hope I caught this in time.  How about I do this;

```
sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda5 /mnt
sudo mount /dev/sda7 /mnt
```

Then I enter

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Would that work OK?

---

### Post by ranch hand on 2010-04-13
NO.  You only want sda5.  What you are doing here is establishing a remote control of your OS that you want to supply the menu.

What they are talking about is if you have your OS installed on 2 (or 3) partitions and one of those is a boot partition.  You do not have that.

When you get to the grub-install command is where you just want sda and no number at all.

---

### Post by Nesaskewatch on 2010-04-13
To clarify, I do this;

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub
grub-install /dev/sda
```

Does that look OK?

---

### Post by ranch hand on 2010-04-13
Perfect.

I should be more clear too.  You could just use sda7, your 9.10 istall but then you would be on grub0.97 and the commands ore different and probably will not work from the 10.04 Live CD because it does not have that grub on it.

Just go with the commands you have in your post.

---

### Post by Nesaskewatch on 2010-04-14
OK folks.  It's all good now.  All partitions (except the swap while in sda7) are working fine now.  I ran the commands as shown, and there was grub.  Just had to run sudo update-grub from inside sda5 and there popped up sda7.  Fantastic results!  

I'm going to try and summarize this odyssey from what went wrong through to what fixed it.  Worth it I think.  I did get quite a spiel of "/poc/devices: fopen failed: No such file or directory!" and "grep: /proc/mounts: No such file etc..."  after I entered update-grub, and after grub-install /dev... etc.  But I just ignored the errors and pressed on to victory!

I can't thank you guys enough for all the help and cajoling.  I got to being pretty down on the whole mess a bit earlier today, but I took your advice and beat the bugger!  

Cheers very much all.  Now on to swap file repairs!

:)

---

### Post by 4Orbs on 2010-04-14
I've heard rumors that sometimes you can fix Windows by simply hitting the computer with a hammer.

---

### Post by ranch hand on 2010-04-14
All I can say is the guy has stamina.

Geeze am I glad that is over.

I think he needs to pat himself on the back a couple times at least.

I am going to have a beer.

---

### Post by 4Orbs on 2010-04-14
> I am going to have a beer. 
Bill Gates should send you a six pack. And pizza.

---

### Post by ranch hand on 2010-04-14
I wouldn't trust the stuff.

---

### Post by mikodo on 2010-04-14
What a great read. It was enlightening to see the spirit and fortitude of Ubuntu people helping each other, with such good humour at the end of it all!

---

### Post by oleink on 2010-04-14
MAN YOU GUYS ARE GREAT haha.  You need some kind of reward

---

### Post by Nesaskewatch on 2010-04-14
I thought long and hard about the hammer solution, and believe me when I say that more than once I considered just giving up and wiping everything and starting again.  But I must state most clearly that this was **all** due to my own fiddling with something I should have spent much more time understanding *prior* to doing it.  Were I a more impulsive individual, this laptop would have been in a lot of tiny pieces right now.  However, that would have been a shameful waste of a perfectly good machine that never intended to bother anyone in its life!  One of the best things about Linux is the ability to control, and permanently change, virtually everything it does.  The very thing that makes Linux so good turned out in my case to be its undoing.  Sometimes the most difficult thing to understand with Ubuntu is that **very little knowledge can be a very dangerous thing.**  This kind of worries me, as in my many years as a journeyman mechanic, I always hammered home to my apprentices to be certain that they are not *causing* more damage than they are being paid to fix.  In this case I completely failed to listen to my own advice.

If there is one thing I am going to take away from here, it is this: **Take the time to fully understand what you are doing *before* making _any_ changes!**

Hi.  My name's Dave, and I'm an Ubuntuholic.

Hats off you guys.  Nice work.  

(Forensic analysis to follow soon.  *If* I can figger it out)

---

### Post by ranch hand on 2010-04-14
Nah, screw it up.  Best way to learn.

If you can get an external drive it is nice to have an install that can't hurt you that you can play with.  This will work with an external as long as you can turn off the internal drive.

Right now I am on my test platform (spend most of my time here) running 10.04.  My internal drives are "off" so that there is no way I can screw up my "real" installs.

I learned about multi booting the first week I had Hardy (first linux) installed bucause I have an unreasonable wife.

I broke Hardy past my ablity to fix it 5 time s the first week playing with it.  It was so FUN.  The wife was not amused.  She thinks the computer should work.

I installed a second Hardy just to experiment on.  Did nothing to the "main" until it past the second install and that included updates.

Still have that first Hardy on here too.  Works great.

---

### Post by egalvan on 2010-04-14
> **ranch hand said:**
> I think this is why folks use things like clonezilla to move from drive to drive.

Generally, clonezilla is a little easier to use.

since partitions should be un-mounted in order to cleanly clone them,
then booting with a gparted cd or clonezilla cd is more or less the same. Clonezilla just provides a few more options, such as cloning entire drives at once, and using the LAN.

>  I think that re writes the fstab.

No, clonezilla does NOT touch the fstab.

>   I don't use it as;
A>I like to know what an app is doing so I need to learn to do it myself first

Knowing what is going on is an excellent way of keeping your OS and data safer.
Although I'm a bit confused as to what "doing it myself first" means...
Does this mean you have used "dd" to move the bits, and then did a direct fix to the partition table to reflect the changes?
(I greatly admire your software skills, and have no doubts that you could do this...seriously)

> B>I do not like the idea of someone elses script messing with my files
So you have changed *all* the scripts in Ubuntu to ones you wrote yourself?
Again, I'm confused as to the meaning of this...


> 
C>Third party apps to run your box is just too damned much like "running" MS

Even more confusing...

Ubuntu, and indeed 100% of Linux/Unix is composed of "third-party apps".
Or are you saying that Cannonical wrote ALL of Ubuntu?


Clonezila is not a program...
Clonezilla could be termed a "distro"...
It is Open Source GPL, and it uses Open Source GPL apps to do it's work.
See the project pages.

gparted is an Open Source GPL GUI "frontend" that uses the Open Source GPL project known as "parted" to do it's work.
See the project pages.

By contrast, most everything Microsoft uses is closed-source, proprietary, copy-righted, patented DRM'ed and "Intellectual Property" protected.

As I said, I'm confused as to where your concerns about clonezilla and others is coming from.
But I only have your written words, so I may have misunderstood something, somewhere.

> I switched to Linux so I could actually run my box.  Got a lot to learn but it is FUN.

Yep, it's mighty fun.
And I think that as long as it is Open Source, GPL, it's OK by me.
I don't even mind donating some $$ to the authors,
which I encourage everyone to do,
and I do it on a regular basis.

And to close this....

**It's YOUR CHOICE as to how and what you run on your machine**

which is the greatest strength in the OSS/FOSS/GNU/GPL Community.
:guitar:

---

### Post by Nesaskewatch on 2010-04-16
> **4Orbs said:**
> That's a bummer. There are a couple of items in your boot info that seemed odd to me. First is that sda1 appears to have grub installed in that partition. I don't think that should be there but I'm not knowledgeable enough about grub to speak in absolutes. 

This turned out to be the clue that eventually made everything clear.  When I first upgraded sda5 from 9.10 to 10.04, I was given a choice of where to install the new grub. (10.04 has a new version)  When I moused over the check boxes to select where to put grub, a pop up information box opened that says to install grub to all on the list if you are unsure where to put it.  I *was* _very_ unsure!  I selected all.  That was when this whole mess started.  Had I fully understood what was happening, I would have never installed grub to the windows partition.  All the resizing and moving went perfectly fine as it turns out.  It was the updater installing grub to windows (at my direction due to a lack of understanding) that messed things up.  I would merely have had to update-grub had I not installed grub all over the place!  Another mistake I made was not checking if all the os's were functioning before moving on.  I might have caught the problem much sooner had I made sure everything was ok.  

I am going to post much the same thing in the Lucid development forum as well.  I have not seen much warning about this issue (if it is indeed an issue)  Might be a good idea to make it clear *not* to ever install grub to a windows partition; that is unless you really want to for some reason!  Believe it or not, I had no idea that I shouldn't...

Again, thanks for all the help.

---

### Post by Nesaskewatch on 2010-04-16
Just one last thing.  _[This]("http://articles.techrepublic.com.com/5100-10878_11-6031733.html")_ (link) is a good place to go if you need to fix a windows boot sector or mbr.  In my case it was simply a matter of booting into the xp disk and running fixboot.exe from the recovery console.  There are other less intrusive methods at that link as well.  Useful for us chronic windows users.

Excelsior!

---

