---
title: "Boot from iso?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by choko on 2009-02-12
Hello all,

I have been reading the BootFromUsb document and thought
I would try something similar namely "BootFromIso", so
instead of mounting the iso and copying the files to the
usb, I simply copied the iso file itself. Well, I thought
to myself either it will work or not, but the outcome
was neither, namely I got started the installation.
Ofcourse, this is of no use, I need the live-cd. Does
anyone know how to do this? (If at all it is supported,
as it is,sfor example in slax linux)

---

### Post by Ripose on 2009-02-12
Sounds like you are trying to do 2 different things.
Not sure what you mean "supported by slax"

You have to burn the iso to CD.
There is a different download for a USB install.

---

### Post by Temposs on 2009-02-12
hi choko,
  You should follow the instructions from this page precisely if you want to burn a bootable iso from CD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and this one for USB:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

If you don't follow it exactly, it won't work.

---

### Post by choko on 2009-02-12
Hello,

In Slax, after the boot prompt you can write as follows

linux=/dev/sdaX/image.iso

This will boot a live-cd slax from the iso file,
in other words, one is not required to copy the
individual files from the cd, so one does not
need to burn the image. I couldn't find this
flexibility on ubuntu.

Also, there is a document

Preparing Files for USB Memory Stick Booting

We find there the following

"Adding an ISO image

The installer will look for an Ubuntu ISO image on the stick as its source for additional data needed for the installation. So your next step is to copy an Ubuntu ISO image onto your stick (be sure to select one that fits). The file name of the image must end in .iso. "

---

### Post by mkvnmtr on 2009-02-12
I was wondering the same thing today. The 9.04 daily build for powerpc is 702 MB and that is too big to burn to a cd. I know you can mount an ISO but I don't know if you can boot from it. Seems like you could but maybe the bios or firmware would not see it.

---

### Post by choko on 2009-02-12
Maybe it's not possible


[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


I quote

"Copy the Ubuntu CD to your USB stick

Copy the contents of the Ubuntu installation CD to your USB drive (i.e. all files and directories that are on the installation CD). [COLOR="Red"]Please do not copy an ISO image of the installation CD[/COLOR]. Note that you don't have to burn the iso to copy it's contents, from linux it can be mounted like so:"

---

### Post by Ripose on 2009-02-13
This link may help [Install Ubuntu on a USB stick]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar")

---

