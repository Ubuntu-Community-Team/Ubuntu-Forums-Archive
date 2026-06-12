---
title: "kapcid using 50% cpu"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by egalvan on 2009-03-15
HP Pavillion a810n
AMD 64 3200
4gig RAM


Running either of these...

Ubuntu liveCD
PartedMagic LiveCD

Machine slows down to a crawl,
any video stutters (stops/starts) at about 2 times a second,
mouse stutters (stops/starts) at about 2 times a second,
fan revs up and down at about the same speed...

'top' shows kapcid using approx 50% CPU, with zero RAM,
several other processes show less than 1%.


Any ideas?

No, I have not installed anything on this machine.

---

### Post by martrn on 2009-03-15
Looks like kernel bug [http://bugzilla.kernel.org/show_bug.cgi?id=12170]("http://bugzilla.kernel.org/show_bug.cgi?id=12170")

It doesn't or shouldn't occur on on recent upgrade of the kernel.
I could be certain, ensure you turn power-save / features off in BIOS.

---

### Post by egalvan on 2009-03-15
This is not a recent kernel...

Ubuntu is an original Hardy 8.04 ISO from April 2008

PartedMagic a little newer, ISO from Aug 2008

NO LOAD is put on machine, problem starts as soon as CD starts to load system.

As for BIOS options, this is an HP machine, the BIOS options are very limited...
 no "power-saving" or "acpi" type options.

And lastly, is this an AMD-related bug?
I didn't see that info in that link you gave.

Thanks

---

### Post by martrn on 2009-03-15
> **egalvan said:**
> ..NO LOAD is put on machine, problem starts as soon as CD starts to load system..As for BIOS options, this is an HP machine, the BIOS options are very limited...no "power-saving" or "acpi" type options...And lastly, is this an AMD-related bug?...I didn't see that info in that link you gave.

I have seen what you describe before, Sometimes you can install/boot Ubuntu with no ACPI?  In Linux, Ubuntu does not require ACPI to be present in order to work. If the kernel attempts to load an ACPI module, it will pause for a second and then the module

To turn off the attempt to load ACPI, press <F6> on the boot menu for the CD, and add

acpi=off

You may have to modify the GRUB menu after installation to make the change permanent. To modify the GRUB menu, open a terminal, and enter

sudo gedit /boot/grub/menu.lst

The add the "acpi=off" to the kernel line of each entry.

With 64bit processors, there is a 'feature' Linux has support integrated into the kernel version 2.6.x ??   This 'feature' is called "SpeedStep" or "PowerNow".   No it is not an AMD or Intel related bug it a power management 'bug' (eg is this).

It might be a bug in the kernel or your BIOS or something thats in both of the CD's when they start eg. X.org.  (or even a problem with a piece of your hardware?)

I do not know. I am not sat in front of it.

---

