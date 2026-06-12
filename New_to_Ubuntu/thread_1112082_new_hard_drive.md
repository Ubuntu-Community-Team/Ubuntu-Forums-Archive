---
title: "new hard drive"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by squrl on 2009-03-31
How long should it take to format a 500 gig ata drive to ext3 with gparted??

This has been running for a couple hours and stll going.

Thanks

---

### Post by jchiar on 2009-03-31
That really depends on the hardware. Some settings are also involved, Serial-vs-Parallel.
This page explains it well.
[http://compreviews.about.com/od/storage/l/aaSerialATA.htm](http://compreviews.about.com/od/storage/l/aaSerialATA.htm)
There are many factors here, spin rate, data flow rate, CPU speed, Ribbons and a few other things.
That is also a very large ATA, a few platters in that one, so spin rate and reader arms also come into play.
I would first check the disk integrity before doing a format of any kind. This is called a benchmark.
Personally I would do it 1/3rd ext3, the rest NTFS. This would give it more flexibility and be easier on cross platform /moves or transfers.

---

### Post by halitech on 2009-03-31
I recently did a 160 gig sata drive (connected with USB1.1 external case) and it took the better part of an hour. I don't remember the last time I did my ata internal drive (160gig) but I'm pretty sure it was awhile.

---

### Post by khelben1979 on 2009-03-31
> **squrl said:**
> How long should it take to format a 500 gig ata drive to ext3 with gparted??

This has been running for a couple hours and stll going.

Thanks

What harddrive model is it? (My guess: [Western Digital]("http://en.wikipedia.org/wiki/Western_Digital"))

---

### Post by Ravernomina on 2009-03-31
it all depends on the speed of you hard drive. This includes spin rate/format/Buss sped (ata,sata 1.5,sata 3.0) and also how cool the harddrive is itself.


ATA buss speed: 500 MBPS

Sata buss speed: 1.5 GBPS

Sata 2 buss speed: 3.0 GBPS

Good luck to you:popcorn:

---

