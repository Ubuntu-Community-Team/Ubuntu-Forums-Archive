---
title: "Usb startup Disc Creator question"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by ubfu on 2009-12-28
I wanted to create a USB startup disk into my usb pendrive.
But I have files on my pendrive.Is it possible to create startup disk without formatting my current usb drive ?

Anyhow , I wanted to create a startup disk for ubuntu 9.10 avoiding any format drive.Having 2GB free space on the pendrive.

Thank you :)

---

### Post by HarrisonNapper on 2009-12-29
Theoretically, yes, it is possible. However, flash drives are not hard-drives, so I would suggest doing it the easy way. Move the files from the drive to your comp, create the liveUSB (I use unetbootin because it is awesome), then move the files back.

Cheers.

---

### Post by C.S.Cameron on 2009-12-29
You can create a second FAT32 partition on the drive using gparted/partition editor and install to that using usb-creator or unetbootin. This should leave your current files intact.

---

