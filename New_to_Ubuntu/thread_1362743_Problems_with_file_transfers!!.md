---
title: "Problems with file transfers!!"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2009-12-23
ive noticed that if i move one file or a few small files into a usb or sd card,then remove the card and put it back in it will not be there anymore. im finding this extremely annoying!!could someone please explain to me why this is happening or even better how could i fix this.

also could someone please tell me a program which is similar to scandisk for ubuntu.

thanks in advanced - Daniel

---

### Post by Geoff918 on 2009-12-23
You might want to start with a command line (apps -> accessories -> terminal)

Do the following with the device attached please:

sudo fdisk -l

This may tell us what format the drive is in (file system), etc.

---

### Post by audiomick on 2009-12-23
Hallo.
Are you ejecting the portable media properly?

For file systems, try fsck.

look at
```
man fsck
```

---

### Post by swoody on 2009-12-23
Are you giving the files time to copy to the USB/SD card, or are you removing it too early? Also, have you just been removing the drive, or unmounting it properly first?

As mentioned, I would double-check what FS the drive uses. Also, have you tried the USB/SD card on another computer? Or other drives on this computer? It may be an issue with the drive itself.

---

