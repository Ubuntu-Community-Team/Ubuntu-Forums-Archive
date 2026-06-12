---
title: "file corrupt when copy to USB"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by blizta on 2010-07-20
hi there.....

when i copy some mp3s to USB drive and suddenly remove it (i'm in haste :D), why the mp3s that have been copyed to my usb corrupted.

but, it doesn't happen in windows. 

thanks....

---

### Post by bodhi.zazen on 2010-07-20
It will happen on any OS. You should eject before you remove the device, the eject or umount command servers to write all the data and close the file system.

---

### Post by blizta on 2010-07-20
> **bodhi.zazen said:**
> It will happen on any OS. You should eject before you remove the device, the eject or umount command servers to write all the data and close the file system.
but, i heard it'll be ok if it FAT.

---

### Post by JustinR on 2010-07-20
I'm pretty sure in Windows there's a feature that allows you to pull out the drive without data corruption - with a performance loss on the drive but in Linux it works differently, as far as I know a feature like this doesn't exist.

---

### Post by mcduck on 2010-07-20
> **blizta said:**
> but, i heard it'll be ok if it FAT.

nope, the file system used won't help you there. If some of the data isn't yet written to the drive when you unplug it, there's no way how the filesystem (or anything, really) could fix the file for you.

You aren't supposed to unplug devices without safely removing them first in Windows, and same applies to both Linux and OSX. As well as any other modern operating system.

(If you really, really want to do that kind of thing it's possible to enable the "sync" option for a drive in fstab. That will make Linux to write everything to that drive immediately, without buffering the writes. As a result it becomes much less likely that you end with corrupted data if you unplug the drive unsafely, but on the other hand the lifetime of any flash device can suffer pretty badly. Not to mention that buffering really improves your systems overall performance, which is why it's used in all modern operating systems in the first place...)

---

### Post by blizta on 2010-07-20
well, thanks everybody........
safely remove is the best way. but, sometimes it take a minute to succesfully ejected......

---

