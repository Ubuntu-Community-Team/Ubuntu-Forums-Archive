---
title: "[SOLVED] Grub Error 17 while starting thumb installed Hardy"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by thomas228 on 2008-12-25
Hi

This is my first thread and I need help as I can't find any answers with the forum search

I installed Hardy on an 8GB thumb using adult swim's method found in

[http://ubuntuforums.org/showthread.php?t=1017566&page=2]("http://ubuntuforums.org/showthread.php?t=1017566&page=2") post #14

and selecting the bios usb option to boot into grub's dual boot gave me

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Ubuntu 8.04.1, kernel 2.6.24-22-generic (0n /dev/sda3)
Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)


First 3 options give

Error 17: Cannot mount selected partition

Press any key to continue...

Last 2 options give

Error 22: No such partition

Press any key to continue.

Windows Vista/Longhorn (loader) option gives

Starting up …   then hangs and requires shutting the computer down

My normal dual boot (Vista/Ubuntu 8.04) works fine but the thumb ??/

Any help would be very much appreciated 

Please be patient as I am handicapped with having to use dial up thru windows so it may take me some time to respond.

Thanks in advance

Tom

---

### Post by tomtom1982 on 2008-12-26
Please post the output of

```
sudo fdisk -l
```

on terminal

---

### Post by northern lights on 2008-12-26
I'm not sure, whether I have understood you correctly.
All three OSs (Ubuntu, Windows, Ubuntu on thumbdrive) fail to boot when the USB flashdrive is connected, however the very same hdd installs of Ubuntu and Windows boot without the USB drive plugged in?

If so, you might want to flash your BIOS. It is quite common, for hardware vendors to ship new boards early and add full USB boot compatibility with a later BIOS/firmware upgrade only.

Check whether your mainboard vendor offers a newer BIOS to download.

---

### Post by thomas228 on 2008-12-26
> **tomtom1982 said:**
> Please post the output of

```
sudo fdisk -l
```on terminal

Hi

Woke up early and found your post

Here's the output you asked for

```
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        7111    55574528    7  HPFS/NTFS
/dev/sda3            7112       13956    54982462+  83  Linux
/dev/sda4           13957       14593     5116702+  82  Linux swap / Solaris

Disk /dev/sdb: 16.2 GB, 16240345088 bytes
142 heads, 32 sectors/track, 6980 cylinders
Units = cylinders of 4544 * 512 = 2326528 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6981    15859696    c  W95 FAT32 (LBA)

Disk /dev/sdc: 8021 MB, 8021606400 bytes
16 heads, 32 sectors/track, 30600 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000e44cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          16       22969     5875977   83  Linux
/dev/sdc2           22970       30598     1953024    5  Extended
/dev/sdc5           22970       30598     1953008   82  Linux swap / Solaris
tds@tds-laptop:~$ 
```

 Note that Disk /dev/sdb is an extra thumb I use to copy results over to this laptop so I can post in windows.

Original Errors as in post #1 are the same with 16GB thumb removed

Thanks

Tom

---

### Post by thomas228 on 2008-12-26
> **northern lights said:**
> I'm not sure, whether I have understood you correctly.
All three OSs (Ubuntu, Windows, Ubuntu on thumbdrive) fail to boot when the USB flashdrive is connected, however the very same hdd installs of Ubuntu and Windows boot without the USB drive plugged in?

If so, you might want to flash your BIOS. It is quite common, for hardware vendors to ship new boards early and add full USB boot compatibility with a later BIOS/firmware upgrade only.

Check whether your mainboard vendor offers a newer BIOS to download.

Hi 

Thanks for responding

You understand my problem correctly however I'm not sure it is a bios problem as I'm able to do a live thumb boot of the ubuntu livecd iso.

Still I'll check with Toshiba and see if te phenox bios needs updating.

Thanks

Tom

---

### Post by bumanie on 2008-12-26
I have skim read the post you referred to. I suspect that when you are trying to boot off the usb stick, grub cannot find a reference to it in /etc/fstab. If I were you, I would follow [this instead]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") - adultswim was very sure about his method and it may well work, but I have not tried it, however I have tried the method on the link and it works. It doesn't require any editing of the grub menu or fstab.

