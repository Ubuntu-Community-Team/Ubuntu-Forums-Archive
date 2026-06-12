---
title: "UNetbootin more then one cd on a flash dirve"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-01
[http://www.linuxjournal.com/article/10697](http://www.linuxjournal.com/article/10697)
It talks like their is more then one cd on the flash drive so how do I do that? What I'm i doing wrong each time I install a new one on to the flash drive the old one does not work. I have one flash drive that is 4g.

---

### Post by C.S.Cameron on 2010-06-01
Check this:
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
If you copy/paste these into terminal you should end up with a multi Boot Flash drive.

Note that if you are running an older version of Ubuntu, pre grub2, you should run these booted from the Live CD.

---

### Post by oldfred on 2010-06-01
I used the panticz site (which is actually a bash script to create the whole thing with those ISOs) and these sites.
 
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)

I have a 4GB USB flash with 4 ubuntu's, gparted & system rescue ISOs.

---

### Post by C.S.Cameron on 2010-06-01
Here are a few menuentry, a couple of them came from OldFred:

set timeout=10
set default=0

menuentry "Ubuntu Live 10.04 Persistent" {
 loopback loop /boot/iso/ubuntu-10.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt -- persistent
 initrd (loop)/casper/initrd.lz 
}

menuentry "Run Ubuntu Live 10.04" {
 loopback loop /boot/iso/ubuntu-10.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/iso/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry "Parted Magic" {
    set isofile="/boot/iso/pmagic-4.10.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry "tinycore" {
 loopback loop /boot/iso/tinycore_2.3.1.iso
 linux (loop)/boot/bzImage --
 initrd (loop)/boot/tinycore.gz
}

menuentry "Memory test (memtest86+)" {
 linux /boot/img/memtest86+.bin
}

---

### Post by lance bermudez on 2010-06-02
I was given this also

[http://tazbuntu.blogspot.com/2009/05/multibootin-with-unetbootin.html](http://tazbuntu.blogspot.com/2009/05/multibootin-with-unetbootin.html)

not doing any better at figuring this one out either. I want to dule boot Billix, f-secure-rescue-cd, and xununtu live 64. how do i do that? Billix and f-secure-rescue-cd both have folders called boot and KNOPPIX. Also the boot folder also have the syslinux.cfg as well the just the /syslinux.cfg in the main drive not in a folder.

---

