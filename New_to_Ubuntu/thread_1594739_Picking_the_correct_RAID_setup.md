---
title: "Picking the correct RAID setup"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by noncentz303 on 2010-10-12
Afternoon All,

I am trying to setup a friends RAID but I am having trouble picking the kind of RAID setup I need. I plan on using a hardware RAID controller unless of course this is not the best solution.

I bought 3 hard drives... 2 large 2TB and one fast solid state drive. I figured I would load my OS on the SSD and the other 2 for storage. I would like to have some sort of redundancy so I figured that RAID 1 would be my choice. Thing is doesn't RAID make all of the my disks "transparent" to the Operating system. 

I think the only way I would be able set this up would be to RAID 0 the two 2TB drives and then simply run the OS on the SSD.... without any redundancy.

Any thought or suggestions would be great!

Noncentz303

---

### Post by CharlesA on 2010-10-12
RAID 0 = striping, which has no redundancy. If you lose one drive, you lose all yer data.

If you want redundancy with 2 drives, use RAID 1 or mirroring.

---

### Post by noncentz303 on 2010-10-12
Howdy,

I want redundancy with 3 drives so if I go with RAID 1 how to I specify which physical drive I install the operating system on??

Thx

---

### Post by fatality_uk on 2010-10-12
Remember that 2 x 2TB drives under RAID 1 equals 1 x 1TB array. I woould go with RAID 1 for maximum security.

---

### Post by sandyd on 2010-10-12
> **noncentz303 said:**
> Howdy,

I want redundancy with 3 drives so if I go with RAID 1 how to I specify which physical drive I install the operating system on??

Thx
why not just do RAID 1 with the two 2 TB drives, then leave the SSD seperate?

p.s. SSDs are less crash-damage-prone than hard drives, because when a hard drive crashes, the head drops onto the platter (which is NOT good for the Hard Drive...). Over time, the platter gets damaged, and so does the head.
SSDs don't have moving parts; they use the same memory that resides in your mp3 player. Therefore, they are less damage-due-to-crash prone.

---

### Post by fatality_uk on 2010-10-12
When it comes to installing the OS, you would go into the manual partition tool and specify your SSD. I would install a separate home /home partition and have a daily cron job to back that up to the RAID Array. That way, your are pretty sure that any issues, it can be quickly restored.

---

### Post by CharlesA on 2010-10-12
> **sandyd said:**
> why not just do RAID 1 with the two 2 TB drives, then leave the SSD seperate?

+1.

Could always put /home on the 2TB Array, but you can do that after install as well.

---

### Post by noncentz303 on 2010-10-12
Well thanks kindly everyone!

I decided to go with the raid 1 for the 2x2TB drives and leave the SSD separate. Away I go.

---

