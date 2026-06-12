---
title: "ubuntu wont boot after install (had to use acpi=off)"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by bronevaya on 2010-01-26
Hi, I have a motion computing m1300 tablet and when I boot from the cd nothing happens. Now if I use the ACPI=OFF option then it will boot from the cd and install. But when I reboot the machine and take the cd out it will not boot again. It just gives me a blinking cursor. It does give me GRUB but past that nothing works. help!

---

### Post by Hendronicus on 2010-02-05
Boot up with the live cd, mount the drive and then edit the kernel lines in /boot/grub/menu.lst to include the ACPI=OFF switch. If the live cd boots this way then the the installed OS should too. You could also try editing the kernel line when you see the GRUB prompt as well, just to see.

---

