---
title: "PC won't shut down?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by iggy pop on 2010-03-09
At the end of a busy day of surfing the Super Highhway i click on "Shut Down" and although the screen goes blank the computer is still running and the only option is to press the start button on the computer until the computer does stop running.

---

### Post by spiderbatdad on 2010-03-09
maybe a problem between the kernel acpi and firmware. Either try disabling power management through the bios or try disabling acpi in the kernel with acpi=off. This can be done in /etc/default/grub :
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**acpi=off**"
GRUB_CMDLINE_LINUX=""

```
Then run the command:
```
sudo update-grub
```

---