PS: I would be very careful about flashing ones bios - if there is a power interruption part way through, your motherboard will only be good for scrap - I know many flash bios without problems, but I have seen a number of people run into the above issue as well.

---

### Post by northern lights on 2008-12-26
> **thomas228 said:**
> I'm able to do a live thumb boot of the ubuntu livecd iso
If you can do that, your BIOS needs no update. It is simply quite common that USB boot compatibility is claimed for a motherboard but only added via firmware upgrades later.

It's all the more weird, that none of the three OSs would boot then.

I'd suggest, going with a different approach, like the one of pendrivelinux.org, as bumanie proposed.

---

### Post by tomtom1982 on 2008-12-26
> Here's the output you asked for
 
 
Code:
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        7111    55574528    7  HPFS/NTFS
/dev/sda3            7112       13956    54982462+  83  Linux
/dev/sda4           13957       14593     5116702+  82  Linux swap / Solaris

Disk /dev/sdb: 16.2 GB, 16240345088 bytes
142 heads, 32 sectors/track, 6980 cylinders
Units = cylinders of 4544 * 512 = 2326528 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6981    15859696    c  W95 FAT32 (LBA)

Disk /dev/sdc: 8021 MB, 8021606400 bytes
16 heads, 32 sectors/track, 30600 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000e44cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          16       22969     5875977   83  Linux
/dev/sdc2           22970       30598     1953024    5  Extended
/dev/sdc5           22970       30598     1953008   82  Linux swap / Solaris
tds@tds-laptop:~$
 Note that Disk /dev/sdb is an extra thumb I use to copy results over to this laptop so I can post in windows.
 

Well, that won't be helpfull, but your grub menu.lst seems to be right.

---

### Post by thomas228 on 2008-12-26
> **bumanie said:**
> I have skim read the post you referred to. I suspect that when you are trying to boot off the usb stick, grub cannot find a reference to it in /etc/fstab. If I were you, I would follow [this instead]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") - adultswim was very sure about his method and it may well work, but I have not tried it, however I have tried the method on the link and it works. It doesn't require any editing of the grub menu or fstab.

PS: I would be very careful about flashing ones bios - if there is a power interruption part way through, your motherboard will only be good for scrap - I know many flash bios without problems, but I have seen a number of people run into the above issue as well.

> **northern lights said:**
> If you can do that, your BIOS needs no update. It is simply quite common that USB boot compatibility is claimed for a motherboard but only added via firmware upgrades later.

It's all the more weird, that none of the three OSs would boot then.

I'd suggest, going with a different approach, like the one of pendrivelinux.org, as bumanie proposed.

Thanks for your recommendations 

I looked at the link and only have a few problems with that method.

They can probably be worked around with a wifi connection however that requires a 28 mile round trip to my local Hardy's

My only internet connection at home is dial up at a very shaky 26 kb.

That lack of internet speed is the reason I am trying to use a thumb installation in the first place.

I have 2 laptops and 4 desktops and thought a thumb OS system transfer would be a way to get ubuntu on all my computers.

Thanks for the input and I hope we can find a way of fixing my Error 17.

The later part of your referenced link may offer an answer as the thumb installation I have appears to have everything in it 

Thanks

Tom

---

### Post by northern lights on 2008-12-26
> **tomtom1982 said:**
> Well, that won't be helpfull, but your grub menu.lst seems to be right.
I might just be blind or still a bit mindf*cked from too much Christmas partying, but where exactly did the OP post his menu.lst?

@the OP:
GRUB returns error 17 during stages 1.5 and 2 if the partition requested exists, but the filesystem type cannot be recognized by GRUB. It returns error 22 if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

What could be happening is that connecting the thumbdrive alters device indentifiers for the hdd also, but then again your *fdisk -l* output suggests that the thumbdrive is added to the end as /dev/sdc.

Can you compare *fdisk -l* outputs with and without the 8GB thumb and see whether the rest remains the same (it should)?

