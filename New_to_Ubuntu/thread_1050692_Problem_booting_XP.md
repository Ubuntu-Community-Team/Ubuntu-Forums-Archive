---
title: "Problem booting XP"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by SquirrelyDirge on 2009-01-25
So yeah, last night I managed to get Ubuntu installed and really it's quite nice. There's an amazing amount of orange but it's not blinding or anything so it's fine.

My problem is as follows. I have two harddrives connected in my comp. Ubuntu is installed on the Primary Master harddrive, an 8o GB Western Digital. I have Windows XP installed on the Secondary Master hardrive, 4o GB Maxtor. I'm -trying- to configure the computer to give me the option of booting either OS, and so far that's worked out great with GRUB giving me the option after the comp is powered on. As of now, ubuntu seems to work without any problems (well a minor sound issue, but that's for another time). However, whenever I try to boot Windows XP, I'm taken to the safe mode selection screen. Then, regardless of whichever mode I choose, the computer restarts and I'm returned to GRUB. I'm entirely new to this whole...thing and really haven't a clue what I'm doing. Could someone please offer their assistance?

Computer- Dell Dimension 43oo

---

### Post by Hospadar on 2009-01-25
I suspect it's a problem with your windows installation.  If windows is getting to the safe mode selector then I'd assume the windows drive has gotten to the point where it is booting, at which point grub and ubuntu no longer have anything to do with the process.

I'd ask a couple questions)

1) can you access your windows drive from ubuntu?  If you can see the drive in the file browser in ubuntu, but can't actually access it (or perhaps if you can't see it at all) it might be a sign something is wrong with your windows drive (the file system got messed up somehow maybe)

2) if you unplug your ubuntu drive, what happens?  same basic deal? if windows boots up fine now, I suppose there is some issue involving linux, perhaps involving physical drive setup, maybe try swapping drives so windows is the primary master.

To solve your problem I would try:

Doing a repair on your windows installation with a windows install cd - do this with the ubuntu drive unplugged.  windows has a nasty habit of overwriting the boot partition on the primary master

If you swap drives, you may have to reconfigure grub - go to the community docs link in my sig and search for "reinstall grub"  you'll find a helpful page.  It involves a livecd and some command line action, but nothing too bad.  just read carefully and ask questions here if you have them.

It is possible (though it seems unlikely from the problem you described) that your windows boot loader got messed up.  Some googling will turn up all kinds of pages on how to restore your windows bootloader (ntldr).  I think that as above, unplugging your ubuntu drive while doing this could save a lot of potential hassle

---

### Post by SquirrelyDirge on 2009-01-26
I can access the files on the Secondary just fine since I just copied a bunch of media files over to the Primary. I'll try running just XP when I get the chance but it actually raises another question. 

When I installed XP, I had swapped pulled out my current Primary Master and plugged my Secondary in as the Primary. So XP was installing itself on what was at the time the Primary drive. I have since moved it back to to the Secondary slot. Could that be cause for my problem?

Just a small note, after installing XP, that is while it was the Primary, it was running just fine. I don't know about now since I've I've installed Ubuntu. I'll have to check again.

---

### Post by lisati on 2009-01-26
<possible red herring>
I don't know about Dells, but some Compaq machines (including some with AMD64 cpus) have an ellergy to having XP SP3 installed - the Compaq/HP website have a patch. There's another update which messes with the ability to configure the "interactive" buttons (a patch is available for this one)

Thought: are there any updates to XP that could be causing problems?
</possible red herring>

---

### Post by SquirrelyDirge on 2009-01-26
Oh, I should probably point out what I'm using exactly...

Primary- Ubuntu 8.1o 32bit
Secondary - Windows XP Pro SP2

If that helps any.

---

### Post by hyper_ch on 2009-01-26
post teh output of
```

sudo fdisk -l

```

```

df -h

```

```

cat /boot/grub/menu.lst

```

---

### Post by caljohnsmith on 2009-01-26
I think it would help to get a clearer picture of your setup related to booting Windows, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by SquirrelyDirge on 2009-01-28
> sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x224f224e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9542    76646083+  83  Linux
/dev/sda2            9543        9729     1502077+   5  Extended
/dev/sda5            9543        9729     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b1b8b1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4982    40017883+   7  HPFS/NTFS

```

> df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  4.5G   64G   7% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  104K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.7M  249M   2% /dev
tmpfs                 251M  500K  251M   1% /dev/shm
lrm                   251M  2.0M  249M   1% /lib/modules/2.6.27-9-generic/volatile

```

