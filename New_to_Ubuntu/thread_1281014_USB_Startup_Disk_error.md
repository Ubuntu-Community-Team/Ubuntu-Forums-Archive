---
title: "USB Startup Disk error"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by poisonborz on 2009-10-02
Hola,
I need to create a usb Ubuntu to my pendrive: I used the Startup Disk creator from the 9.04 livecd, but when I booted the pendrive, it wrote the good ol' **Could not find kernel image: linu**.

Yes, I googled after it, and yes, syslinux.cfg exists, along with the syslinux folder. The cfg reads:

```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```

Anyone having an idea what could be wrong? I used vanilla SDCreator settings on a vanilla pendrive...
Thanks

---

### Post by tarps87 on 2009-10-03
It could be a fault durring the creation of the live usb, have you tried rebuilding the live usb, running a check on the live cd (if it is a cd) or a check sum if it is an iso. Failing this you can try unetbootin.

---

### Post by poisonborz on 2009-12-17
I found a quick & great tool to create USB installs, although it's for Windows: with UltraISO (even the trial version) you can quickly "burn" any iso image to a pendrive.

---

### Post by theozzlives on 2009-12-17
Why not try the USB Creator that comes with Ubuntu.

---

### Post by C.S.Cameron on 2009-12-17
Try unetbootin, if that works delete all the files on the stick and re-try usb-creator.
Unetbootin is a bit better at setting up the drive than usb-creator.

---

