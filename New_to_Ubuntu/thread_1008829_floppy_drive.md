---
title: "floppy drive?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by em3ry on 2008-12-11
ubuntu 8.10/gnome/

ok. first I couldnt find 'floppy drive' anywhere in my file browser. so I went to the net and found this:

sudo gedit /etc/modules

and add the line :

floppy 


I did and now 'floppy drive' does appear in the file browser but It doesnt do anything when I click on it.  something elso I read said to run

mount /dev/fd0

but there is no fd0. only a fd.



dont know what to do.

&#9785;

yes the floppy drive always worked before under windows.

---

### Post by em3ry on 2008-12-11
when I just now accidently booted with a floppy in the drive it did nothing till I removed it and rebooted. so the drive seems to work.

---

### Post by Kellemora on 2008-12-12
Hi em

Floppy Drives are VERY POORLY supported in Ubuntu!

I've never been able to mount the drive itself, only the contents of the drive and then ONLY if it was formatted in FAT.

I spent part of a day formatting some floppies in EXT2 only to find they don't work in Ubuntu.

Also, there is NO WAY to format 720 floppies or larger than 1.44 floppies and I have hundreds of new 2.0 floppies here.  I can format them to 1.44 on a Windows machine using FAT but Ubuntu still can't read a single one of them.

And I don't think they have any support for 5-1/4 floppies at all.

Although I Love Ubuntu, in order to use SOME of the features of Ubuntu, it requires you maintain a WinDOZE machine close by!
Did I say Not Cool?

The biggie I found was that the 3rd party drivers used for Printer Hardware, although in many aspects are better than the OEM drivers that came with the printer.  The programmers made a MAJOR BOOBOO.  They provided NO WAY to change out the Toner Cartridges.  So we need to keep a WinDOZE machine to plug the Printer into every time it needs a cartridge changed.

I don't doubt that in the next release they will quit supporting CDs too, since the younger crowd uses USB sticks and drives now.

Hate to sound sarcastic here, but I'm trying to get AWAY from the DOZE, not keep adding more DOZE machines in order to enable the use of Ubuntu!
And feel it's a VALID POINT that should be addressed by the powers that be!

TTUL
Gary

---

### Post by rlunger on 2008-12-12
I had the same problem in Xubuntu 8.10.  After some time reading various forums, this is the solution I came up with:

Create a mount point folder for your floppy:
    
    sudo mkdir /media/floppy

As root, add this line to /etc/fstab, followed by a Return character:

    /dev/fd0	/media/floppy  vfat	rw,user,noauto  0	0

As root, add this line to /etc/modules, followed by a Return:

    floppy

Create the floppy as a block device:

    sudo mknod fd0 b 2 0 

Set ownership properties:

    sudo chown root:users /dev/fd0

Now you can mount your floppy drive:

    sudo mount -t vfat /dev/fd0 /media/floppy

Hope this helps.

---

