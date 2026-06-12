---
title: "dual boot mystery!"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by cranston on 2009-02-14
i have two hard drives one with ubuntu installed and the other with xp installed, i canaballised an old PC.  the ubuntu disk is the primary disk the Xp is the slave.  when i switch on the pc from cold i get the error message "no boot device available. enter a boot disk and press any key to continue" I switch off and on the PC and immediately and low and behold grub loads!! has anybody got an idea of why this strange behaviour is occurring?

---

### Post by indeterminate on 2009-02-15
I've had old machines do that kind of stuff before, where they refuse to start from a cold boot, but a warm reboot will work fine. I have no idea why it happens... it's probably just a symptom of old age in the computer.

---

### Post by Peter09 on 2009-02-15
Two things could be happening,
1. The BIOS is not waiting long enough for the hard disks to spin up, so its failng to read them.
2. On startup the system is not being reset properly.

It might be worth checking that the hard drives are configured properly master/slave etc and the bios is set up for them.

---

### Post by cariboo on 2009-02-15
You may want to replace your CMOS battery,  that should  solve your problem.

Jim

---

