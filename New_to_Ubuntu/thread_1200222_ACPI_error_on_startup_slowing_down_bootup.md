---
title: "ACPI error on startup slowing down bootup"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Mriswithe on 2009-06-29
I am running ubuntu 9.04 on a compaq laptop running a sata drive and every time I boot up be it from a suspend, hibernate or a complete shutdown/reset I get the following message, I pulled the message from the kern.log:
```
Jun 29 18:55:03 mriswithe-laptop kernel: [    7.740017] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [    8.224015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224007] ata2.00: qc timeout (cmd 0x0)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224016] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224061] ata2.00: ACPI: failed the second time, disabled
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224063] ata2.00: revalidation failed (errno=-5)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224104] ata2: limiting SATA link speed to 1.5 Gbps
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.708015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
```

Only this part actually shows on startup

```
Jun 29 18:55:03 mriswithe-laptop kernel: [    7.740017] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224016] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224063] ata2.00: revalidation failed (errno=-5)
```

I don't know for sure but I am fairly certain that this is slowing down my startup, now this isn't the most important thing to me but when I was running feisty faun it did the same thing. my computer is a cq60-220us compaq laptop. 

Any info is greatly appreciated.

Mriswithe

---

### Post by adaren on 2009-07-07
ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
ata2.00: revalidation failed (errno=-5)  


I have the same problem and my comuter is hp cq60-130.

What is that? what's wrong?

---

### Post by luckymonkey on 2009-07-23
I have the same issue.
i have a compaq presario cq60-211dx.
if you guys have solved the problem i would apreciate the info.
Thanks.

---

### Post by luckymonkey on 2009-08-04
using the acpi=off option when booting the kernel, somewhat skips those nasty checks, but afterwards everything is very slow...

---

### Post by luckymonkey on 2009-08-15
For the record, Debian Squeeze kernel was upgraded earlier today and this thing is now fixed!!!
linux-image-2.6.30

---

### Post by luckymonkey on 2009-08-15
No, it is not completely fixed, but the boot time is much faster.

---

