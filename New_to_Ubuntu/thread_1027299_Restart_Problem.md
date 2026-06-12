---
title: "Restart Problem"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by ragegainor on 2009-01-01
I am using a Dell XPS 410 Desktop on which I have just installed Ubuntu 7.10.  Everyhing seems to be just fine except I cannot restart my computer.  When I try to restart my computer just hangs.  Never had this problem with windows.  I also noticed in my logs that ACPI:PCI interrupt for device 0000:00:19.0 is disabled.  I really have no idea what this means but I do know I cannot restart my computer.  I can shutdown the computer but I cannot restart it, the system just shows the ubuntu logo. Any solutions would be greatly appreciated.

---

### Post by mikewhatever on 2009-01-01
Open you menu.lst for editing and remove 'splash' from the boot line for Ubuntu, the word in red in the example below. Then reboot and note where it stops.

> 
title           Ubuntu 8.10, kernel 2.6.27-9-generic
kernel          /boot/vmlinuz-2.6.27-9-generic root=/dev/sdaX ro quiet [COLOR="Red"]splash[/COLOR]
initrd          /boot/initrd.img-2.6.27-9-generic
quiet



---

