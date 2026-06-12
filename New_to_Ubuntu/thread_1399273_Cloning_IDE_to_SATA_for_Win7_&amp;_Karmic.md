---
title: "Cloning IDE to SATA for Win7 &amp; Karmic"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-05
I have a new motherboard and 400gig SATA drive. I have Win7. I have Karmic on an IDE drive. 

After I install Win7 and shrink the partition(s) of Win7 is it possible to clone my IDE partitions, GRUB2 and /home and all other /xxx directories to the SATA?

What's a good way to bring all of Karmic over to the new hard drive without having to re-install dozens of application packages?

thnx.

---

### Post by CharlesA on 2010-02-05
So you want to just clone 1 partition and move it over, not the entire drive, right?

I think you can do that but I am not 100% sure.

---

### Post by Mark_in_Hollywood on 2010-02-05
I cannot understand your response.

I have an IDE drive. It has Karmic (as on OS) on it's OWN partition. It has /home and /swap on their own partitions. I want to preserve as much of the bits and bytes on the IDE drive as possible. 

I won't be using Win7. It there for the very occasional problem unresolved by Linux.

I have a 400 gig SATA drive. I want to make Win7 about 35 gig. The rest for Karmic. I want GRUB2 to enable dual-booting.

Is this any clearer?

---

### Post by nhasian on 2010-02-05
I dont know about Win7, but in previous versions of windows if you moved the hard disk or OS to a different hard disk controller it will blue screen on startup. probably tinkering with the registry would fix it but it would probably just be easier to do a fresh install of windows on the new sata drive.

> **Mark_in_Hollywood said:**
> After I install Win7 and shrink the partition(s) of Win7 is it possible to clone my IDE partitions, GRUB2 and /home and all other /xxx directories to the SATA?


---

### Post by CharlesA on 2010-02-05
If Windows is already installed on the 400GB drive and you shrink that partition, you could probably try to clone the partition using Clonezilla, but I would recommend first backing everything up on both drives, then Trying to restore that partition to the new drive.

If you want an easier way, just resize the windows partition, install 9.10 and then copy over yer home directory.

---

