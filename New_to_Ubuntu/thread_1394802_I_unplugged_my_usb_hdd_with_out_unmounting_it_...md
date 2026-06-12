---
title: "I unplugged my usb hdd with out unmounting it .."
date: 2010-01-31
forum: New to Ubuntu
---

### Post by stuntman6 on 2010-01-31
I am running ubuntu 8.04 ... i unplugged my usb hdd with out unmounting it and noow it wont load back up what do i do ?? please if anyone has any sugjestions it would be very aprecheated ..

---

### Post by Silent Warrior on 2010-01-31
Have you rebooted between attempts? I don't see how it should matter, but it's something to try. I've removed USB-sticks without unmounting first - not the same as a USB HDD, but they still work just fine.
I don't know what the /dev-enumeration for those things generally look like, otherwise I'd suggest some manual mounting/unmounting juju through the commandline ("jiggle the handle", like). Just... wait around for someone more knowledgable, I guess.

---

### Post by mikewhatever on 2010-01-31
Can you post the output of <sudo fdisk -l> with the external hdd plugged in.

---

### Post by stuntman6 on 2010-01-31
> **mikewhatever said:**
> Can you post the output of <sudo fdisk -l> with the external hdd plugged in.
Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bc50c9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS

 this is what it shows for that hdd can you help ????

---

### Post by blazemore on 2010-01-31
```
sudo umount /dev/sdd1; sudo fsck /dev/sdd1
```

---

### Post by stuntman6 on 2010-01-31
> **blazemore said:**
> ```
sudo umount /dev/sdd1; sudo fsck /dev/sdd1
```
it kicked this out im not sure whats going on ...

 sudo umount /dev/sdd1; sudo fsck /dev/sdd1
umount: /dev/sdd1: not mounted
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdd1

 what is this

---

### Post by stuntman6 on 2010-02-01
i got it to boot back up i plugged it into a windows box and changed the name of the hard drive and when i booted linux it was like butter on the screen thanx for all the attempts to fix my mess up ...

---

