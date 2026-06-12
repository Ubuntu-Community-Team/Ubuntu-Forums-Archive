---
title: "IDE drive not named /dev/hda?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by minsf on 2009-03-06
i'm reading some documentations about partitioning, and they all suggest that IDE drives are named /dev/hdXY by convention, where X=a,b,c,... and Y is the partition number. However, I'm running 8.10 and my hard disk is named /dev/sda (i assume that 5 years old internal laptop hard drive is IDE, unless you tell me that there is another possibility).
Is this normal with ubuntu?

---

### Post by tarps87 on 2009-03-06
All or at least nearly all drives IDE drives appear as sdxy now, It is now using the libata-pata driver so this is normal in Ubuntu

---

### Post by minsf on 2009-03-06
i thought this is the ata_piix driver...
anyways, thanks for the info!

---

