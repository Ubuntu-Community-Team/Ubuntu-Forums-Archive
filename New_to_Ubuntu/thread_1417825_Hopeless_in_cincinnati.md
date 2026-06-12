---
title: "Hopeless in cincinnati"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by oxygenfarm on 2010-02-27
I have a 5-year-old HP with an AMD64 processor and 2 gigs RAM...and until yesterday had Win XP Media Center and Ubuntu 9.10 running...at separate times.
Small strange things began happening: email typing slowed; Ubuntu wouldn't load; finally on startup I read that Grub was broken, and Windows wouldn't load. I renewed NTLDR and such, w/o results, then tried to load a live Ubuntu CD to repair Grub, but the 9.10 CD would go into the splash screen, work for a minute, then the machine would die.
I opened the box and tightened all cables and reinserted RAM sticks. Meanwhile, my Windows C: and D: drives seem to have changed names! I also ran the Kaspersky rescue disk, with no problems found.
Help appreciated.

---

### Post by ankscorek on 2010-02-27
u need a firmware upgrade....update ur bios and i think will give u respite to certain extent

---

### Post by MooPi on 2010-02-27
A quick memtest sounds like a good idea.

---

### Post by Mark Phelps on 2010-02-28
This is apparently an OEM machine (HP) and while there MIGHT have been BIOS updates for this in the last five years, it's unlikely that (1) the BIOS is suddenly the problem and (2) a BIOS upgrade is going to fix anything.  BIOS updates should only be done when necessary -- not just when possible.

Is your Ubuntu installed inside Windows? Or is it installed to a separate partition?

Also, were you having these slowdown problems only in Ubuntu? Or were you also having them in Media Center?

You said the machine would "work for a minute". Does that mean you actually got to a working Ubuntu desktop? Or do you mean that it sat on the splash screen for a minute and then died?

---

### Post by oxygenfarm on 2010-02-28
I ran Memtest86 (3 hours) and it found no errors.

The machine is an HP Presario, and Ubuntu 9.10 had been on D:. Minor problems were first evident in Windows, then Ubuntu would not load, then a live CD (I used Ubuntu 7.10) would load, then even that would stop after a few minutes on the splash screen, and on(ab)normal HD boot I would get indications that Grub is broken, (error 22?).
Last time I had the live CD running I could see all my C: files, but the drive names had changed.
Thanks again for good advice.

---

### Post by oldos2er on 2010-02-28
In Ubuntu run **palimpsest** to check your hard disks.

---

### Post by oxygenfarm on 2010-02-28
I ran PowerMax on both HDs (Maxtors) and they passed w/o errors.

---

### Post by lyall on 2010-02-28
it could be your CMOS battery

I have seen the CMOS battery when it is low or about to die do strange things

try replacing the CMOS battery on your motherboard

good luck and have fun learning

---

### Post by oxygenfarm on 2010-03-02
I renewed the CMOS battery and reboot brought me a GRUB(?) list which included Windows_RP, the recovery partition. Biting the bullet I reinstalled WinXP and then was also able to boot into Ubuntu.
The weird change in drive designations should have been the tip!
Again, many thanks.

---

