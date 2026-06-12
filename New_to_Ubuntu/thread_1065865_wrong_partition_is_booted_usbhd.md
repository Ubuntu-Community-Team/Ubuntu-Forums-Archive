---
title: "wrong partition is booted? usb/hd"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by choko on 2009-02-10
I have installed the live-cd on /dev/sda6 and also on
/dev/sdb1.

sda6=my hd
sdb1=usb stick

My grab menu.lst entry is

title           boot live-cd from harddisk
root            (hd0,5)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz



title           boot live-cd from usb stick
root            (hd1,0)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz


My problem is that it is always the /dev/sda6 which will be
booted, I can't get the usb partition to boot, i.e. it always
picks up the squash file system from the hd, never from the
usb. If I delete the /dev/sda6 partition, it will then find
the usb stick. Any ideas?

---

### Post by Sidewinder1 on 2009-02-10
You might try changing the boot sequence in your BIOS.?.

---

### Post by ranch hand on 2009-02-10
When you boot and your box fires up there should be an option to enter bios (setup) or boot menu.  Click on boot menu and then select the option there.  It is easier than changing your bios.

That said, if you want to boot from the usb all the time change your bios.

This is assuming that you installed on the HDD and wthe Stick independent of each other.  If you have both up when you install they will be dual booted and you should get a grub menu list giving you the choice of which to boot.

---

