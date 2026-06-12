---
title: "Movign large files"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-10
When movign the entire contents of a hard drive is there a way to set the copy operation to "skip" uncopyable files automatically? It's a bummer to set it to copy, then wait 6 hours and find it stopped 1/2 way through.

I'm only getting a 5mb/sec transfer rate, how do I troubleshoot the slow copy speed? Drives are rated at 3gb/sec. DMA is enabled by checking hdparm.

---

### Post by LewRockwell on 2009-07-10
I haven't had that problem with clonezilla([http://www.clonezilla.org/](http://www.clonezilla.org/))

perhaps a tool like this([http://www.partedmagic.com/](http://www.partedmagic.com/)) might fit in the servicetech's toolbox?

.

---

### Post by Western Digital on 2009-07-10
To clarify something for you, just because your SATA drive can achieve 3GB/s, in no way means that you get anywhere near that. Even 10kRPM drives can't achieve that high of a transfer rate. 

If you were to have many very-fast SSDs in a RAID 5 configuration, and then used SATA, then I bet you would get closer to the theoretical throughput.

---

### Post by servicetech on 2009-07-10
> **Western Digital said:**
> To clarify something for you, just because your SATA drive can achieve 3GB/s, in no way means that you get anywhere near that. Even 10kRPM drives can't achieve that high of a transfer rate. 

If you were to have many very-fast SSDs in a RAID 5 configuration, and then used SATA, then I bet you would get closer to the theoretical throughput.

I'd be excited to get 1/100th of the theoretical output (30mb/s), 5mb/s sec is just ridiculous.

---

