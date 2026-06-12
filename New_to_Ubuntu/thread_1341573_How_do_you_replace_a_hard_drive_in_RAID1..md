---
title: "How do you replace a hard drive in RAID1?."
date: 2009-11-29
forum: New to Ubuntu
---

### Post by sunrex on 2009-11-29
I just wanted to know how you would go about replacing a failed hard drive in RAID1. This would include what sort of partition you would need, etc.

---

### Post by markjensen on 2009-11-29
You yank it out and put a new one in.  :P

Since there is redundancy, it can be rebuilt (the data put back in).  Do you have a hardware RAID controller (not likely), or a software one (and yes, hardware-assisted ones are really software driven)?

I think the dmraid tools in Linux will allow you to rebuild your array.

---

### Post by sunrex on 2009-11-29
> **markjensen said:**
> You yank it out and put a new one in.  :P

Since there is redundancy, it can be rebuilt (the data put back in).  Do you have a hardware RAID controller (not likely), or a software one (and yes, hardware-assisted ones are really software driven)?

I think the dmraid tools in Linux will allow you to rebuild your array.

It's software, not BIOS either :).

The problem is I re-synced the array with mdadm, but on a reboot the array wont stick around (well, the mirror. It's degraded every time) and apparently the second drive isn't even partitioned... its weird.

---

### Post by falconindy on 2009-11-30
Uh, you need to fail the old drive and remove it from the array before you can add a new one. Might wanna check out the man page on mdadm.

---

### Post by sunrex on 2009-11-30
> **falconindy said:**
> Uh, you need to fail the old drive and remove it from the array before you can add a new one. Might wanna check out the man page on mdadm.

I did. Then I re-synced it. And it degrades each time on reboot. It's not a hard drive failing because I manually removed it from the array to test redundancy and then re-added it (SATA cable).

---

### Post by sunrex on 2009-11-30
bump

---

### Post by falconindy on 2009-12-02
> **sunrex said:**
> I did. Then I re-synced it. And it degrades each time on reboot. It's not a hard drive failing because I manually removed it from the array to test redundancy and then re-added it (SATA cable).
How are you "manually removing" it? Unless you're doing some sort of bizzare testing, there shouldn't be a need to ever touch the physical connection on the drive.

---

