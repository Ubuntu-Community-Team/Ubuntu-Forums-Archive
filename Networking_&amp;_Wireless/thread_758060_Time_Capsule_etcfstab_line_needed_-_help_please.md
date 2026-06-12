---
title: "Time Capsule /etc/fstab line needed - help please"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by yeahdef on 2008-04-17
Hi relatively new to Ubuntu and i really dig it.
Im running 8.04 on a blackbook core duo.

trying to edit /etc/fstab to automatically mount both my time capsule and the attached terabyte has been frustrating.

my line is:
//<ip_to_capsule_here>/<time_machine_disk_name>/ /media/time_capsule smbfs uid=joey,gid=user 0 0

i get nothing when i evoke a remount with
sudo mount -a

anyone solved this?
i think it has something to do with the password on the time capsule

---

