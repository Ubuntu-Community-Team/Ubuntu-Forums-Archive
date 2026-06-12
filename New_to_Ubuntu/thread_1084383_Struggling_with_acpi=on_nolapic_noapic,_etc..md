---
title: "Struggling with acpi=on nolapic noapic, etc."
date: 2009-03-02
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2009-03-02
SOLVED
I got frustrated that the booting process hung up and freeze. After many googling and I have tried a lot of combinations of acpi=on acpi=off acpi=force nolapic noapic ,etc and finally find out adding acpi=on and nolapic on grub would let the boot process goes.** [update: I just find out only nolapic is needed to make it boot without freeze]** Here's my /boot/grub/menu.lst 
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on nolapic  quiet  
initrd		/initrd.img-2.6.27-11-generic
```


But now my Celeron Dual-core processor only has one core being activated. 
These few lines in dmesg tell that BIOS may have some problems (ACPI?APIC??I am really frustrated...)
```

[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] found SMP MP-table at [c00f85b0] 000f85b0
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
    0.022266] ACPI: Core revision 20080609
[    0.025121] ACPI: Checking initramfs for custom DSDT
[    0.427585] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428100] BIOS bug, local APIC #0 not detected!...
[    0.428142] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428181] SMP disabled
```

But my BIOS don't have any setting available. It's a very simplified one because it's a cheap notebook. I visited the manufacturer site and cannot find any BIOS to upgrade. It is the crappest BIOS I've ever seen.  Please take a look at the photo of the BIOS. 

[[img]http://www.freeimagehosting.net/uploads/th.c6cdb9be85.jpg[/img]](http://www.freeimagehosting.net/image.php?c6cdb9be85.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.ae131e81c8.jpg[/img]](http://www.freeimagehosting.net/image.php?ae131e81c8.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.8762a54627.jpg[/img]](http://www.freeimagehosting.net/image.php?8762a54627.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.6e9ac46d3f.jpg[/img]](http://www.freeimagehosting.net/image.php?6e9ac46d3f.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.6e9ac46d3f.jpg[/img]](http://www.freeimagehosting.net/image.php?6e9ac46d3f.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.6e9ac46d3f.jpg[/img]](http://www.freeimagehosting.net/image.php?6e9ac46d3f.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.3b56426eb0.jpg[/img]](http://www.freeimagehosting.net/image.php?3b56426eb0.jpg)


Actually I started a thread about my cpu issue
[http://ubuntuforums.org/showthread.php?t=1084326](http://ubuntuforums.org/showthread.php?t=1084326)

And I read this tutorial page but still don't know what to do: 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I wonder if any of you have ever experienced similar issue and the way to fix it. Thanks!

**Update:** I finally get both core working. I added these options to the kernel line in /boot/grub/menu.lst 
**noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard** 
And two cores were brought up. 

Hope it may help anyone who has an SiS 671MX with a dual-core cpu. 

Here's the extract of my /boot/grub/menu.lst
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro quiet noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
initrd		/initrd.img-2.6.27-11-generic

```

---

### Post by monkey4ahead on 2012-03-26
Just to let you know this information did help someone out. Me! I have a different motherboard (Foxconn RC4107MA-RS)but found I could only successfully boot with the "nolapic" option. Even then the PC would randomly reboot. In desperation I tried your boot options and I now have a fully-functioning, hyper-threaded and stable system. Thanks!

---

