---
title: "I'm stuck on an Install Error"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by ntonline on 2010-12-07
I attempted to install Ubuntu 10.10 and encountered an error during install.  The install was about 60% complete when an unknown filesystem error occured.  I restarted my machine and was greeted by the following error message:
 
 ```
error: unknown filesystem.
grub rescue>
```I get the above grub rescue error message whenever I boot from the hard drive, which has both XP and a partial install of Ubuntu on it.  When I attempt to run Ubuntu 10.10 or 10.04 from the CD, I encounter the following message:

```
strike F1 to retry boot, F2 for setup utility

```Unfortunately, when I strike F1 the machine does not reboot, rather the same line appears again:

```
strike F1 to retry boot, F2 for setup utility
strike F1 to retry boot, F2 for setup utility

```When I strike F2 I'm directed to the BIOS.

I can't get passed this cycle. Anyone have any suggestions?

---

### Post by kyle6513 on 2010-12-07
Re-try the install using your live CD

---

### Post by ntonline on 2010-12-07
> **kyle6513 said:**
> Re-try the install using your live CD
When I attempt to run Ubuntu 10.10 or 10.04 from the CD, I encounter the following message:

strike F1 to retry boot, F2 for setup utility

---

### Post by sydbat on 2010-12-07
How old is the computer you are trying to install Ubuntu on? Any other specs you can share will help us too.

If it is an old hard drive, it could have failed. This might explain the errors.

---

### Post by ntonline on 2010-12-07
> **sydbat said:**
> How old is the computer you are trying to install Ubuntu on? Any other specs you can share will help us too.

If it is an old hard drive, it could have failed. This might explain the errors.

I never considered hard drive failure.  I own an old Dell Dimension 3000 with Windows XP OS installed on it.  I partitioned the 80GB ([SamsungSpinPoint P80]("http://www.samsung.com/ph/consumer/monitor-peripherals-printer/hard-disk-drive/35-pata-hdd/SP0802N/index.idx?pagetype=prd_detail"))                          hard drive using [EaseUS]("http://www.partition-tool.com/personal.htm")  home edition with the intention of installing Ubuntu 10.10 with a dual  boot option.  I did not attempt to install Ubuntu using WUBI.  I  attempted to install the Ubuntu v10.10 32-bit Desktop Edition and  screwed up somewhere along the line.  Now my computer will only display the aforementioned errors whether attempting to boot from the live CD or the hard drive.

---

### Post by owiknowi on 2010-12-07
You could first try to run a check disk program, either from samsung, from within xp or from the rescuecd ([http://www.sysresccd.org/](http://www.sysresccd.org/)).
BTW: xp does not recognize partitions other than fat(32) and ntfs.

If that doesn't work: power off completely, wait a while, connect the computer to the power source and try to boot a killdisk CD and wipe the whole disk.
Errors - bad sectors and such - will appear.

If not to bad use gparted or pmagic in order to:
1. give the hard disk a new disk label from the menu
2. partition the disk

If nothing helps try an other hard disk.

Hope this helps to solve your problem.

---

### Post by matt_symes on 2010-12-07
Hi

Try removing the boot  to hard drive option in the BIOS and just have the boot to CDRom option, so there is  only  one boot option.

Does that boot into the LiveCD?

Kind regards

---

### Post by owiknowi on 2010-12-07
> **matt_symes said:**
> Hi

Try removing the boot  to hard drive option in the BIOS and just have the boot to CDRom option, so there is  only  one boot option.

Does that boot into the LiveCD?

Kind regards

Just put the option boot from CDRom at the top and the boot from Hard disk as second.
Better not remove - if possible - any entries from your BIOS

---

### Post by matt_symes on 2010-12-07
Hi

> Better not remove - if possible - any entries from your BIOS

Eh? As long as you can get into the BIOS you can always put them back. ;) My assumption was that the CDRom was the first boot device. This would have been needed to install Ubuntu in the first place.

Kind regards

---

### Post by owiknowi on 2010-12-07
> **matt_symes said:**
> Hi



Eh? As long as you can get into the BIOS you can always put them back. ;) My assumption was that the CDRom was the first boot device. This would have been needed to install Ubuntu in the first place.

Kind regards

That's correct: first boot device is always on top as you already assumed.

---

