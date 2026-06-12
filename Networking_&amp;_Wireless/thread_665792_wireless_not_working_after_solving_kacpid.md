---
title: "wireless not working after solving kacpid"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by blackenedbloodx on 2008-01-12
hey guys i had the problem you have all probably heard about. kacpid and kacpid_notify. i added to /boot/grub/menu.lst acpi=off and apm=off to my kernel line. but now i cant recognize my home wireless network!! i have a signal for the ones around me but not mine. any ideas??

---

### Post by manoj_isi on 2008-05-18
acpi=off is not a good solutions for kacpid, since if we use it on dual cores  only 1 core get active.

Solution to kacpid which works fine for me :
 After booting windows when  boot linux kacpid starts, to stop it just cut the power supply to your PC including UPS if any , without shutting down (obviously after saving data) when linux desktop is active.  yes i am saying that take the power cord out.

 Now switch on the power of ur machine & boot linux, kacpid will not appear.(hopefully)

Happy Linuxing,

---

