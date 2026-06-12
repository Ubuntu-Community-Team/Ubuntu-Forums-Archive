---
title: "PLEASE HELP: stuck in initramfs"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by tdrusk on 2010-10-20
I am so frustrated right now. I've got work to do and my desktop won't work.

I just updated my system(10.10 64 bit) and it required a restart. I restarted and my resolution was wrong. I thought maybe it updated a kernel, so I wanted to boot to an earlier one. I used startup-manager and switched it from the selected kernel to a previous one and made it default. Now I boot and it goes to initramfs telling me "udevadm trigger is not permitted while udev is unconfigured. Gave up on waiting for root device. Missing modules cat /proc/modules; ls /dev/ ALERT! /dev/disk/by-uuid/cf44d924-da15-40f5-8d23-fdedc35f3f7c does not exist. Dropping to shell!

So here I am in a shell.

I would boot the ubuntu disk, but I can't eject my cd-drive because my computer does not have an eject button the cd-drive. 

What can I do to get my computer working again?

---

### Post by ZarathustraDK on 2010-10-20
I don't get the error-message, but what happens if you do:

```
sudo /etc/init.d/gdm start (or stop first, then start)
```

or

```
sudo service gdm start (& stop)
```

?

---

### Post by bobbob1016 on 2010-10-20
Start up with the new kernel, and have Device Manager install the drivers for your card.  You went the hard way right away.  What video card are you using?  How many upgrades have you done?  I always do a fresh install, but my /home is on a different partition, so I don't lose my settings.

---

### Post by tdrusk on 2010-10-20
> **bobbob1016 said:**
> Start up with the new kernel, and have Device Manager install the drivers for your card.  You went the hard way right away.  What video card are you using?  How many upgrades have you done?  I always do a fresh install, but my /home is on a different partition, so I don't lose my settings.
How do I get to grub so I can pick which kernel to run?

The card is an integrated intel.

I installed a few days before Ubuntu 10.10 became officially released(installed in late-beta)

It was a fresh install and was working great until 20 minutes ago when all this started.

---

### Post by tdrusk on 2010-10-20
> **ZarathustraDK said:**
> I don't get the error-message, but what happens if you do:

```
sudo /etc/init.d/gdm start (or stop first, then start)
```or

```
sudo service gdm start (& stop)
```?
I can't run these. sudo is not found and neither is /etc/init.d/gdm or service. I am stuck in this shell..

---

### Post by albandy on 2010-10-20
boot with a live cd, mount your root partition and send us your grub configuration.

---

### Post by tdrusk on 2010-10-20
> **albandy said:**
> try this:
sudo dpkg-reconfigure initramfs-tools
I can't boot into Ubuntu. It drops me into BusyBox before booting.

---

### Post by P4man on 2010-10-20
> **tdrusk said:**
> I am so frustrated right now. I've got work to do and my desktop won't work.

I just updated my system(10.10 64 bit) and it required a restart. I restarted and my resolution was wrong. I thought maybe it updated a kernel, so I wanted to boot to an earlier one. I used startup-manager and switched it from the selected kernel to a previous one and made it default. Now I boot and it goes to initramfs telling me "udevadm trigger is not permitted while udev is unconfigured. Gave up on waiting for root device. Missing modules cat /proc/modules; ls /dev/ ALERT! /dev/disk/by-uuid/cf44d924-da15-40f5-8d23-fdedc35f3f7c does not exist. Dropping to shell!

So here I am in a shell.

I would boot the ubuntu disk, but I can't eject my cd-drive because my computer does not have an eject button the cd-drive. 

What can I do to get my computer working again?

AFAIK, every cd drive has an eject mechanism, though it may require you insert a paperclip in a tiny hole.

Other alternative: create a bootable USB stick on a different machine. Use [unetbootin]("http://unetbootin.sourceforge.net/") if you only have access to a windows machine.

TO be honest, my guess is, you have a harddrive problem.

---

### Post by albandy on 2010-10-20
> **tdrusk said:**
> I can't boot into Ubuntu. It drops me into BusyBox before booting.

