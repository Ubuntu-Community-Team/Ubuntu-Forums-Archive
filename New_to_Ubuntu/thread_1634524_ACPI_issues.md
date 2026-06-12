---
title: "ACPI issues"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by Solumin on 2010-11-30
Hello Ubuntu Community!

I recently installed Ubuntu as a dual boot with Windows 7.  I had a few hiccups at first, but these were all ironed out when I booted with the acpi=off option.  However, I don't like having to use this option, since I cannot use any of the advanced power management options or see the charge on my battery.  My only other boot option is i915.modeset=1.

If I do not use the acpi=off option, a flood of "spurious response" messages appears:
```
spurious response 0x0:0x0, last cmd=0x0f0000
```These are usually preceded by a "could not reset ohci card" message from the firewire module.  I am able to log in on the command line, but no graphics are shown.  I tried to launch firefox from the command line, but a "no display set" error appeared.

Is there a way to boot with the ACPI on?  It's not absolutely necessary, but I would like to at least be able to see how much charge is left on my battery...

my computer:
Toshiba Satellite A500
Intel Core i5 CPU M430 @ 2.27 GHz
Memory: 3.7 GB 
Kernel: 2.6.35-23-generic
(What other information is needed?)

---

