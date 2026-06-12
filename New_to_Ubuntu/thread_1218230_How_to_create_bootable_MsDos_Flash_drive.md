---
title: "How to create bootable MsDos Flash drive?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by bikrus on 2009-07-20
Hi!

I have:
1. Ubuntu 9.04
2. Toshiba 4Gb flash drive
3. Bootable MS DOS 6.22 floppy image (1.44Mb)
4. Have no floppy drive

I need to make bootable MS DOS 6.22 flash drive. How can I achive it? Please, help.

---

### Post by schwascore on 2009-07-20
FreeDOS [http://wiki.fdos.org/Installation/BootDiskCreateUSB]("http://wiki.fdos.org/Installation/BootDiskCreateUSB")

You could probably use the built in boot-disk creator and the images from [bootdisk.com]("http://www.bootdisk.com/") to do this as well.

---

### Post by rCXer on 2009-07-20
Here are 2 ways to do this ( :( sorry they are for windows ).  Method 1 always works for me.  I haven't tried the last one. You could also try [FreeDOS](http://en.wikipedia.org/wiki/FreeDOS), a open source MS-DOS clone.

1. [Making MS-DOS thumbdrive in Windows](http://www.pcstats.com/articleview.cfm?articleid=1676&page=2).
 * Install and run the "[HP USB Disk Storage Format Tool](http://files.extremeoverclocking.com/file.php?f=197)"
 * Under Filesystem choose "FAT 32"
 * Check "Create a DOS startup disk"
 * Select "using MS-DOS system files"
 * Then press "Start"
 * Reboot. You may have to enable USB booting in BIOS.
 This method can also be used with FreeDOS by selecting "using DOS system files located at" and entering path of the files

2. [Make FreeDOS thumbdrive in Windows](http://www.bensbits.com/2007/08/21/booting_dos_from_a_usb_flash_drive)

---

### Post by spcwingo on 2009-07-20
You can use Unetbootin to create a Freedos USB boot disk.  It works great for flashing the BIOS.  :D

---

### Post by bikrus on 2009-07-21
> **schwascore said:**
> FreeDOS ...

You could probably use the built in boot-disk creator and the images from bootdisk.com

1. Sorry. Interested in MsDos 6.22.
2. There are no MsDos 6.22 ISO (not floppy image) at the bootdisk. I have troubles with converting image file format to iso. But this will be one of the solutions of my problem.

> **rCXer said:**
> Here are 2 ways to do this ( :( sorry they are for windows ).

Sorry. Have no Windows. Interested in ubuntu (*nix) solution.

> **spcwingo said:**
> You can use Unetbootin to create a Freedos USB boot disk.  It works great for flashing the BIOS.  :D

1. I am intereseted in MsDos 6.22.
2. I will not use it to flashing the BIOS.

------------------------------------------

Thanks, guys! I understand that my task is out of standard solutions. That's why I've asked about it here at the Ubuntu forum. One more time:

I have:
1. Ubuntu 9.04
2. 4Gb flash drive (
3. Bootable MS DOS 6.22 floppy image (1.44Mb), not iso
4. Have no floppy drive

I need to make bootable MS DOS 6.22 flash drive.

1. I have no Windows.
2. I am intereseted exactly in MsDos 6.22, not FreeDOS etc.
3. I will not use it to flashing BIOS.

---

### Post by bikrus on 2009-07-21
Thanks everyone! Problem solved!

Solution:

sudo qemu -fda /home/user1/var/desktop/msdos622.img -hda /dev/sdb

At qemu start press F12 to boot from floppy and do things like in simple dos box. After boot from floppy:
>fdisk
to create active partition on flash drive.
>format /s c:
to format "C" drive and copy system files.
>fdisk /mbr
to allow booting from c: drive.

That's all.

---

