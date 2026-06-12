---
title: "Ubuntu locks up several times a day"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by djackn on 2010-03-24
Installed ubuntu, eclipse, gcc, g++, gdb, cdt, firestarter, etc. PC locks up (hard, need to pull the power) several times a day. Reinstalled ubuntu, etc. Still locks up. Ran memtest overnight with 0 errors. Any ideas before I try another PC?

---

### Post by byStanderone on 2010-03-24
...one question, can you boot from the live cd without any problem?

---

### Post by djackn on 2010-03-24
> **byStanderone said:**
> ...one question, can you boot from the live cd without any problem?
 
Yes, if what you call the live CD is the install CD. 
The PC I have been using has a new HD.

---

### Post by HereInOz on 2010-03-24
Sounds like a hardware issue.  Either incompatible hardware or faulty hardware.  Could still be the RAM, even after a MemTest, or possible overheating or maybe a failing hard disk.

---

### Post by HereInOz on 2010-03-24
Ok, then the HDD is probably OK.  Did you change the HDD cable?

---

### Post by spiderbatdad on 2010-03-24
Likely a power management problem. The dmesg file can tell you.
You can configure your system to boot using the option acpi=off (easiest),
or you can try to disable power management in the bios (might work.)

---

### Post by jnmjr on 2010-03-24
> **djackn said:**
> Installed ubuntu, eclipse, gcc, g++, gdb, cdt, firestarter, etc. PC locks up (hard, need to pull the power) several times a day. Reinstalled ubuntu, etc. Still locks up. Ran memtest overnight with 0 errors. Any ideas before I try another PC?


I had the same exact issue for a long time, it's the video card and/or drivers.... Start there.

---

