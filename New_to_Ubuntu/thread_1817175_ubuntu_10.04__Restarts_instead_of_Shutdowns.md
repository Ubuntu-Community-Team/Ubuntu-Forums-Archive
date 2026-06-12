---
title: "ubuntu 10.04 : Restarts instead of Shutdowns"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by aas452 on 2011-08-03
I tried everything from shutdown commands, changing Grub to GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force", reloading my graphic card drivers, but still restarts when I select shutdown... 

ubuntu 10.04 LTS
Nvidia GTX 570,
GIGABYTE|GA-Z68XP-UD3P - MotherBoard

Driving me nuts, any help would be much appreciated ](*,)

---

### Post by sadaruwan12 on 2011-08-03
Well this is very strange ok did you tried this command from the terminal.

```
$ sudo init 0
```

try this and let us know what happen.

---

### Post by aas452 on 2011-08-03
No luck restarts again

:(

---

### Post by sadaruwan12 on 2011-08-03
Well it seems to be your inittab scripts have messed up best thing for you is to reinstall your system backup you home folder and do a repair on your system.

---

### Post by aas452 on 2011-08-04
I just completed a full system restore, Ubuntu is fresh out of the box. I try to shutdown, and it still restarts...

Also init 0 also restarts...

any other ideas???

---

### Post by aas452 on 2011-08-04
Looks like it was a BIOS setting after all, if anyone else has this problem, my motherboard has a "power managment setting" which enables phone calls to turn on the computer, for some reason I disabled this option and it the computer =D> SHUTDOWN =D>

\\:D/

---

