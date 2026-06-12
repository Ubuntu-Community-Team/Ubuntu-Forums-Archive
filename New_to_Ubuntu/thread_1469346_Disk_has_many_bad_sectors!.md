---
title: "Disk has many bad sectors!"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by alien92 on 2010-05-02
im pretty new to ubuntu.i installed ubuntu 10.04 but was having many problems,
so i tried installing ubuntu 9.10 and upgrading but while partitioning i got an error.
finally i managed to install it but im getting a warning about my disk having 178 bad sectors.
i tried googling how to fix it but did not get any precise solution
the number of bad sectors are not increasing.
i have backed up my data and would like to know if there is any way i could fix it
i.e. without buying a new hard drive??
also will it create any problems?
thanks a lot in advance

---

### Post by zakoo2 on 2010-05-02
download hiren's boot cd, burn to cd, boot from cd, select hddregenerator, run scan and repair, and there you go... if this doesn't help, you should buy a new hdd!

---

### Post by prshah on 2010-05-02
> **alien92 said:**
> warning about my disk having 178 bad sectors.
the number of bad sectors are not increasing

Usually, a disk having bad sectors mean that it has undergone physical damage to the internal structure.

It cannot be corrected; the bad sectors are marked thus and not accessed during future read/write operations.

As long as it is not increasing, it may be only a onetime issue, and you could probably continue using your HDD.

If it starts increasing, your only option is to replace the disk. Unfortunately, the "increase" can only be detected with a thorough disk check, so it may be too late by the time you find out. 

Here's some common symptoms that indicate bad sectors are interfering with your work; Files get mysteriously corrupted; System get very slow when accessing disk ; HDD activity LED stays solidly lit from time to time, even though only light HDD activity is supposed to take place; errors about "Emask exception" occur with high frequency, even after a standard disk check.

If you find any or most of these symptoms, you most likely have a disk going bad. The only option is to replace it, sorry.

If you still plan to use the HDD, please maintain regular backups of your work in other media.

---

### Post by Elfy on 2010-05-02
moved to ABT

---

### Post by alien92 on 2010-05-02
Thanks a lot,but it turned out it was the Palimpsest bug.The message is not comming in 10.04.
:)

---

### Post by oldos2er on 2011-10-07
Closed, necromancy.

---