> cat /boot/grub/menu.lst
```
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
default		0

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e

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
# defoptions=quiet splash

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by SquirrelyDirge on 2009-01-28
And here is the Results.txt information.

> sudo bash ~/Desktop/boot_info_script*.sh
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x224f224e

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  153,292,229  153,292,167  83 Linux
/dev/sda2        153,292,230  156,296,384    3,004,155   5 Extended
/dev/sda5        153,292,293  156,296,384    3,004,092  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b1b8b1b

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63   80,035,829   80,035,767   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f2af36d6-9344-4ae8-bd11-4f87abb9ab2e" TYPE="ext3" 
/dev/sda5: UUID="827bfd2b-bb94-401a-b62c-56801f1e31b3" TYPE="swap" 
/dev/sdb1: UUID="3644A46644A42A97" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fi)

=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e

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
# defoptions=quiet splash

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f2af36d6-9344-4ae8-bd11-4f87abb9ab2e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f2af36d6-9344-4ae8-bd11-4f87abb9ab2e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=827bfd2b-bb94-401a-b62c-56801f1e31b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  24.6GB: boot/grub/menu.lst
  24.5GB: boot/grub/stage2
  23.8GB: boot/initrd.img-2.6.27-7-generic
  23.8GB: boot/initrd.img-2.6.27-9-generic
  23.5GB: boot/vmlinuz-2.6.27-7-generic
  23.7GB: boot/vmlinuz-2.6.27-9-generic
  23.8GB: initrd.img
  23.8GB: initrd.img.old
  23.7GB: vmlinuz
  23.5GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-28
From the script output, everything looks in order to boot Windows from Grub, so I think you probably have a Windows problem and not a Grub problem at this point. If your BIOS offers you the choice of which HDD to boot on start up, either via a quick boot menu by pressing F10/F12 or some key like that, or you could also change the BIOS boot order to boot the Windows drive first, I think you will experience the same Windows problems when booting the Windows drive directly. To try and fix Windows, I would suggest booting your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try booting Windows again and let us know if anything changes. We can work from there if you want.

---

### Post by GepettoBR on 2009-01-28
I'd say that the problem is with Windows not being in the primary drive. Windows MUST be the first partition of the first drive in order to boot correctly, in my experience. Luckily for you, GRUB is very powerful and can trick Windows into thinking it's the primary even if it isn't.

Open a Terminal, backup and edit your /boot/grub/menu.lst file as root ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup && gksudo gedit /boot/grub/menu.lst
```

Find the entry for Windows near the end of the file. Mine looks liek this: ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
chainloader	+1
```

Pay attention to that number (hd0,0) since yours is different, probably (hd1,0).

All you have to do is add three lines that will swap the two drives before chainloading windows' bootloader, fooling it into believing that it's the primary drive. Add them between the "root" and "savedefault" lines.

```
map (hd0) (hd1)
map (hd1) (hd0)
liveswap
```
That's it. Save, exit and try booting into Windows to see if it works.

---

### Post by caljohnsmith on 2009-01-28
**GepettoBR**, you might want to read through the results of the Boot Info Script that SquirrelyDirge posted, because he/she is all ready using the correct mapping lines with Grub:
[QUOTE=SquirrelyDirge]```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
[/QUOTE]
And to my knowledge, there is no "liveswap" Grub command. Do you have any references for that? I would be interested to learn more about it if you do. Thanks in advance.

---

### Post by sadaruwan12 on 2009-01-28
Hi Bro,
> When I installed XP, I had swapped pulled out my current Primary Master and plugged my Secondary in as the Primary. So XP was installing itself on what was at the time the Primary drive. I have since moved it back to to the Secondary slot.

You've maid a big mistake while installing your windows system never ever change the primary installation structure on windows. What's happening with your windows system is that when you try to boot the windows it detects the HDD's stance as the secondary but in the install log your secondary HDD has been taken as the primary so the system generates a blue screen error or an kernel type of error and reboots it self you want be able to see this error until you disable that from the selection menu you're getting when you try to boot in to XP. In the list you may see some thing like this "Disable reboot on error" or some thing similar to that. Now what you've to do is that to have clean install of the both OS's and it's better if you install windows first on the primary HDD and go with the secondary HDD for the Ubuntu installation after this you want have any trouble.

---

### Post by GepettoBR on 2009-01-28
> **caljohnsmith said:**
> **GepettoBR**, you might want to read through the results of the Boot Info Script that SquirrelyDirge posted, because he/she is all ready using the correct mapping lines with Grub:

And to my knowledge, there is no "liveswap" Grub command. Do you have any references for that? I would be interested to learn more about it if you do. Thanks in advance.

Sorry, I missed that. I'll be more careful. My reference for "liveswap" is the Super Grub Floppy, which contains an entry marked "Live Swap" with only the three lines I instructed SquirrelyDirge to add. I suppose the two "map" lines wouldn't work unless followed by the liveswap command.

---

### Post by SquirrelyDirge on 2009-05-07
I apologize for not returning sooner, but I've been somewhat busy as of late. I would like to say thank you to those who helped since  I managed to get XP working again. (Deleted the old partition it was on, created a new one and reinstalled it.)

Now, however, I seem to have a new problem. Mere days after I managed to get XP working, something happened with a System32 file, causing even to not even work. At first I didn't think much of it, perhaps a virus or something wormed its way onto the drive. With this in mind I simply went to delete the partition it was on (and, I assumed, XP with it), created a new one and tried to reinstall XP. Only now it doesn't seem to work. I get the following message.

