---
title: "External hard drives"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Iknownothing on 2010-05-01
Can anyone suggest a good external hard drive that works with Ubuntu. Do the Freecom tough drives work with Ubuntu?

---

### Post by nhasian on 2010-05-01
dont they all work with ubuntu?  I've always had good luck with western digital drives.

---

### Post by KirbySmith on 2010-05-01
I have two StarTech.com housings populated with WD drives that work with 9.10 via USB.  I did discover that one has to partition and format the drives using PATA or SATA connections in the computer or the drives are invisible to ubuntu (or more likely, invisible to the BIOS).  I haven't experimented with eSATA yet to determine whether blank drives can be partitioned and formatted through that interface.

kirby

---

### Post by Sir Jasper on 2010-05-01
Hi,

Not all external hard drives say that they support Linux.

There may be some attractively priced offers in the UK during this Bank Holiday period and there are plenty of reliable manufacturers so your spec requirements, including ruggedness,  weight, physical size, GB capacity, rpm, running direct from USB slot without extra power supply, wrap-around cable, etc. are probably more important than any particular manufacturer.

My regards

---

### Post by nhasian on 2010-05-01
> **Sir Jasper said:**
> Not all external hard drives say that they support Linux.

Just because the packaging doesn't say Linux or the manufacturer specifically doesn't support Linux does not mean that it will not work.
IDE, SATA, USB, etc are standards that should work on any OS.

---

### Post by KirbySmith on 2010-05-17
To extend my earlier remark, if a drive has any formatting sufficient to be seen by the BIOS, then GParted can see it via USB, and one can then reformat to whatever collection of partitions and formats one wants.  If the disk is defective in some way, such as a bad sector, the formatting process will find it and stop with a complaint.  I've recently reformatted or thrown out about 10 old windows drives this way.

kirby

---

