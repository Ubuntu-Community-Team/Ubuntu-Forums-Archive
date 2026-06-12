---
title: "APIC error on CPU0: 40(40) on Jaunty"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by dbuehler on 2009-09-12
I just moved from Hardy Heron to Jaunty Jackalope and have been getting many error messages "APIC error on CPU0: 40(40)"  I searched previous posts and have changed the boot for no apic but am still getting the errors.

I have been trying to ignore it but I had a crash today and the only thing in the logs that I could find at that time was this APIC error.  In fact, I have gotten up to 30 of these errors in one second.

Does anyone have a suggestion?

My system is an Asus P4S8X motherboard with a 2.4 Ghz Pentium 4.

Thanks.

Dan

---

### Post by stderr on 2009-09-12
Hmm, I'd be tempted to try disabling ACPI and falling back to APM:

acpi=off pci=noacpi apm=force

---

### Post by dbuehler on 2009-09-13
Thanks for the advice stderr.  I tried it but am still getting quite a few errors.  I modified /boot/grub/menu.lst to add the parameters you suggested on the end of the 'kernel' line.  It now reads 

"kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro  single acpi=off pci=noacpi apm=force"

I am pretty new to linux but think I did that right.

Could my problem be due to some hardware incompatibility with Jaunty?  I searched the archives and found that my video card, Radeon X1300 pro is no longer supported.  However, it seems to be working OK but at a lower resolution.

Dan

---

### Post by stderr on 2009-09-13
I think ATI were ***holes and stopped updating their Linux drivers for x1300s and the like. So I figure you'd do best using the latest (old) version of ATI's drivers that do work with x1300s, or just use the open source drivers (except they will be really slow with 3D acceleration - i.e. games). 

I wouldn't think that would have anything to do with your APIC issue though. 

How about also adding noapic to the list of parameters? We're disabling a lot of stuff now, buy hey, it might work :) 

```
acpi=off pci=noacpi apm=force noapic
```

It's also a good idea to edit the kernel boot line from the boot screen rather than in menu.lst. This way, if it complains and refuses to boot, you can more easily boot your system again (by restarting and _not_ modifying the kernel parameters again). By modifying menu.lst, you're going straight to the permanent solution. It shouldn't be a big problem in this case, especially if you have other kernel versions to fall back to, but it's good practice to test first (pressing 'e' at the boot screen and modifying the line there, before pressing 'b' to boot), rather than implementing the solution (editing menu.lst).

It would also help to ensure you're editing the correct kernel line (the latest kernel in the boot menu is normally the top one).

> **dbuehler said:**
> Could my problem be due to some hardware incompatibility with Jaunty?
In a sense, with a APIC error I would assume motherboard/BIOS, as the APIC is on the motherboard. Not to say at all that this is non-resolvable.

---

### Post by dbuehler on 2009-09-13
Thanks again steder.  

I tried what you said and apparently I wasn't editing the boot parameters correctly.  When I edit grub during boot as you suggest, it seems to work with no APIC errors.  Now i am confused as to how to permanently change it.

In /boot/grub/menu.lst here is a note about AUTOMAGIC that I do not fully understand.  The correct kernel seems to be within the AUTOMAGIC portion. The only kernel statement that is not in that portion is this one:

"# kernel	/vmlinuz root=/dev/hda2 ro"

Can you point me in the right direction?

Dan

---

### Post by stderr on 2009-09-13
Sounds good - we have a fix! That's fine, you want to be editing within the AUTOMAGIC markers. 

In a terminal, run:

```
uname -r
```

What it prints out is your current kernel. Find that entry in menu.lst and make the modifications there. For example, 

```
ace@ace1:~$ uname -r
**2.6.27-14-generic**
ace@ace1:~$ gksudo gedit /boot/grub/menu.lst

```

Scrolling down to "## ## End Default Options ##", the first entry I see is:

```

title		Ubuntu 8.10, kernel **2.6.27-14-generic**
uuid		b1e0ec5b-576d-4097-b559-cdad5455912f
kernel		/boot/vmlinuz-**2.6.27-14-generic** root=UUID=b1e0ec5b-576d-4097-b559-cdad5455912f ro splash quiet 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

```

and I'd append the parameters to that "kernel" line.

---

### Post by dbuehler on 2009-09-13
Wow! many thanks stderr.  That fixes my problem.

Dan

---