---

### Post by bumanie on 2008-12-26
> I might just be blind or still a bit mindf*cked from too much Christmas partying, but where exactly did the OP post his menu.lst?No, you haven't done too much partying, no menu.lst has been posted - probably wouldn't be a bad idea though. Post the output of > cat /boot/grub/menu.lstas well as northernlights request.

---

### Post by caljohnsmith on 2008-12-26
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by thomas228 on 2008-12-26
> **northern lights said:**
> I might just be blind or still a bit mindf*cked from too much Christmas partying, but where exactly did the OP post his menu.lst?

@the OP:
GRUB returns error 17 during stages 1.5 and 2 if the partition requested exists, but the filesystem type cannot be recognized by GRUB. It returns error 22 if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

What could be happening is that connecting the thumbdrive alters device indentifiers for the hdd also, but then again your *fdisk -l* output suggests that the thumbdrive is added to the end as /dev/sdc.

Can you compare *fdisk -l* outputs with and without the 8GB thumb and see whether the rest remains the same (it should)?

Hi

Output of fdisk -l remains the same for Disk /dev/sda however with just the 8GB thumb installed the 8GB Disk becomes /dev/sdb (with the 16GB thumb removed)

Same error # 17 with just 8GB installed and booting via usb bios

Removing all thumbs leaves fdisk -l with just Disk /dev/sda portion

Output takes a long time transfering by thumb and editing tabs and returns in windows notepad

Thanks

Tom

---

### Post by northern lights on 2008-12-26
> **thomas228 said:**
> Output takes a long time transfering by thumb and editing tabs and returns in windows notepad
Don't have to post it, I'm sure you can compare it own your own.
The behavior you describe is what is expected happen anyhow.

I'm a bit stumped as to what could cause it.

Once again, try a different approach of setting up your bootable thumb, if the same errors happen look into a firmware/BIOS upgrade.

---

### Post by thomas228 on 2008-12-26
> **bumanie said:**
> No, you haven't done too much partying, no menu.lst has been posted - probably wouldn't be a bad idea though. Post the output of as well as northernlights request.

Hi 

Switched to Openoffice 00o3 

Here's the menu.lst from dual boot vista/ubuntu (...-22-generic)


[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
color cyan/blue white/blue

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
title		Windows 95/98/NT/2000
root		(hd0,1)
savedefault
makeactive
chainloader	+1
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
# kopt=root=UUID=de634c04-e589-43d6-b428-92bb97d5b277 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=773

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=de634c04-e589-43d6-b428-92bb97d5b277 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=de634c04-e589-43d6-b428-92bb97d5b277 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/PHP]



And heres menu.lst from 8GB thumb

