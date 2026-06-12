---
title: "How to (re)-install the BOOT RECORD on /dev/hda3 of my Windows 98 ?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-11
Hello, 

I played around with grub and so on, and erased the Boot Record of Windows (98). 

How to restore it ? Is there someone that could provide a regular *.bin to dd to let it reboot again ?  

I boot the windows partition by means of grub installed on linux, but the dos boot record of /dev/hda3 is gone :( :(

Any help welcome

Best regards

---

### Post by cariboo on 2010-01-11
If you can boot into dos, just run **fdisk /mbr** from the prompt. For windows operating systems, the boot files have to be on the first partition of the first hard drive.

---

### Post by lkraemer on 2010-01-11
Just go here:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Scroll down to the Super Grub Page:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
and Scroll down to Where to get Super Grub....
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk)

Get the .9799 version img (for floppy) or the iso (for cdr),
then burn them according to the directions.

Boot the floppy or cdr and go to Fix Windows, then use syslinux
to re-write the MBR.  Done!  Re-boot into Windows.
Easy.

lk

---

### Post by oldfred on 2010-01-11
This is the old windows way of doing it. You may have more of a problem than just the MBR.

[http://articles.techrepublic.com.com/5100-10878_11-5032921.html](http://articles.techrepublic.com.com/5100-10878_11-5032921.html)

The MBR for windows just jumps to the partition with the boot flag on. Then it reads additional files to boot.

---

### Post by frenchn00b on 2010-01-12
> **cariboo907 said:**
> If you can boot into dos, just run **fdisk /mbr** from the prompt. For windows operating systems, the boot files have to be on the first partition of the first hard drive.

well if you do this: fdisk /mbr 
You will erase the grub/booting of the whole harddisk. Better not. Linux is more powerful than this :)

edit : 
+ it requires something else than linux : DOS

---

### Post by frenchn00b on 2010-01-12
This is an example of boot record for floppy disk;

> 6. If you want to be extra cautious, you can save a copy of the current machine's master boot record to a file on the floppy. The following example assumes the master boot record is on device hda; the file containing the boot record is named boot.mbr.

 dd if=/dev/hda of=/media/floppy/boot.mbr bs=512 count=1  
To restore it, you would just reverse the parameters of the dd command:

 dd if=/media/floppy/boot.mbr of=/dev/hda bs=512 count=1 

this shall be possible for the /dev/hda3 , this way ... somehow

But I have lost the boot.mbr file of my partition hda3

---

### Post by lkraemer on 2010-01-12
Well, if you need a Grub boot floppy, you can make one easily.
If you are using GRUB2 (Ubuntu 9.10 or later) it will be a little
harder.  Search for "create a grub boot floppy"!

Just insert the created Grub boot floppy or CDR (burned from ISO) and
boot.

Or you can insert a LiveCD of Ubuntu and boot it.  Then open a Terminal
window and type (assuming Legacy Grub and not GRUB2):
```

sudo grub
find /boot/grub/stage1

```
This will return a location.  If you have more than one, select the
installation that you want to provide the grub files.

You can also type:
```

root (

```
then the TAB key to see what is avalable to boot from.

Next, this is important, whatever was returned for the find command, use
it in the next two lines:
```

root (hd?,?)
setup (hd?)
quit

```
Then exit the Terminal Window and test the boot.

lk

---

### Post by frenchn00b on 2010-01-12
> **lkraemer said:**
> Well, if you need a Grub boot floppy, you can make one easily.
If you are using GRUB2 (Ubuntu 9.10 or later) it will be a little
harder.  Search for "create a grub boot floppy"!

Just insert the created Grub boot floppy or CDR (burned from ISO) and
boot.

Or you can insert a LiveCD of Ubuntu and boot it.  Then open a Terminal
window and type (assuming Legacy Grub and not GRUB2):
```

sudo grub
find /boot/grub/stage1

```
This will return a location.  If you have more than one, select the
installation that you want to provide the grub files.

You can also type:
```

root (

```
then the TAB key to see what is avalable to boot from.

Next, this is important, whatever was returned for the find command, use
it in the next two lines:
```

root (hd?,?)
setup (hd?)
quit

```
Then exit the Terminal Window and test the boot.

lk


Well thank you  nice howto 
.. 
but 
I need a boot record of windows 98 (dos) for my /dev/hda3 partition of windows 98  (which has nothing to do with the master boot record)

Could somebdy get this boot record from a working system ? (bin)

---

