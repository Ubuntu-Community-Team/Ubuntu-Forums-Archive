---
title: "boot problem"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by DrScum on 2010-01-10
I am running Ubuntu 8.04 on a desktop. The system is up to date. Since the second or third to the last update from the update manager I am observing a boot problem: booting hangs with a black screen saying "Starting up...." in the upper left corner. If everything went normal, the next step would be "Loading pleas wait..." also in the upper left hand corner and then the Ubuntu screen would appear with the orange progress indicator moving from left to right.
The only way to overcome this is to cut off power and start over. Sometimes I need one, sometimes two and sometimes as much as three restarts. Very rarely it happens that the system hangs during the orange progress bar moving.

How can I diagnose and preferably fix this problem?

---

### Post by Iowan on 2010-01-10
Not a solution - only a debugging tool... You might change the /boot/grub/menu.lst kernel line from **splash** to **nosplash**. This *might* (if my guess is correct) show a more detailed list of what is going on as Ubuntu starts up.

---

### Post by DrScum on 2010-01-10
THX for pointing out a diagnose tool for me, 

at this point it could be anything, a broken HDD, a faulty motherboard, and, of course, a boot problem.
I'll make the changes and keep you posted about the results.

It'll be tomorrow though since it's getting late in my time zone.

---

