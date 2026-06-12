---
title: "Network card not detected"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by dmoshal on 2006-08-23
Hi - I just installed Ubuntu 6.06 (Server version) on a new Dell PowerEdge 1950, with 2 NICS.

The installer doesn't detect any network cards - how should i proceed?

Thanks
Dave

---

### Post by gsavix on 2006-08-23
hi!
you could use in command line:
first command:   "sudo dmesg"
second command:  "sudo modprobe"
third command:   "sudo ifconfig" 

this commands will help you know about what your hardware is?

---

