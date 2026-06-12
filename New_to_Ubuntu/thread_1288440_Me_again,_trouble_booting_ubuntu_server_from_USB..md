---
title: "Me again, trouble booting ubuntu server from USB."
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-10-11
Hi,

I posted earlier about having trouble installing Ubuntu Server Edition (x32, 9.04) from my USB flash drive, I believe I've found the solution however I'm still having problems. I've been reading the documentation on installing Ubuntu Server from a USB here: [https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)
and I've got to the point where I'm executing the script...

So, I execute the script, it seems to be working, it installs syslinux, mtools etc then it says:

```

Use fdisk to manually create a 1GB bootable FAT16 partition.
Press [ENTER] to start the fdisk program...

The number of cylinders for this disk is set to 1926.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):

```
I'd really like to get this working, any help is much appreciated!

- Aaron.

---

### Post by yeats on 2009-10-11
If you are using desktop Ubuntu, you can install a program called usb-creator that will take care of all this for you.  There is a similar program for Windows called UNetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I would use one of those - they take the work out of what you're struggling with.

---

