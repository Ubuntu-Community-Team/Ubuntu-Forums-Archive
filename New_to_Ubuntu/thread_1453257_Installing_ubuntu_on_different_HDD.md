---
title: "Installing ubuntu on different HDD?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by kwerty on 2010-04-13
Hi all,

Brand new to the forum and I would like to ask a basic question re: installing  Ubuntu Desktop Edition.

My PC has three HDD's - C: (for backup), D: (empty) and E: (Windows XP).  I want to install Ubuntu on D: and choose which O/S to load on startup.  However, it appears as though Ubuntu will only install on E: alongside Windows.

I've only ever installed Windows before and it will detect multiple HDD's and  ask which one I wish to install to. So, how can I specify which HDD I want Ubuntu to install to?

Many Thanks for any help.

---

### Post by Sin@Sin-Sacrifice on 2010-04-13
When you get to the partitioning part of the installation select "manually partition". Right click the correct drive (probably /dev/sdb) and select "Format to" and then ext4 but make sure you make the size of the partition minus the size of your swap partition. Right click the leftover space and format it to linux-swap. Click proceed...

---

### Post by 4Orbs on 2010-04-13
Something you should be aware of: Those drives that Windows shows might actually be only different partitions on one hard drive.

---

### Post by kwerty on 2010-04-13
Okay, thanks - everything's backed up so I'll try the 'manual partition' selection and follow those pointers.
Cheers.

---