[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=cbc5e19a-cab8-4bcc-85fd-8fd2303b2e49 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cbc5e19a-cab8-4bcc-85fd-8fd2303b2e49 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cbc5e19a-cab8-4bcc-85fd-8fd2303b2e49 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=de634c04-e589-43d6-b428-92bb97d5b277 ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=de634c04-e589-43d6-b428-92bb97d5b277 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot[/PHP]

Hope this sheds more light on the problem

Tom

---

### Post by caljohnsmith on 2008-12-26
> **thomas228 said:**
> ```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cbc5e19a-cab8-4bcc-85fd-8fd2303b2e49 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Red"](hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cbc5e19a-cab8-4bcc-85fd-8fd2303b2e49 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		[COLOR="Red"](hd1,0)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```

If you are booting from your 8 GB USB drive, then I believe I see the problem with your menu.lst: the entries should use (hd0,0) rather than (hd1,0) since the Ubuntu on the USB drive is on the first drive in the BIOS boot order or (hd0) when you boot the USB drive. How about booting your USB drive again, but this time select the first Ubuntu entry in the Grub menu, press "e" to edit it, select the line that says "root (hd1,0)", press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent. Let me know how it goes or if you still run into problems.

---

### Post by thomas228 on 2008-12-26
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

Hi caljohnsmith

```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

results in Failed because I do not have  an internet connection in ubuntu. 

I have to use wifi at Hardy's for that to work unless I can download the referenced boot info script via windows and transfer it to ubuntu desktop.

Not sure I know how to do that

So until later (Hardy's)

Tom

---

### Post by bumanie on 2008-12-26
I believe Caljonsmith is correct. If you are changing the boot device in bios to usb when using the usb device, grub would see the usb device as the first partition on the first drive. Where Caljonsmith has highighted the (hd1,0) it needs to be changed to (hd0,0). To do this > gksudo gedit /boot/grub/menu.lstChange the entries to (hd0,0), save - reboot and the computer should boot from the usb device when it is placed first in bios.

---

### Post by thomas228 on 2008-12-26
> **caljohnsmith said:**
> If you are booting from your 8 GB USB drive, then I believe I see the problem with your menu.lst: the entries should use (hd0,0) rather than (hd1,0) since the Ubuntu on the USB drive is on the first drive in the BIOS boot order or (hd0) when you boot the USB drive. How about booting your USB drive again, but this time select the first Ubuntu entry in the Grub menu, press "e" to edit it, select the line that says "root (hd1,0)", press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent. Let me know how it goes or if you still run into problems.

WORKED

Thanks caljohnsmith

I'll make the changes to menu.lst on the thumb

```
sudo gedit /boot/grub/menu.lst
``` and "root (hd1,0)" to "root (hd0,0)"

What about Vista etc?

Thank you for your help

Tom

---

### Post by caljohnsmith on 2008-12-26
Glad to hear that worked, Tom. To boot Vista from your Grub menu, how about trying both of the following entries in your menu.lst:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Save, reboot, and let me know if either work; if not, let me know exactly what happens when you choose them from the Grub menu.

---

### Post by thomas228 on 2008-12-26
> **caljohnsmith said:**
> Glad to hear that worked, Tom. To boot Vista from your Grub menu, how about trying both of the following entries in your menu.lst:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

results in

```
Starting up ...

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

```

and

```
title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```

results in

```
Error 21: Selected disk does not exist

Press any key to continue...
```

Seems there is no windows  BOOTMGR in the MBR on the thumb ??


Thanks again

Tom

---

### Post by caljohnsmith on 2008-12-26
Sorry about that Tom, that was my mistake; I didn't notice that your Vista was actually on the 2nd partition and not the 1st one, so instead try:
```
title       Windows Vista (hd1)
rootnoverify     [COLOR="Blue"](hd1,1)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
That should work if I haven't lost my brain again, but if it doesn't work, let me know exactly what happens. :)

---

### Post by thomas228 on 2008-12-26
> **caljohnsmith said:**
> Sorry about that Tom, that was my mistake; I didn't notice that your Vista was actually on the 2nd partition and not the 1st one, so instead try:
```
title       Windows Vista (hd1)
rootnoverify     [COLOR="Blue"](hd1,1)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
That should work if I haven't lost my brain again, but if it doesn't work, let me know exactly what happens. :)

Thanks again caljohnsmith

That works for Vista

I changed the hdd ubuntu ...-22 from root   (hd0,2) to root    (hd1,2) and got it to boot up ok

Only question left is how much I can reduce the kernel line to

ie can I get rid of root=UUID=... so I'll have fewer problems on using the thumb boot option on other computers??

Thanks for all your time

Tom

---

### Post by caljohnsmith on 2008-12-26
> **thomas228 said:**
> Thanks again caljohnsmith

That works for Vista

I changed the hdd ubuntu ...-22 from root   (hd0,2) to root    (hd1,2) and got it to boot up ok

Only question left is how much I can reduce the kernel line to

ie can I get rid of root=UUID=... so I'll have fewer problems on using the thumb boot option on other computers??

Thanks for all your time

Tom
Actually you would want to keep the UUID line, because the UUID of a partition won't change even if you use the drive in other computers. It's the (hdX,Y) that can change (specifically the X can change), depending on which drive you boot from on start up, so UUIDs are actually an advantage to use. Anyway, glad you have it all booting OK now; cheers and have fun with Vista and Ubuntu. :)

---

