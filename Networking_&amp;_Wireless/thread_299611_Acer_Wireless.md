---
title: "Acer Wireless"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by rpasell on 2006-11-14
Sorry it's taken me so long to test this. Following the instructions here

[http://ubuntuforums.org/showpost.php...&postcount=357](http://ubuntuforums.org/showpost.php...&postcount=357)

when I issue:

rob@ACERlaptop:~/Desktop/acer_acpi-0.3$ sudo modprobe acer_acpi

I get:

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

I've tried copying the .ko file to that directory manually with no success.

Any ideas?
Edit/Delete Message

---

### Post by FrodoB on 2006-11-14
Just a guess:

$ sudo /sbin/depmod -a

Then try to load it.

---

### Post by rpasell on 2006-11-15
no dice, I get the same message returned.

---