Sorry, I was editing my comment. Please send your grub configuration.

---

### Post by tdrusk on 2010-10-20
> **albandy said:**
> Sorry, I was editing my comment. Please send your grub configuration.
How can I do that without being in Ubuntu?

---

### Post by albandy on 2010-10-20
You can edit grub in boot time.
When grub starts, enter the "e" key and change root=UID=..... with root=/dev/sda1
then ctrl+x to boot
assuming sda1 as the root partition.

---

### Post by tdrusk on 2010-10-20
> **albandy said:**
> You can edit grub in boot time.
When grub starts, enter the "e" key and change root=UID=..... with root=/dev/sda1
then ctrl+x to boot
assuming sda1 as the root partition.
My install skips grub and tries to boot the default kernel. There is not grub splash when booting. How can I get into grub. (Thanks for your help btw)

---

### Post by albandy on 2010-10-20
> **tdrusk said:**
> My install skips grub and tries to boot the default kernel. There is not grub splash when booting. How can I get into grub. (Thanks for your help btw)

Press the right shift key while booting and grub will appear

---

### Post by utilitytrack on 2010-10-20
> **tdrusk said:**
> What can I do to get my computer working again?

See this: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123")

PS
And who can state that Ubuntu 10.10 is not a beta? I think it's consist from bugs only :))

---

### Post by tdrusk on 2010-10-20
> **albandy said:**
> Press the right shift key while booting and grub will appear
THANKS! I am in :) Will post what you asked in a second...

---

### Post by albandy on 2010-10-20
> **tdrusk said:**
> THANKS! I am in :) Will post what you asked in a second...

Also, you can open your cd reader with a paper clip, there is a little hole near the eject button, see the image attached:

---

### Post by tdrusk on 2010-10-20
here's grub.cfg

```
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
set default="2"
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

```

If I use startup-manager and select the newer kernel as my default should it work?

---

### Post by albandy on 2010-10-20
Now, lets see if your harddisk UUID differs from the grub one:
type: sudo blkid 
and submit the answer.



> **tdrusk said:**
> here's grub.cfg

```
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
set default="2"
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cf44d924-da15-40f5-8d23-fdedc35f3f7c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set cf44d924-da15-40f5-8d23-fdedc35f3f7c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

```

If I use startup-manager and select the newer kernel as my default should it work?

---

### Post by tdrusk on 2010-10-20
> **albandy said:**
> Now, lets see if your harddisk UUID differs from the grub one:
type: sudo blkid 
and submit the answer.

```
/dev/sda1: UUID="cf44d924-da15-40f5-8d23-fdedc35f3f7c" TYPE="ext4" 
/dev/sda5: UUID="e34c72d4-6e18-4261-9d58-247fa6a2819a" TYPE="swap" 

```

---

### Post by tdrusk on 2010-10-20
Just for the record, I am in the newest kernel and would like to stay in it if i can get the correct resolution.
Here's my lspci
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
```

---

### Post by albandy on 2010-10-21
> **tdrusk said:**
> ```
/dev/sda1: UUID="cf44d924-da15-40f5-8d23-fdedc35f3f7c" TYPE="ext4" 
/dev/sda5: UUID="e34c72d4-6e18-4261-9d58-247fa6a2819a" TYPE="swap" 

```

Your UUID are right so maybe a kernel re-installation will work. 

sudo apt-get --reinstall kernel_name

---

### Post by viuks on 2010-11-25
Today I got exactly the same problem. Boot tops on busybox and initramfs.
It could not be hard drive problem, because I have separate partition with previous Ubuntu version on it and I am in. It seems to me, that Maverick is just still in beta stage.

---

### Post by madjr on 2010-11-25
> **viuks said:**
> Today I got exactly the same problem. Boot tops on busybox and initramfs.
It could not be hard drive problem, because I have separate partition with previous Ubuntu version on it and I am in. It seems to me, that Maverick is just still in beta stage.

how did it broke on you? did you do anything? does the live cd/usb boots?

---

### Post by taur on 2011-02-15
bump

---

