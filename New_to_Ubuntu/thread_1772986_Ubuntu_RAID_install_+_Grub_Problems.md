---
title: "Ubuntu RAID install + Grub Problems"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by justin-case on 2011-06-01
Hi Guys

Iam currently setting up Ubuntu on a supermicro supeserver 5014C-T. It has no raid controller so i guess thats a Software RAID??

Any way - i keep getting GRUB install error, i have tried 10.04, 11.00 and finally 9.10
i guessing that this has something to with the RAID.

Please post if i need to run a script for installation log/archive.


Thx

---

### Post by seawolf167 on 2011-06-01
Did you setup and initialize your RAID array correctly? Take a look at [this page ]("https://help.ubuntu.com/community/Installation/SoftwareRAID")and see if you have the software RAID properly configured.

---

### Post by justin-case on 2011-06-01
The MB has RAID configured in the bios  (bios options: ACHI,RAID,SATA)

Is that Fake RAID?

---

