---
title: "System Diagnotics"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by coolbrook on 2009-09-13
I'm using the **System Profiler and Benchmark** app. (**hardinfo** package)

Are there more apps like this that show greater detail?  (For example: the slots occupied by my RAM)

---

### Post by synapsys on 2009-09-13
The slots occupied by your ram can be viewed in the bios.

---

### Post by jmszr on 2009-09-13
coolbrook,

This isn't an app, but it has fairly good detail:```
sudo lshw -html > ~/Desktop/hardware.html
```

It will show up on your Desktop,of course.

---

### Post by louieb on 2009-09-13
hard drive diagnostics and monitoring - [B]smartmontools
[/B]> Description: control and monitor storage systems using S.M.A.R.T.
 The smartmontools package contains two utility programs (smartctl and smartd)
 to control and monitor storage systems using the Self-Monitoring, Analysis and
 Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
 hard disks. It is derived from the smartsuite package, and includes support for
 ATA/ATAPI-5 disks. It should run on any modern Linux system.


---

### Post by coolbrook on 2009-09-13
> **jmszr said:**
> ```
sudo lshw -html > ~/Desktop/hardware.html
```

It will show up on your Desktop,of course.

Awesome!  Thank you.

---