```
TO install Windows XP on the partition you selected, Setup must write some startup files to the following disk: 

76317 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

However, this disk does not contain a Windows XP-compatible partition.

To continue installing Windows XP, return to the partition selection screen and create a Windows XP-compatible partition on the disk above. If there is no free space on the disk, delete an existing partition, and then create a new one.

T return to the partition selection screen, press ENTER.
```

Is it safe to assume I screwed something up -badly-? If so, might someone assist me fixing this?

---

### Post by Didius Falco on 2009-05-07
Hi,

Please open a Terminal shell and type ```
sudo fdisk -l
``` and post the output here. After you paste the ouput here, please put code (# on the toolbar in the message editor) tags around it. Then we can see what format that partition is.


Regards,

Didius

---

### Post by caljohnsmith on 2009-05-07
SquirrelyDirge, is your setup still the same as when you posted "fdisk -l" in post #8? If so, that would explain your troubles reinstalling Windows; Windows always requires a primary NTFS/FAT partition on the master drive to put its boot files. If you are trying to reinstall Windows to your 40 GB sdb drive, I'm guessing your sdb drive is the slave drive while your 80 GB HDD is the master drive; that means Windows can't find any partition on your 80 GB master drive to put its boot files since all the partitions on your 80 GB drive are for linux. I think your best bet is to open your computer, disconnect the 80 GB drive, temporarily make your 40 GB drive the master drive, and then reinstall Windows to the 40 GB master drive. Once you've installed Windows to the 40 GB drive and confirmed it boots OK, you can reconnect the 80 GB drive so it is the master drive again, and go back to your original setup. Let me know how it goes or if you run into problems.

John

---

### Post by SquirrelyDirge on 2009-05-07
Here's the results of the [sudo fdisk -l] command.

I'll try cracking the case open and swapping the harddrives tomorrow.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x224f224e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9542    76646083+  83  Linux
/dev/sda2            9543        9729     1502077+   5  Extended
/dev/sda5            9543        9729     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b1b8b1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4981    40009851    7  HPFS/NTFS

```

---

### Post by Didius Falco on 2009-05-07
If you ever have to choose between my advice and the advice of caljohnsmith, do yourself a favor and go with his...

Regards,

Didius

---

### Post by caljohnsmith on 2009-05-07
> **Didius Falco said:**
> If you ever have to choose between my advice and the advice of caljohnsmith, do yourself a favor and go with his...

Regards,

Didius
Thank you for the compliment, Didius, but I certainly make my share of mistakes and sometimes completely misdiagnose someone's problem. We really appreciate all the help you give in the forums, so please don't let me scare you off. :)

Cheers,
John

---

### Post by SquirrelyDirge on 2009-05-10
> SquirrelyDirge, is your setup still the same as when you posted "fdisk -l" in post #8? If so, that would explain your troubles reinstalling Windows; Windows always requires a primary NTFS/FAT partition on the master drive to put its boot files. If you are trying to reinstall Windows to your 40 GB sdb drive, I'm guessing your sdb drive is the slave drive while your 80 GB HDD is the master drive; that means Windows can't find any partition on your 80 GB master drive to put its boot files since all the partitions on your 80 GB drive are for linux. I think your best bet is to open your computer, disconnect the 80 GB drive, temporarily make your 40 GB drive the master drive, and then reinstall Windows to the 40 GB master drive. Once you've installed Windows to the 40 GB drive and confirmed it boots OK, you can reconnect the 80 GB drive so it is the master drive again, and go back to your original setup. Let me know how it goes or if you run into problems.

John 

Alright so I just managed to get around to trying this. I made 4o GN drive the primary, installed windows and verified it was working, switched it back to the Secondary master position, and tried running it from the GRUB boot loader. I received the same message as I did before this recent mess. That is, it brought up that screen where you can select to boot in Safe Mode.

I'm wondering, does it matter whether the drive is in the Secondary Master or Primary Slave position?

---

### Post by caljohnsmith on 2009-05-10
> **SquirrelyDirge said:**
> Alright so I just managed to get around to trying this. I made 4o GN drive the primary, installed windows and verified it was working, switched it back to the Secondary master position, and tried running it from the GRUB boot loader. I received the same message as I did before this recent mess. That is, it brought up that screen where you can select to boot in Safe Mode.

I'm wondering, does it matter whether the drive is in the Secondary Master or Primary Slave position?
I would try putting the drive in the Primary Slave position and see what difference that makes about booting Windows from Grub. Also, what is your current Grub entry for Windows? Is it the same as from your post #8 and post #9?

---

### Post by SquirrelyDirge on 2009-05-10
```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

So yes, the Grub entry is the same as before.

---

### Post by SquirrelyDirge on 2009-05-10
It works now! I'm happy but incredibly confused. I did as you said and made the 4o GB drive the Primary slave and it worked. I have no idea why but it did. Thank you very much caljohnsmith. And thank you everyone else who helped as well.

---

