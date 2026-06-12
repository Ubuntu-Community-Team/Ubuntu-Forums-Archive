---
title: "LGDT3305 and SAA7160"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-10-26
Is there a terminal command that would show if drivers for the

LGDT3304 or LGDT3305 TV tuners

and

SAA7160 (Phillips Semiconductor or NXP or TridentMicro) are

in-built into this kernel:


2.6.35-22-generic

---

### Post by bioterror on 2010-10-26
> **Mark_in_Hollywood said:**
> Is there a terminal command that would show if drivers for the

LGDT3304 or LGDT3305 TV tuners

and

SAA7160 (Phillips Semiconductor or NXP or TridentMicro) are

in-built into this kernel:


2.6.35-22-generic

[http://packages.ubuntu.com/en/maverick/i386/linux-image-2.6.35-22-generic-pae/filelist]("http://packages.ubuntu.com/en/maverick/i386/linux-image-2.6.35-22-generic-pae/filelist")

and with search I got:
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/frontends/lgdt3305.ko
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/frontends/lgdt330x.ko

With the Philips this was closest:
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/video/saa7164/saa7164.ko

---

