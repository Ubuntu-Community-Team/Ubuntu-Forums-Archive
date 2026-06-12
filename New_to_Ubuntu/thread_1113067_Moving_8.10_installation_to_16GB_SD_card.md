---
title: "Moving 8.10 installation to 16GB SD card"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by blackstripes on 2009-04-01
I have an HP Mini with a 16GB SSD and a 16GB SDHC card.  8.10 is currently installed to the SSD but I am wanting to move it to the SD card.  Will someone tell me if this will work?

I am booting from a USB drive created using the live CD and I have formatted the SD card to EXT3.  The command I was going to run in the terminal is this:

```
sudo cp -r / /media/disk
```

Will this work?

---

### Post by Nostalos on 2009-04-01
I wouldn't recommend it as I don't beleive that would preserve the permissions. 

Not sure exactly what you are wanting to do here, but i'm assuming making this boot from the SDHC card.   And since they are the same size, dd would be better and make an exact duplicate of the original device.


Assumption.
SSD = /dev/sda
SDHC = /dev/sdb
(again I am assuming.  MAKE SURE AND DOUBLE CHECK

dd if=/dev/sda of=/dev/sdb bs=1M

This will copy everything including the boot block.   However do note that you will not necessarily boot from the SDHC without modifying /etc/fstab to point to the proper new volumes.

---

